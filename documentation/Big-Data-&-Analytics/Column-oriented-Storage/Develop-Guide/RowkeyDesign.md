# Rowkey设计指导

## 引言 

HBase Rowkey是唯一索引(Rowkey用来表示唯一一行记录)，Rowkey设计的优劣直接影响读写性能。

HBase中的行是按照Rowkey的ASCII字典顺序进行全局排序的。

举例说明：假如有5个Rowkey：“012”, “0”, “123”, “234”, “3”，按ASCII字典排序后的结果为：“0”, “012”, “123”, “234”, “3”。（注：文末附常用ASCII码表）

Rowkey排序时会先比对两个Rowkey的第一个字节，如果相同，然后会比对第二个字节，依次类推… 对比到第X个字节时，已经超出了其中一个Rowkey的长度，短的Rowkey排在前面。

由于HBase是通过Rowkey查询的，一般Rowkey上都会存一些比较关键的检索信息，建议提前考虑数据具体需要如何查询，根据查询方式进行数据存储格式的设计，要避免做全表扫描，因为效率特别低，且会损耗集群性能。

## Rowkey设计原则

Rowkey设计应遵循以下原则：

## Rowkey唯一原则

Rowkey在设计上必须保证唯一性

Rowkey在HBase中只插入不更新(不做update操作)。HBase中所有操作都是“流式“操作,不会更改原来存储过的数据,只会进行append,并通过加上新的版本标识表示是最新数据（VERSION为1会覆盖，默认是1）。

## Rowkey的散列原则

Rowkey设计应散列，均匀的分布在各个HBase节点上

如果Rowkey按照时间戳的方式递增，不要将时间放在二进制码的前面，建议将rowkey的高位作为散列字段，由程序随机生成，低位放时间字段，这样将提高数据均衡分布在每个RegionServer，以实现负载均衡的几率。

Rowkey的第一部分如果是时间戳，会将造成所有新数据都在最后一个Region，造成访问热点。

热点：大量的client直接访问集群的一个或极少数个节点（访问可能是读、写或者其他操作）。大量访问会使热点Region所在的单个机器超出自身承受能力，引起性能下降（Full GC）甚至Region不可用，这也会影响同一个RegionServer上的其他Region，由于主机无法服务其他Region的请求。

通常有3种方式来解决热点问题：

#### Reverse反转

针对固定长度的Rowkey反转后存储，这样可以使Rowkey中经常改变的部分放在最前面，可以有效的随机Rowkey。 反转Rowkey的例子通常以手机举例，可以将手机号反转后的字符串作为Rowkey，这样的就避免了以手机号那样比较固定开头(137x、15x等)导致热点问题。缺点是牺牲了Rowkey的有序性。
                                                            
#### Salt加盐

Salting是将每一个Rowkey加一个前缀，前缀使用一些随机字符，使得数据分散在多个不同的Region，达到Region负载均衡的目标。

比如在一个有4个Region(注：以 [ ,a)、[a,b)、[b,c)、[c, )为Region起至)的HBase表中， 加Salt前的Rowkey：abc001、abc002、abc003

我们分别加上a、b、c前缀，加Salt后Rowkey为：a-abc001、b-abc002、c-abc003

可以看到，加盐前的Rowkey默认会在第2个region中，加盐后的Rowkey数据会分布在3个region中，理论上处理后的吞吐量应是之前的3倍。由于前缀是随机的，读这些数据时需要耗费更多的时间，所以Salt增加了写操作的吞吐量，不过缺点是同时增加了读操作的开销。

#### Hash散列或者MOD

用Hash散列来替代随机Salt前缀的好处是能让一个给定的行有相同的前缀，这在分散了Region负载的同时，使读操作也能够推断。

确定性Hash(比如md5后取前4位做前缀)能让客户端重建完整的RowKey，可以使用Get操作直接Get想要的行。

例如将上述的原始Rowkey经过hash处理，此处我们采用md5散列算法取前4位做前缀，结果如下

9bf0-abc001 （abc001在md5后是9bf049097142c168c38a94c626eddf3d，取前4位是9bf0）

7006-abc002

95e6-abc003

若以前4个字符作为不同分区的起止，上面几个Rowkey数据会分布在3个region中。实际应用场景是当数据量越来越大的时候，这种设计会使得分区之间更加均衡。

如果Rowkey是数字类型的，也可以考虑MOD方法（其他类型可以使用hashcode MOD），示意图：

## Rowkey长度原则

Rowkey设计建议定长，长度在10~100个字节，越短越好。    RowKey是一个二进制码流，可以是任意字符串，最大长度 64kb，实际应用中一般为10-100bytes，以 byte[] 形式保存，一般设计成定长。建议越短越好，不要超过16个字节，原因如下：

   （1）数据的持久化文件HFile中是按照KeyValue存储的，如果rowkey过长，比如超过100字节，1000w行数据，光RowKey就要占用100*1000w=10亿个字节，将近1G数据，这样会极大影响HFile的存储效率；

   （2）MemStore将缓存部分数据到内存，如果rowkey字段过长，内存的有效利用率就会降低，系统不能缓存更多的数据，这样会降低检索效率。

   （3）目前操作系统都是64位系统，内存8字节对齐，控制在16个字节，8字节的整数倍利用了操作系统的最佳特性。

   其他的如列族名、列名等属性名也是越短越好。value永远和它的key一起传输的。当具体的值在系统间传输时，它的RowKey、列名、时间戳也会一起传输。如果你的RowKey和列名和值相比较很大，那么你将会遇到一些有趣的问题。HFile中的索引最终占据了HBase分配的大量内存。

## Rowkey有序原则

充分利用Rowkey字典顺序排序特点，将经常读取的数据存储到一块，将最近可能会被访问的数据放到一块。
     
时间戳反转设计：一个常见的数据库处理问题是快递获取数据的最近版本，使用反转的时间戳作为Rowkey的一部分对这个问题十分有用，可以将Long.MAX_VALUE - timestamp追加到key的末尾，例如：[key][reverse_timestamp]
  
表中[key]的最新值可以通过scan [key]获得 [key]的第一条记录，因为HBase中rowkey是有序的，最新的[key]在任何更旧的[key]之前，所以第一条记录就是最新的。

这个技巧可以替代使用多版本数据，多版本数据会永久（很长时间)保存数据的所有版本。同时，这个技巧用一个scan操作就可以获得数据的所有版本。

## HBase Rowkey设计实战

在实际的设计中我们可能更多的是结合多种设计方法来实现Rowkey的最优化设计。

列1：设计订单状态表

使用Rowkey: reverse(order_id) + (Long.MAX_VALUE – timestamp)

设计优点：一、通过reverse订单号避免Region热点，二、可以按时间倒排显示。

列2：使用HBase作为事件(事件指的的终端在APP中发生的行为，比如登录、下单等等统称事件(event))的临时存储(HBase存储最近10分钟的热数据)

设计event事件的Rowkey为：两位随机数Salt + EventId + Date + Kafka的Offset

设计优点： 加盐的目的是为了增加查询的并发性，假如Salt的范围是0~n，那我们在查询的时候，可以将数据分为n个split同时做Scan操作。经过测试验证，增加并发度能够将整体的查询速度提升5～20倍以上。

随后的EventId和Date是用来做范围Scan使用的。在大部分的查询场景中，都指定了EventId，因此把EventId放在了第二个位置上，同时EventId的取值有几十个，通过Salt + EventId的方式可以保证不会形成热点。

把Date放在Rowkey的第三个位置上以实现按Date做Scan。这里可以考虑对Data进行反转（参考时间戳反转设计）

这样的Rowkey设计能够很好的支持如下查询场景：

1、只按照EventId查询

2、按照EventId和Date查询

非必要情况，一般不建议进行全表的Scan查询，全表Scan对性能的消耗很大。

HBase的表设计

HBase表设计通常可以是宽表（Wide Table）模式，即一行包括很多列。同样的信息也可以用高表（Tall Table）形式存储，通常高表的性能比宽表要高出50%以上。所以推荐使用高表来完成表设计。

表设计时考虑HBase数据库的一些特性：

1、在HBase表中是通过Rowkey的字典序来进行数据排序的

2、所有存储在HBase表中的数据都是二进制的字节
 
3、原子性只在行内保证，HBase不支持跨行事务

4、列族(Column Family)在表创建之前就要定义好

5、列族中的列标识(Column Qualifier)可以在表创建完以后动态插入数据时添加

## 总结

在Rowkey设计时，请先考虑业务场景，比如是读比写多、还是读比写少。HBase本身是为写优化的，即便是这样，也可能会出现热点问题，设计时尽量避免热点。如果读场景比较多，除了考虑以上Rowkey设计原则外，还可以考虑和其他缓存数据库如Redis等结合。