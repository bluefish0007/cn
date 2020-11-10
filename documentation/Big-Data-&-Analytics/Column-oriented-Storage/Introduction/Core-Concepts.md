# 核心概念
以下是列式存储帮助文档中使用到的概念及其解释，请参考。

- **Row Key**：行键与nosql数据库一样，row key是用来表示唯一一行记录的主键，HBase的数据时按照RowKey的字典顺序进行全局排序的，所有的查询都只能依赖于这一个排序维度。
- **Columns**：  Family 列族列簇：HBASE表中的每个列，都归属于某个列族。列族是表的schema的一部分(而列不是)，必须在使用表之前定义。列名都以列族作为前缀。例如courses：history，courses：math 都属于courses这个列族。
- **Cell**：由{row key，columnFamily，version} 唯一确定的单元。cell中的数据是没有类型的，全部是字节码形式存储。
关键字：无类型、字节码
- **TimeStamp**： 时间戳HBASE中通过rowkey和columns确定的为一个存储单元称为cell。每个cell都保存着同一份数据的多个版本。版本通过时间戳来索引。时间戳的类型是64位整型。时间戳可以由HBASE(在数据写入时自动)赋值，此时时间戳是精确到毫秒的当前系统时间。时间戳也可以由客户显示赋值。如果应用程序要避免数据版本冲突，就必须自己生成具有唯一性的时间戳。每个cell中，不同版本的数据按照时间倒序排序，即最新的数据排在最前面。
