## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/m/api/data`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| counter | 是 | array<[CounterInput](#CounterInput)> | 要查询的counter列表 |


<span id="CounterInput"></span>
CounterInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| resourceType | 是 | string | 要查询counter的资源类型 |
| resourceUuid | 是 | string | 要查询counter的资源uuid |
| monitorTags | 是 | string | 要查询的曲线tags |
| metric | 是 | string | 要查询的指标名称（[指标名类型](/static/docs-content/products/监控接口/根据指标名查询counter索引（MonitorCounter）.md#MetricEnum)） |
| startTime | 是 | int64 | 开始时间，单位为秒时间戳 |
| endTime | 是 | int64 | 结束时间，单位为秒时间戳 |


## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[MetricOutput](#MetricOutput)>   | 请求返回数据|

<span id="MetricOutput"></span>
MetricOutput：

|参数名称 | 类型 | 描述|
|--------|-----|-----|
| resourceType     |   string  |   资源类型    |
| monitorTags     |   string  |   所查询的曲线tags    |
| metric     |  string  |   监控指标名（[指标名类型](/static/docs-content/products/监控接口/根据指标名查询counter索引（MonitorCounter）.md#MetricEnum)）     |
| metricAlias     |   string  |   监控指标别名     |
| values | array<[Value](#Value)> | 曲线上的点坐标  |

<span id="Value"></span>
Value：

|参数名称 | 类型 | 描述|
|--------|-----|-----|
| timestamp     |   int64  |   对应时间点，单位为秒时间戳     |
| value  |   int64 |  对应指标值 | 


## 错误码
|错误码 | 说明    |
|------|------|
| 0    | 请求成功  |


## 示例

```
请求：
curl -X POST \
  https://open.diidyunapi.com/dicloud/m/api/data \
  -H 'Authorization: Bearer 9a23d72c1f9d5b39a2d96c474b3d308f5f3d8a5a5b865a7ea3618366cebcc0fc' \
  -H 'Content-Type: application/json;charset=UTF-8' \
  -d '{
    "regionId": "gz",
    "counter": [
        {
            "resourceType": "eip",
            "resourceUuid": "2c0faf76ff8454ec9713d808e67e7ef0",
            "monitorTags": "",
            "metric": "rxbytes",
            "startTime": 1551200000,
            "endTime": 1551201000
        }
    ]
}'

输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": [
        {
            "endTime": 1551201000,
            "metric": "rxbytes",
            "metricAlias": "入方向流量",
            "monitorTags": "",
            "resourceType": "eip",
            "resourceUuid": "2c0faf76ff8454ec9713d808e67e7ef0",
            "startTime": 1551200000,
            "values": [
                {
                    "timestamp": 1551200040,
                    "value": 34
                },
                {
                    "timestamp": 1551200100,
                    "value": 53.333333
                },
                {
                    "timestamp": 1551200160,
                    "value": 52.666667
                },
                {
                    "timestamp": 1551200220,
                    "value": 80
                },
                {
                    "timestamp": 1551200280,
                    "value": 56
                },
                {
                    "timestamp": 1551200340,
                    "value": 35.333333
                },
                {
                    "timestamp": 1551200400,
                    "value": 322.5
                },
                {
                    "timestamp": 1551200460,
                    "value": 211.333333
                },
                {
                    "timestamp": 1551200520,
                    "value": 54
                },
                {
                    "timestamp": 1551200580,
                    "value": 20
                },
                {
                    "timestamp": 1551200640,
                    "value": 13.333333
                },
                {
                    "timestamp": 1551200700,
                    "value": 6.666667
                },
                {
                    "timestamp": 1551200760,
                    "value": 60.666667
                },
                {
                    "timestamp": 1551200820,
                    "value": 12.666667
                },
                {
                    "timestamp": 1551200880,
                    "value": 26.666667
                },
                {
                    "timestamp": 1551200940,
                    "value": 46.166667
                },
                {
                    "timestamp": 1551201000,
                    "value": 53.333333
                }
            ]
        }
    ],
    "requestId": "0a8450315c777fcbee6e01a2e20988b0"
}
```
