# describeBackupPolicy


## 描述
获取备份策略

## 请求方式
GET

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/backupPolicy

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|
|**instanceId**|String|True| |Instance ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](describebackuppolicy#result)| |

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**preferredBackupPeriod**|String| |
|**preferredBackupWindow**|String| |
|**backupRetentionPeriod**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
