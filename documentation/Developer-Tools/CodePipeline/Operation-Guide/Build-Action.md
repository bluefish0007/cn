# 操作类型-构建

构建是基于用户提供的源代码，生成软件包/镜像的自动化编译过程。目前流水线集成了[京东云-云编译](../../../Developer-Tools/CodeBuild/Introduction/Product-Overview.md)。

## 参数说明

参数名称|参数说明
:---|:---
操作类型|构建
操作名称|根据操作类型默认生成操作名，如构建-默认-1.一条流水线里面，操作名保持唯一
操作提供方|构建系统。流水线集成了[京东云-云编译](../../../Developer-Tools/CodeBuild/Introduction/Product-Overview.md)产品用于构建
代码源|选择前面阶段添加的源代码，作为云编译任务的输入commitId
云编译-任务|选择「代码源」对应的云编译任务。会根据代码源中的仓库地址过滤云编译任务
手动确认|选择流转到下一阶段的方式。如果选择手动流转，本阶段会在用户点击确认后执行
