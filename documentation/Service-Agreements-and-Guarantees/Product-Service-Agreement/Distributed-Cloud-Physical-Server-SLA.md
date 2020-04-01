### 1.服务范围

本服务等级协议（Service Level Agreement，以下简称 “SLA”）规定了京东智联云向客户提供分布式云物理服务器（Distributed Cloud Physical Server，简称“DCPS”）的服务可用性等级指标及赔偿方案，京东智联云的其他服务器产品不在本服务等级协议覆盖范围内。

### 2.服务等级指标

#### 2.1服务可用性

京东智联云提供的分布式云物理服务器旨在为客户提供性能卓越的独享物理服务器，允许客户快速在线购买物理服务器、部署操作系统，设置公网和内网IP地址、设置网络带宽资源，并支持按需弹性扩容物理服务器和网络带宽资源等。分布式云物理服务器提供基于云计算模式的按需使用和按需付费的在线结算功能。分布式云物理服务器适用于游戏、互动直播、视频监控、在线教育等多种应用场景。分布式云物理服务器的所有具体功能请详见京东智联云在官网上提供的详细帮助文档。分布式云物理服务器服务所有可能影响客户的功能性变更都将向客户公告。

#### 2.2服务可用性


服务周期：一个服务周期为一个自然月，如不满一个自然月不计算为一个服务周期。
服务周期分钟数：指按照一个服务周期内实际总天数×24（小时）×60（分钟）计算所得的分钟时长。

服务周期不可用分钟数：指一个服务周期内单用户的单台分布式云物理服务器发生无冗余硬件故障，导致该分布式云物理服务器无法使用需要停机维护的累计分钟时长。

服务可用性计算公式：（一个服务周期内单用户单节点内所有服务器的服务周期分钟数之和 – 一个服务周期内单用户单节点内所有服务器的服务周期不可用分钟数之和）/（一个服务周期内单用户单节点内所有服务器的服务周期分钟数之和）× 100%。

服务器可用性承诺：一个服务周期内单用户单节点的服务可用性不低于99.5%

（节点：指的是京东智联云的边缘机房所处的不同地理位置（大区-城市），不同节点之间是完全隔离的，提供的服务通过公网进行通讯）。 

#### 2.3数据可销毁性

在用户要求删除数据或设备在弃置、转售前、到期回收时，京东智联云将采取技术手段彻底删除磁盘上的所有数据，确保数据无法复原。设备报废时，磁盘将进行消磁。

#### 2.4数据可迁移性

用户启用分布式云物理服务器时，可以通过公网或内网自行迁移数据。

#### 2.5数据私密性

京东智联云提供的分布式云物理服务器在客户租用期间为客户独享；在网络层面，通过用户自定义的vpc实现网络隔离，默认归属同一vpc的分布式云物理服务器才能内网互通。

#### 2.6数据知情权

用户购买分布式云物理服务器时可根据需求选择已有数据中心购买服务器。

用户可选择的已有数据中心均遵守的当地的法律和中华人民共和国相关法律。

用户所有数据不会提供给任意第三方，除政府监管部门监管审计需要。

#### 2.7数据可审查性

依据现行法律法规或根据政府监管部门监管、安全合规、审计或取证调查等原因的需要，在符合流程和手续完备的情况下，京东智联云可以提供用户所使用的服务的相关信息，包括关键组件的运行日志、运维人员的操作记录、用户操作记录等信息。

#### 2.8服务资源调配能力

分布式云物理服务器提供多种配置的机型供用户选择。用户可根据需要按照京东智联云配置方案自行选择适合自己应用场景的分布式云物理服务器类型和数量。分布式云物理服务器支持在线实时升级公网带宽。

#### 2.9网络接入性能

用户在开通京东智联云分布式云物理服务器时，可选择为分布式云物理服务器增加边缘云公网IP（即EIP），并设置边缘云公网IP所需的公网出口带宽，默认上行带宽和下行带宽为1:1，可配置的范围从1Mbps最高至10000Mbps（10000Mbps为可提供的带宽最大值，根据不同节点该最大值可能会不同，请根据实际节点合理选择；若上行带宽不够用，可以额外申请）。

#### 2.10服务计量准确性
分布式云物理服务器具备准确、透明的计量计费系统，京东智联云根据用户的分布式云物理服务器的计费类型、实际使用时长和购买数量进行扣费结算。具体计费&扣费标准以京东智联云官网公布的有效的计费模式、价格和扣费方法为准。用户的原始计费日志默认最少保留3年备查。

### 3. 服务赔偿条款

#### 3.1 赔偿范围：

因京东智联云设备故障、设计缺陷或操作不当导致用户所购买的分布式云物理服务器无法正常使用，京东智联云将对不可用时间进行赔偿，但不包括以下原因所导致的服务不可用时间：

（1）京东智联云预先通知用户后进行系统维护所引起的，包括割接、维修、升级和模拟故障演练；

（2）任何京东智联云所属设备以外的网络、设备故障或配置调整引起的；

（3）客户的应用程序或数据信息受到黑客攻击而引起的；

（4）客户维护不当或保密不当致使数据、口令、密码等遗忘、丢失、或泄漏所引起的；

（5）客户自行升级操作系统所引起的；

（6）客户的应用程序或安装活动所引起的；

（7）客户的疏忽或由客户授权不当的操作所引起的；

（8）不可抗力以及意外事件引起的；

（9）由于客户违反《京东智联云服务协议》导致的分布式云物理服务器被暂停或终止，包括但不限于由于订单过期或者账号欠费导致分布式云物理服务器被暂停服务或被释放等；

（10）其他非京东智联云原因所造成的不可用。

#### 3.2 赔偿方案

故障时间=不可用时间。

包年包月的分布式云物理服务器以服务时长补偿的方式，按故障时间100倍/台赔偿。

按配置付费的分布式云物理服务器以代金券的形式补偿，赔付金额=故障前24小时平均每小时费用/60×故障时间×100。

说明：

京东智联云通过赠送代金券的方式进行赔偿，赠送代金券仅支持购买分布式云物理服务器产品，赔偿总额不超过当月用户就该分布式云物理服务器实例已支付的月度服务费用（不含赠送余额或代金券抵扣的费用）。

按配置付费的分布式云物理服务器使用时间如果小于24小时，按实际使用时长平均值计算费用；故障时间按分计算。
### 4.其他
京东智联云有权根据变化适时对本服务等级协议部分服务指标作出调整，并及时在京东智联云官网[www.jdcloud.com](https://www.jdcloud.com) 发布公告或发送邮件或书面通知向用户提示修改内容。如您不同意京东智联云对本服务等级协议所做的修改，您有权停止使用分布式云物理服务器服务，如您继续使用分布式云物理服务器服务，则视为您接受修改后的服务等级协议。
