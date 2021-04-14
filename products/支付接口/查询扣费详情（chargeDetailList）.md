## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/chargeDetailList`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| resourceUuids | 否 | []string |资源uuid列表，缺省时无限制|
| startTime | 是 | int64 |查询起始时间，取毫秒为单位的unix_timestamp|
| endTime | 是 | int64 | 查询结束时间，取毫秒为单位的unix_timestamp，与start之间间隔不能大于1周 |
| limit  | 否 | int16  | 查询限制数目，缺省为10，最大为100 |
| offset  | 否 | int32  | 查询起止index，缺省为0，配合limit使用 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | [ChargeDetailList](#chargeDetailList)	 | 请求返回数据 | 

<span id="chargeDetailList"></span>
ChargeDetailList:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| items | [ChargeDetail](#chargeDetail) | 计费详细信息数据列表 |
| total | int64 | 总条目数 |

<span id="chargeDetail"></span>
ChargeDetail:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| resourceType | string | 资源所属产品，取值列表如[ResourceType](#resourceType)所示 |
| subResourceType | string | 资源所属子产品，取值列表如[SubResourceType](#subResourceType)所示 |
| resourceName | string | 资源名称 |
| value | float | 消费金额（单位为元，保留小数点后三位） |
| regionId | string | 地区id |
| zoneId | string | 地域id |
| startTime | int64 | 计费起始时间，取毫秒为单位的unix_timestamp |
| endTime | int64 | 计费结束时间，取毫秒为单位的unix_timestamp |
| resourceUuid | string | 资源id |
| resourceCreateTime | int64 | 资源创建时间，取毫秒为单位的unix_timestamp |
| chargeDetailStatus | string | 计费信息的状态，取值有'未结算','已结算' |
| parentResourceUuid | string | 父资源uuid |
| resourceStatusList | [][StatusStruct](#statusStruct) | 资源的状态列表，按时间顺序 |

<span id="statusStruct"></span>
StatusStruct:
|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| startTime | int64 | 状态起始时间，取毫秒为单位的unix_timestamp |
| endTime | int64 | 状态结束时间，取毫秒为单位的unix_timestamp |
| status | string | 状态，取值见[Status](#status) |

<span id="subResourceType"></span>
SubResourceType:

| 取值 | 描述 |
| ------ | ----- |
|dc2.ssd|云服务器本地SSD型|
|dc2.ebs.gpu.p4|云服务器GPU通用P4型|
|dc2.ssd.enhanced|云服务器本地SSD增强型|
|dc2.ebs.gpu.p40|云服务器GPU通用P40型|
|dc2.ebs.gpu.p100|云服务器GPU通用P100型|
|dc2.ssd.enhanced.gpu.p4|云服务器GPU本地SSD增强P4型|
|dc2.ssd.enhanced.gpu.p40|云服务器GPU本地SSD增强P40型|
|dc2.ssd.enhanced.gpu.p100|云服务器GPU本地SSD增强P100型|
|dc2.ebs|通用型云服务器|
|dc2.ebs.gpu.g4|云服务器GPU通用G4型|
|dc2.ssd.enhanced.gpu.g4|云服务器GPU本地SSD增强G4型|
|dc2.ssd.float|云服务器本地SSD浮动型|
|snap|快照|
|ebs|云盘|
|eip|带宽|
|slb.eip|负载均衡带宽|
|slb|负载均衡|
|waf|Web应用防火墙|
|s3|对象存储|
|mysql|云关系数据库|
|ssl-cert|SSL证书|
|host-sec|主机安全专业防护|
|speech|语音识别|
|ddos.fixed|高防保底带宽|
|ddos.elastic|高防弹性带宽|
|ddos.flow|高防转发流量|
|cache|云弹性缓存|
|eis|云弹性推理|
|storagePackage|存储包|
|nas|文件存储|
|dai.jupyter|机器学习Jupyter Notebook|

<span id="resourceType"></span>
ResourceType:

| 取值 | 描述 |
| ------ | ----- |
|dc2|云服务器|
|snap|快照|
|ebs|云盘|
|eip|带宽|
|slb.eip|负载均衡带宽|
|slb|负载均衡|
|waf|Web应用防火墙|
|s3|对象存储|
|mysql|云关系数据库|
|ssl-cert|SSL证书|
|host-sec|主机安全专业防护|
|speech|语音识别|
|ddos|高防|
|cache|云弹性缓存|
|eis|云弹性推理|
|storagePackage|存储包|
|nas|文件存储|
|dai|托管产品|

<span id="status"></span>
Status:

| 取值 | 描述 |
| ------ | ----- |
|Running|云服务器-运行中|
|Stopping|云服务器-停止中|
|Stopped|云服务器-已停止|
|Destroyed|云服务器-已删除|
|Expunged|云服务器-已释放|
|Ready|云盘-正常|
|Deleted|云盘-已删除|
|Expunged|云盘-已释放|
|Active|带宽-正常|
|Inactive|带宽-不正常（阻断）|
|Deleted|带宽-已删除|
|Expunged|带宽-已释放|

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/chargeDetailList \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"startTime":1587387400000,
	"endTime":1587387600000,
	"offset":0,
	"limit":10,
	"resourceUuids":["bb98762e5e9d058d7ac40eb97eb1fb02"]
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "requestId": "0a59c12e5e9d058d7ac40eb97eb1fb02",
    "data": [
        {
            "resourceType": "dc2",
            "subResourceType": "dc2.ebs",
            "resourceName": "云服务器-es-01",
            "startTime": 1587387400000,
            "endTime": 1587391000000,
	    "value": 0.515,
            "resourceCreateTime":1587387400000,
            "parentResourceUuid":"cc98762e5e9d058d7ac40eb97eb1fb02",
            "regionId": "gz",
            "zoneId": "gz01",
            "resourceUuid": "bb98762e5e9d058d7ac40eb97eb1fb02",
            "resourceStatusList": [
                {
                    "startTime": 1587387400000,
                    "endTime": 1587391000000,
                    "status": "Running"
                }
            ]
        }
    ],
    "total": 1
}
```
