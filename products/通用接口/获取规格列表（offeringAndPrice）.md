## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/offeringAndPrice`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|resourceType|是|string|产品，取值列表如[ResourceType](#resourceType)所示，参数中resourceType与subResourceType至少传入一个|
|subResourceType|是|string|子产品，取值列表如[SubResourceType](#subResourceType)所示|
|regionId|否|string|地区id|
|zoneId|否|string|地域id|
|payType|否|string|付费方式，取值有prepaid与postpaid，代表先付费与后付费|
|specCode|否|string|规格代码|
|chargeType|否|string|计费维度，例如按时间或按流量|
|chargeCycle|否|string|计费周期，例如hour|

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

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | [OfferingList](#offeringList)	 | 请求返回数据 | 

<span id="offeringList"></span>
OfferingList:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| items | [][OfferingListDetail](#offeringListDetail) | 消费信息数据列表 |
| total | int64 | 总条目数 |

<span id="offeringListDetail"></span>
OfferingListDetail:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
|prices|[][Price](#price)|价格信息，一般有两条，分为先付费与后付费|
|offerings|[Offerings](#offerings)|规格信息|

<span id="price"></span>
Price:
|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
|regionId|string|地区id|
|zoneId|string|地域id|
|payType|string|付费方式|
|chargeType|string|计费维度，例如按时间（period）或按流量|
|chargeCycle|string|计费周期，例如hour|
|soldOut|bool|是否已经售罄|
|priceDescs|[]string|价格的描述|
|factors|map[string][Factor](#factor)|计费的因素描述|

<span id="factor"></span>
Factor:
|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
|unitDesc|string|单位描述|
|unitPrice|int64|单价，单位为分|
|unitVolume|int64|步长，配合value与unitDesc使用，例如unitVolume取值为3600，unitDesc为“秒”，那么则表示步长为一个小时，每value增加1，则增加3600秒，即一个小时|
|value|int64|如上述解释|
|range|[2]int64|value的取值范围，数组第一个元素为min，第二个为max|

<span id="offerings"></span>
Offerings:
|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
|resourceType|string|产品|
|subResourceType|string|子产品|
|specCode|string|产品规格代号|
|specs|map[string]object|每个产品不同，一些非兼容性的配置，例如dc2的cpu数等|

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/resourceUsageList \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "resourceType": "dc2",
    "subResourceType": "dc2.ebs",
    "regionId": "gz",
    "zoneId": "gz01",
    "payType": "prePaid",
    "specCode": "dc2.e1.small1",
    "chargeType": "period",
    "chargeCycle": "hour"
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": {
        "items": [
            {
                "prices": [
                    {
                        "regionId": "gz",
                        "zoneId": "gz01",
                        "payType": "prePaid",
                        "chargeType": "period",
                        "chargeCycle": "hour",
                        "offeringUuid": "f701edc5d47bb9c81559a4beeb90a2ae",
                        "soldOut": false,
                        "priceDescs": [],
                        "factors": {
                            "period": [
                                {
                                    "unitDesc": "second",
                                    "unitPrice": 1260,
                                    "unitVolume": 2592000,
                                    "value": 0,
                                    "range": [
                                        1,
                                        36
                                    ]
                                }
                            ]
                        }
                    },
                    {
                        "regionId": "gz",
                        "zoneId": "gz01",
                        "payType": "postPaid",
                        "chargeType": "period",
                        "chargeCycle": "hour",
                        "offeringUuid": "f701edc5d47bb9c81559a4beeb90a2ae",
                        "soldOut": false,
                        "priceDescs": [],
                        "factors": {
                            "period": [
                                {
                                    "unitDesc": "second",
                                    "unitPrice": 1512,
                                    "unitVolume": 2592000,
                                    "value": 0,
                                    "range": [
                                        1,
                                        36
                                    ]
                                }
                            ]
                        }
                    }
                ],
                "offerings": {
                    "resourceType": "dc2",
                    "subResourceType": "dc2.ebs",
                    "specCode": "dc2.e1.small1",
                    "specs": {
                        "dc2.cpuModel": 0,
                        "dc2.cpuNum": 1,
                        "dc2.cpuSpeed": 1,
                        "dc2.gpuNum": 0,
                        "dc2.memorySize": 1073741824,
                        "dc2.model": "dc2.e1.small1",
                        "dc2.name": "1CPU-1GMEM",
                        "dc2.type": "ebs",
                        "dc2.typeName": "通用型",
                        "gpuDeviceOfferingUuid": "",
                        "instanceOfferingUuid": "0cbfed2ba3344344a2a562d64e02baa4",
                        "rootDiskOfferingUuid": ""
                    }
                }
            }
        ],
        "total": 1
    }
}
```
