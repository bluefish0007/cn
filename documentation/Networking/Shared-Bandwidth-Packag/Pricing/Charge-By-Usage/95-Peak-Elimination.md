# 按95消峰计费

本文将详细介绍按95消费计费的共享带宽实例的计费规则。

### 详细介绍

- 按用量计费每天收取保底带宽费用，并每天根据共享带宽包实际使用流量出账单；

- 若月平均超保底带宽大于0，则会收取超保底带宽费用；

- 目前保底带宽按照购买带宽上限的20%设定，此时保底带宽单价和超保底带宽单价相同。

- 选择按95消峰计费模式至少需要使用一个完整的自然月，最早支持在下个月出完账单之后删除。

### 计费公式

- 每个共享带宽包的月度费用 = 保底带宽费用 + 超保底带宽费用



#### 保底带宽费用

- 保底带宽 = 共享带宽上限 × 保底带宽百分比

- 保底带宽费用 = 保底带宽1 × 95消峰保底带宽价格1 × 实例对应保底带宽存在天数1 + 保底带宽2 × 95消峰保底带宽价格2 × 实例对应保底带宽存在天数2 + ....。

一个月中共享带宽包经过变配操作，存在不同的共享带宽上限，进而存在不同的保底带宽1、保底带宽2，...。

- 月平均保底带宽 = 保底带宽费用 / 实例对应计费周期存在天数。



#### 超保底带宽费用

- 月平均超保底带宽 = MAX（0，(月95消峰带宽 – 月平均保底带宽）)

- 超保底带宽费用 = 月平均超保底带宽 × 95消峰超保底带宽价格 × 实例对应计费周期存在天数。

- 月95消峰带宽计算方法如下：

将1个月内全部平均带宽值（30天算，约8640个点）从高到低进行排列，算出全部点的5%对应的点编号（非整数直接取整，如431.95，则取431），5%对应的点的下一个点对应的平均带宽则为消峰带宽值（如431，则取第432个点作为消峰带宽值），下图为1个完整自然月采样和计费方法。


![img](../../../../image/Networking/Shared-Bandwidth-Packag/95-peak-elimination.png)



#### 公式变量说明

- 95消峰保底带宽价格 ：保底带宽所对应的95消峰保底带宽价格。

- 月平均超保底带宽以月为粒度计算，当月平均超保底带宽为月95消峰带宽和月平均保底带宽的差与0中大的那个值。

- 实例对应保底带宽存在天数：以某个保底带宽值计算保底带宽费用的天数

- 实例对应计费周期存在天数：计费周期时间（单位：秒）/（24\*60\*60），实例存在天数小数部分取小数点后2位，其他小数位直接舍弃。



### 共享带宽包定价

| 计费类型   | 保底带宽站带宽上限的百分比 | 保底带宽月单价（元/Mbps/月） | 保底带宽日单价（元/Mbps/天） | 超保底带宽月单价（元/Mbps/月） | 超保底带宽日单价（元/Mbps/天） |
| ---------- | -------------------------- | ---------------------------- | ---------------------------- | ------------------------------ | ------------------------------ |
| 传统95消峰 | 20%                        | 110.70                       | 3.69                         | 110.70                         | 3.69                           |

### 计费实例

假设您够买了1个月按95消峰计费模式的共享带宽包，带宽上限为30Gbps，保底带宽百分比为20%，按照上述消峰方法消峰带宽为6.745Gbps，共享带宽包的总费用为6.745 * 110.70=746671.5元（超保底带宽单价和保底带宽单价一致）。



### 账单说明

- 账单周期：保底带宽费用及超保底带宽费用按月出账单，可提供精确到天的费用明细。

- 出账时间：通常为当前计费周期结束的下个自然月1日。例如：3月1日会生成2月份完整月（2020-02-01 00:00:00 至 2020-02-29 23:59:59）的超保底带宽计费账单。

- 结算时间：账单生成后会自动从您的账户余额中扣除费用以结算账单。请确保结算时账户的余额充足，以免出现欠费问题。



### 变配计费规则

- 按用量计费模式支持实时调节共享带宽上限，并立刻生效。调整完共享带宽上限后，保底带宽也会随之变化。

- 按用量计费模式的共享带宽包不支持调整保底带宽百分比。目前仅支持的百分比为20%。

- 升配/降配 ：以天为粒度计算，每天的保底带宽为当天设置过的最大保底带宽。例如：一天中进行过带宽上限调整: 1000Mbit/s -> 3000Mbit/s -> 2000Mbit/s，则当天的保底带宽为3000Mbit/s\*20%=600Mbit/s。

- 实例对应计费周期存在天数：计费周期时间（单位：秒）/（24\*60\*60），实例存在天数小数部分取小数点后2位，其他小数位直接舍弃。



### 欠费说明

- 每月初结算上个月费用并出账单，当您的账户中余额加可用于支付该付费网络资源的代金券的总和不足，导致扣款不成功，您的付费网络资源（共享带宽包）的状态会变为欠费；

- 当您的付费网络资源欠费后，将停止服务且停止扣费；

- 欠费后，京东智联云会向您发送邮件和短信，通知您的资源已欠费，请您务必注意查看通知并及时充值，以免造成不必要的损失；

- 从停止服务时刻起，您的付费网络资源和资源中的数据保留7天

- 若您在7天内完成补缴欠费金额，被停用的付费资源恢复正常使用；

- 若您在7天内未完成补缴欠费金额，被停用的付费资源将被释放。共享带宽内的弹性公网IP将自动退出共享带宽并恢复为加入之前的带宽峰值和计费方式。

- 若您不想继续使用按用量的付费网络资源，请及时将该资源进行删除。



注意：实际使用天数和共享带宽中是否有业务流量无关，如果创建后不使用也会计算实际使用天数。