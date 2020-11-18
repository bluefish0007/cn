# 核心概念

以下是安全加速 SCDN产品，帮助文档中使用到的概念及其解释，请参考。

**DoS（Denial of Service）**

即拒绝服务攻击。该攻击是利用目标系统网络服务功能缺陷或者直接消耗其系统资源，目的是使该目标客户的系统不可用，无法提供正常的服务。

**DDoS攻击**

分布式拒绝服务攻击(Distributed Denial of Service，DDoS)是指处于不同位置的多个攻击者同时向一个或数个目标发动攻击，或者一个攻击者控制了位于不同位置的多台机器并利用这些机器对受害者同时实施攻击。由于攻击的发出点是分布在不同地方的，这类攻击称为分布式拒绝服务攻击，其中的攻击者可以有多个。

**防火墙规则**

通过多条“与”、“或”运算符，组成的安全防护规则，通过定义一定的过滤条件，对请求进行阻止、JS挑战、允许、绕过等操作。
如可通过防火墙规则阻断来自某个区域的恶意攻击流量。

**WAF**

Web应用防火墙（Web Application Firewall，简称： WAF）。WAF是通过执行一系列针对HTTP/HTTPS的安全策略来专门为Web应用提供保护的防火墙。

**CNAME记录**

别名记录( Canonical Name )；如果需要将一个域名A指向到另一个域名B，再由域名B提供的IP地址，就需要添加CNAME记录。

**半接入**

半接入也称为Cname接入，域名接入安全加速需要用到CNAME记录，在京东智联云控制台配置完成加速域名后，用户会得到一个对应的加速CNAME域名（向*.*cnd.jdcloud-scdn.com），用户需要在域名服务商处配置 CNAME 记录，将域名作CNAME指向*.*cdn.jdcloud-scdndns.com的域名，这样，该域名所有的请求都将转向安全加速的节点。

**边缘节点**

也称SCDN POP节点、缓存节点等，即分布在各地各运营商，缓存源站内容的服务器集群。因其在物理上离用户最近，所以用户可以更快的获取内容，从而实现站点以及用户请求内容加速。