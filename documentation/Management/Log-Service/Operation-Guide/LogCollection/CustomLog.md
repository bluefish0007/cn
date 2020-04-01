## 业务应用日志采集
### 一、通过控制台采集

**注意事项：**

**日志采集agent无需用户手动安装，添加采集配置时选择的云主机会自动安装日志采集agent。确认采集配置即视为同意京东智联云日志服务在对应的云主机内自动安装日志采集agent。已手动安装采集agent的用户不受影响，仍可正常上报日志数据。**

前提条件：

1.在京东云云主机上已经部署了用户自己的业务应用。

2.已经创建了对应的日志集、日志主题和采集配置。

操作步骤：

1.进入日志主题列表页，选择“采集配置”状态为“未配置”的日志主题，点击操作列的“采集配置”，进入采集配置页面。

2.点击“添加采集配置”，进入添加采集配置页面。

3.填写采集配置信息

- 日志来源选择“业务应用”，
- 根据需求选择是否开启采集，如果关闭，则可在需要开启的时候进入采集配置页面编辑采集状态，如果开启，则采集配置创建成功后立即采集。
填写日志路径。该路径为用户业务应用在云主机上产生日志的存储路径，目录前缀支持问号和星号通配符。Linux文件路径应以/开头，例如：/var/log/db/db.log 等。暂不支持Windows云主机的日志采集。日志文本编码为UTF8。
- 选择需要采集的云主机。对于选择的云主机，日志服务会自动在对应的云主机内安装日志采集agent。

4.点击“保存”，完成采集配置的创建。在使用日志检索及日志转储功能时，要确保采集状态处于打开的状态。

5.设置完成后，5分钟左右后即会有最新的日志数据上报至日志服务。

