# 计费概述

共享带宽支持包年包月、按配置、按用量三种付费类型，其中按用量计费支持按增强95；均支持动态调整带宽上限。

## 收费项目

#### 包年包月

- 预付费，在创建共享带宽实例时按照带宽配置计费；

- 计费周期为月，至少购买1个月；


#### 按配置计费

- 后付费，按带宽配置计费；

- 计费周期为小时，每小时出账单；

- 支持转换成包年包月计费模式；


#### 按用量计费

- 后付费，支持按增强95消峰计费；

- 只需支付少量保底带宽费用，即可享受多倍弹性峰值带宽；

- 每天收取少量保底费用，并根据实际用量出账单，若实际用量超出保底带宽需付费超额带宽费用，若未超出保底带宽用量则只需付保底带宽费用；

详情请参考[增强95消峰计费](Charge-By-Usage/Top5-Eliminate.md)。

## 欠费/到期说明

#### 包年包月到期说明

- 您的包年包月付费网络资源到期前，京东智联云会向您发送邮件、短信，提醒您的资源即将到期，请您注意查看并及时续费；

- 包年包月付费类型的共享带宽包到期后将停止服务，从停止服务时刻起，您的付费网络资源和资源中的数据保留7天。

- 若您在7天内在控制台完成续费，实例将恢复正常使用状态。

- 若您在7天内未完成续费或续费不成功，7天后实例将被释放。共享带宽内的弹性公网IP将自动从共享带宽包中移除并恢复为加入之前的带宽峰值和计费方式。

#### 按配置欠费说明

- 当您的账户中余额加可用于支付该付费网络资源的代金券的总和不足以支付下一计费周期费用时，导致扣款不成功，您的付费网络资源（共享带宽包）的状态会变为欠费；

- 当您的付费网络资源欠费后，将停止服务且停止扣费；

- 欠费后，京东智联云会向您发送邮件和短信，通知您的资源已欠费，请您务必注意查看通知并及时充值，以免造成不必要的损失；

- 从停止服务时刻起，您的付费网络资源和资源中的数据保留7天；

- 若您在7天内完成补缴欠费金额，被停用的付费资源恢复正常使用；

- 若您在7天内未完成补缴欠费金额，被停用的付费资源将被释放，共享带宽内的弹性公网IP将自动退出共享带宽并恢复为加入之前的带宽峰值和计费方式；

- 若您不想继续使用按用量的付费网络资源，请及时将该资源进行删除。

#### 按用量欠费说明

- 每月初结算上个月费用并出账单，当您的账户中余额加可用于支付该付费网络资源的代金券的总和不足，导致扣款不成功，您的付费网络资源（共享带宽包）的状态会变为欠费；

- 当您的付费网络资源欠费后，将停止服务且停止扣费；

- 欠费后，京东智联云会向您发送邮件和短信，通知您的资源已欠费，请您务必注意查看通知并及时充值，以免造成不必要的损失；

- 从停止服务时刻起，您的付费网络资源和资源中的数据保留7天；

- 若您在7天内完成补缴欠费金额，被停用的付费资源恢复正常使用；

- 若您在7天内未完成补缴欠费金额，被停用的付费资源将被释放，共享带宽内的弹性公网IP将自动退出共享带宽并恢复为加入之前的带宽峰值和计费方式；

- 若您不想继续使用按用量的付费网络资源，请及时将该资源进行删除。


## 相关参考

- [计费规则](Billed-Rules.md)

- [价格总览](price-Overview.md)

- [增强95消峰计费](Charge-By-Usage/Top5-Eliminate.md)

