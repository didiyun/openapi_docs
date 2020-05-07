## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/resourceConsumeList`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| subResourceType | 否 | []string |子资源类型，取值列表如[SubResourceType](#subResourceType)所示，缺省为all|
| startTime | 是 | int64 |查询起始时间，取毫秒为单位的unix_timestamp（针对后付费而言，只要在这个时间段内还有消费，即可筛选出来）|
| endTime | 是 | int64 | 查询结束时间，取毫秒为单位的unix_timestamp |
| limit  | 否 | int16  | 查询限制数目，缺省为10，最大为100 |
| offset  | 否 | int32  | 查询起止index，缺省为0，配合limit使用 |

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

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | [ConsumeList](#consumeList)	 | 请求返回数据 | 

<span id="consumeList"></span>
ConsumeList:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| items | [ConsumeListDetail](#consumeListDetail) | 消费信息数据列表 |
| total | int64 | 总条目数 |
| totalValue | float | 总消费金额（单位为元，保留小数点后三位） |

<span id="consumeListDetail"></span>
ConsumeListDetail:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
|startTime|int64|此条消费记录的开始时间，取毫秒为单位的unix_timestamp|
|endTime|int64|此条消费记录的结束时间，取毫秒为单位的unix_timestamp|
|resourceType|string|资源类型|
|subResourceType|string|子资源类型|
|subResourceTypeInCh|string|子资源类型中文描述|
|description|string|此条消费记录的中文描述|
|originValue|float|原价应付|
|value|float|实际支付|
|resourceId|string|资源的uuid|
|resourceTag|[]string|资源的标签|
|regionId|string|地区id|
|regionName|string|地区中文描述|
|zoneId|string|地域id|
|zoneName|string|地域中文描述|



## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/resourceConsumeList \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "subResourceType": [
        "all"
    ],
    "startTime": 1586447376000,
    "endTime": 1586447376000,
    "offset": 0,
    "limit": 10
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": {
        "items": [
            {
                "startTime": 1586447376000,
                "endTime": 1586447376000,
                "resourceType": "dc2",
                "subResourceType": "dc2.ebs",
                "subResourceTypeInCh": "通用型云服务器",
                "description": "通用型云服务器 10.255.1.59(内) | 1CPU-2GMEM",
                "originValue": "34.20",
                "value": "34.20",
                "resourceId": "d487897840ab5da3a171323d34dc1e4c",
                "resourceTag": [],
                "regionId": "gz",
                "regionName": "广州",
                "zoneId": "gz01",
                "zoneName": "广州一区"
            }
        ],
        "total": 1,
        "totalValue": "34.2"
    }
}
```
