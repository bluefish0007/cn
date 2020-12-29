 **版本生效日期：2021年1月1日**
 

本服务等级协议（Service Level Agreement，简称 “SLA”）规定了京东智联云向客户提供的容器镜像仓库服务可用性等级指标及赔偿方案。

 
**1.** **定义**

**服务周期** ：一个服务周期为一个自然月。

**服务周期总分钟数：** 服务周期内的总天数╳24（小时）╳60（分钟）计算。

**服务不可用：** 当某一分钟内，客户端尝试访问指定注册表里的任一容器镜像仓库，均持续出现内部错误或是无法上传，拉取镜像等故障，且持续时间覆盖该分钟，则视为该分钟内该注册表不可用。

**服务不可用分钟数** ： 在一个服务周期内服务不可用分钟数之和。

**月度服务费：** 为客户在一个服务周期（即自然月）中单个注册表按使用容量占所有注册表所使用容量比例分摊容器镜像仓库服务在该服务周期支付的总服务费用后的费用，如客户一次性支付多个月份的服务费，则将按照所购买的月数分摊计算月度服务费。

 

**2.** **服务可用性**

**2.1** **服务可用性计算公式**

服务可用性以单个注册表为维度，按照如下方式计算：

服务可用性=（服务周期总分钟数 - 服务不可用分钟数）/服务周期总分钟数×100%。

**2.2** **服务可用性承诺**

服务可用性不低于99.95%，如未达到前述可用性承诺，客户可以根据本协议第3条约定获得赔偿。

**2.3** **除外情形**

**因下述原因导致的服务不可用的时长不计入服务不可用时间：**

（1）京东智联云预先通知用户后进行系统维护所引起的，包括割接、维修、升级和模拟故障演练；

（2）由于运营商故障导致的丢包和延时等不可用情况；

（3）客户的应用程序或数据信息受到黑客攻击而引起的；

（4）客户维护不当或保密不当致使数据、口令、密码等丢失或泄漏所引起的；

（5）客户的疏忽或由客户授权的操作所引起的；

（6）由于客户违反《容器镜像仓库服务条款》导致的服务被暂停或终止，包括由于欠费导致容器镜像仓库被暂停服务或被释放等；

（7）不可抗力引起的；

（8）容器镜像仓库依赖的第三方产品故障，如对象存储故障引起的；

（9）其他非京东智联云原因所造成的不可用。

 

**3.** **赔偿方案**

**3.1** **赔偿标准**

容器镜像仓库服务按所有注册表月度服务可用性，如服务可用性低于99.95%，可按照下表中的标准获得赔偿，赔偿方式仅限于用于购买容器镜像仓库产品的代金券，且赔偿总额不超过未达到服务可用性承诺当月，客户就容器镜像仓库服务支付的月度服务费的25%（不含用免费代金券抵扣的费用）。

| **服务可用性**              | **赔偿代金券金额** |
| --------------------------- | ------------------ |
| 99% ≤ 服务可用性 ＜  99.95% | 月度务费用的10%    |
| 服务可用性 ＜ 99%           | 月度服务费用的25%  |

 **3.2** **赔偿申请时限**

客户可以在每月第五（5）个工作日后对上个月没有达到可用性的情况提出赔偿申请。**赔偿申请必须限于在镜像容器仓库没有达到服务可用性的相关月份结束后两（2）个月内提出。超出申请时限的赔偿申请将不被受理。**

 

**4.** **其他**

本容器镜像仓库服务等级协议自2021年1月1日生效，京东智联云有权对本SLA条款作出修改。如本SLA条款有任何修改，京东智联云将提前15天以网站公示或发送邮件的方式通知您，生效时间为公示后的下一个服务周期即下一个自然月的第一天。如您不同意京东智联云对SLA所做的修改，您有权停止使用服务，如您继续使用服务，则视为您接受修改后的SLA。


 