## **网站防篡改**

您可以使用网站防篡改对指定的敏感页面设置缓存，缓存后即使源站页面内容被恶意篡改，WAF也会向访问者返回预先缓存好的页面内容，确保用户看到正确的页面。

### **操作步骤**

参照以下步骤，启用并配置网站防篡改：

**说明：** 执行以下操作前，请确保已将网站接入WAF进行防护。具体操作请参考CNAME接入指南
1. 登录[京东云Web应用防火墙控制台](https://cloudwaf-console.jdcloud.com)。

2. 前往**网站配置**页面。

3. 选择要操作的域名，单击其操作列下的**防护配置**。

4. 在**网站防篡改**下，启用防护，并单击**前去配置**。 **说明：** 如果您不想使用网站防篡改，您可以在该页面关闭防护。
![image.png](../../../../../image/waf-img/%E7%BD%91%E9%A1%B5%E9%98%B2%E7%AF%A1%E6%94%B9-1.png)

5. 单击**新增规则**，在添加URL对话框配置要防护的具体页面。
![image.png](../../../../../image/waf-img/%E7%BD%91%E9%A1%B5%E9%98%B2%E7%AF%A1%E6%94%B9-2.png)

6. **规则名称**：为该规则命名。

   **URL**：填写精确的要防护的路径。

7. 添加规则后，手动打开对应规则**防护状态**下的开关。如果您在添加规则后未打开防护开关，则设置不会生效。
![image.png](../../../../../image/waf-img/%E7%BD%91%E9%A1%B5%E9%98%B2%E7%AF%A1%E6%94%B9-3.png)

8. 如果被防护页面进行了内容更新，您必须单击**更新缓存**来更新缓存。如果您在页面更新后未更新缓存，WAF将始终返回最近一次缓存的页面内容。
![image.png](../../../../../image/WAF/fanchgai1.png)

 
