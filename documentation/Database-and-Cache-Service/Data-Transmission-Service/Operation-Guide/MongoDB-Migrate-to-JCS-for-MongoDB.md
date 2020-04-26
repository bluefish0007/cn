# 自建MongoDB迁移至云数据库MongoDB

本文介绍如何使用数据传输 DTS 将自建MongoDB数据库迁移至云数据库MongoDB。

数据传输 DTS 支持结构迁移、全量迁移、增量迁移，您可以根据实际情况选择使用。

## 注意事项

### 源数据库配置要求

连接方式：

- 源数据库有公网IP的自建数据库

数据库版本：

- MongoDB 3.2 版
- MongoDB 3.4 版
- MongoDB 3.6 版

数据库配置：

- 需要为副本集模式

账号权限：

- 待迁移库的读权限。
- admin库的读权限。

### 目标数据库版本与配置要求

数据库版本：

- 与源数据库版本一致或更高版本。

账号权限：

- 写权限

数据要求：

- 不能存在与待迁移数据库重名的库。

## 操作步骤

1. 创建迁移任务。

   - 任务名称：名称长度不能少于2字符且不超过32个字符，只支持中文、数字、大小写字母、英文下划线及中划线。

   - 源库信息：

     - 数据库类型，选择“有公网IP的自建数据库”。
     - 数据库类型，选择MongoDB。
     - 数据库地址，填写数据库的域名或IP。
     - 端口，数据库端口。
     - 账号和密码，请提前确认账号具备相应的权限。

   - 目标库信息：

     - 数据库类型，请选择“云数据库 MongoDB”
     - 地域，选择目标实例所在地域。
     - 实例ID，请选择目标实例。
     - 鉴权库、账号和密码，请提前确认账号具备相应的权限。

   - 迁移类型

     - 请选择迁移类型，可选择全量迁移、增量迁移。

   - 选择迁移对象

     - 支持按库、表迁移。

     - 源库类型为“有公网IP的自建数据库”时，支持**可视化选择**和**JSON**两种方式定义要迁移的库表。

     - 说明

       MongoDB不迁移以下数据：

       \- 库：amdin、local、config。

       \- 集合：以"system."开头的集合，包含"$"的集合。

       当一个库内包含超过100个表时，不支持按表选择，只可选择当前库或通过JSON方式指定表。

2. 启动迁移任务。

   - 在任务列表页或详情页，点击**启动**，启动迁移任务。任务启动后，第一步将执行预检查。
   - 预检查成功后，在预检查弹窗中点击**下一步**，执行数据迁移。

3. 结束迁移任务。

   - 迁移类型为全量迁移时，数据迁移完成后，任务自动结束。
   - 迁移类型为增量迁移时，需要手动结束迁移任务，建议目的库数据追上源库时，停止源库写入，检查目的库数据无误后，结束迁移任务。
   - 注意：迁移任务结束后，将不能再次开启。