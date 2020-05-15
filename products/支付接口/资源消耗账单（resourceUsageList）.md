## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/resourceUsageList`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| resourceType | 否 | []string |子资源类型，取值列表如[ResourceType](#resourceType)所示，缺省为all|
| year | 是 | int16 |消耗查询年，因消耗是按照自然月来结算的，所以查询时间以整月为准|
| month | 是 | int16 | 消耗查询月，取值1~12 |
| limit  | 否 | int16  | 查询限制数目，缺省为10，最大为100 |
| offset  | 否 | int32  | 查询起止index，缺省为0，配合limit使用 |
| sortBy  | 否 | string  | 排序字段，当前支持stime（起始时间）/etime（结束时间）/id |
| sortDirection  | 否 | string  | 排序策略，支持desc/asc，缺省asc |

<span id="resourceType"></span>
SubResourceType:

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
|data | [UsageList](#usageList)	 | 请求返回数据 | 

<span id="usageList"></span>
UsageList:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| items | [UsageListDetail](#usageListDetail) | 消费信息数据列表 |
| total | int64 | 总条目数 |
| totalValue | float | 总消费金额（单位为元，保留小数点后三位） |

<span id="usageListDetail"></span>
UsageListDetail:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
|startTime|int64|此条消耗记录的开始时间，取毫秒为单位的unix_timestamp|
|endTime|int64|此条消耗记录的结束时间，取毫秒为单位的unix_timestamp|
|resourceType|string|资源类型|
|subResourceType|string|子资源类型|
|subResourceTypeInCh|string|子资源类型中文描述|
|description|string|此条消耗记录的中文描述|
|originValue|float|原价应付|
|value|float|实际支付|
|duration|int64|消耗时长（单位为秒）|
|resourceUuid|string|资源的uuid|
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
  https://open.didiyunapi.com/dicloud/w/resourceUsageList \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "resourceType": [
        "all"
    ],
    "year": 2020,
    "month": 4,
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
                "resourceType": "dc2",
                "subResourceType": "dc2.ebs",
                "subResourceTypeInCh": "通用型云服务器",
                "description": "通用型云服务器 10.255.1.59(内) | 1CPU-2GMEM",
                "startTime": 1586946425000,
                "endTime": 1587436025000,
                "duration": 489600,
                "originValue": 107.14,
                "value": 107.14,
                "resourceUuid": "d487897840ab5da3a171323d34dc1e4c",
                "resourceTag": [],
                "regionId": "gz",
                "regionName": "广州",
                "zoneId": "gz01",
                "zoneName": "广州一区"
            }
        ],
        "total": 1,
        "totalValue": 107.14
    }
}
```
