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
| metric     |  string  |   监控指标名（[指标名类型](/static/docs-content/products/监控接口/根据指标名查询监控Counter索引（MonitorCounter）.md#MetricEnum)）     |
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
  https://open.didiyunapi.com/dicloud/m/api/data \
  -H 'Authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'Content-Type: application/json;charset=UTF-8' \
  -d '{
      	"regionId" : "gz",
      	"counter":[{
      		"resourceType":"dc2",
      		"resourceUuid":"2706bbf0b09d58ef9f3989e03dc3e075",
      		"monitorTags":"device=vda",
      		"metric":"disk.write",
      		"startTime":1551418588,
      		"endTime":1551422188
      	},{
      		"resourceType":"dc2",
      		"resourceUuid":"2706bbf0b09d58ef9f3989e03dc3e075",
      		"monitorTags":"",
      		"metric":"cpu.util",
      		"startTime":1551418588,
      		"endTime":1551422188
      	}]
      }'
      
输出：
{
    "data": [
        {
            "endTime": 1551422188,
            "metric": "disk.write",
            "metricAlias": "磁盘写",
            "monitorTags": "device=vda",
            "resourceType": "dc2",
            "resourceUuid": "2706bbf0b09d58ef9f3989e03dc3e075",
            "startTime": 1551418588,
            "values": [
                {
                    "timestamp": 1551418620,
                    "value": 0.000211
                },
                {
                    "timestamp": 1551418680,
                    "value": 0.00021
                },
                {
                    "timestamp": 1551418740,
                    "value": 0
                },
                {
                    "timestamp": 1551418800,
                    "value": 0.000243
                },
                {
                    "timestamp": 1551418860,
                    "value": 0.000205
                },
                {
                    "timestamp": 1551418920,
                    "value": 0
                },
                {
                    "timestamp": 1551418980,
                    "value": 0
                },
                {
                    "timestamp": 1551419040,
                    "value": 0.000209
                },
                {
                    "timestamp": 1551419100,
                    "value": 0.000219
                },
                {
                    "timestamp": 1551419160,
                    "value": 0.0002
                },
                {
                    "timestamp": 1551419220,
                    "value": 0
                },
                {
                    "timestamp": 1551419280,
                    "value": 0.000216
                },
                {
                    "timestamp": 1551419340,
                    "value": 0.000209
                },
                {
                    "timestamp": 1551419400,
                    "value": 0
                },
                {
                    "timestamp": 1551419460,
                    "value": 0.000185
                },
                {
                    "timestamp": 1551419520,
                    "value": 0.000209
                },
                {
                    "timestamp": 1551419580,
                    "value": 0.000214
                },
                {
                    "timestamp": 1551419640,
                    "value": 0.000205
                },
                {
                    "timestamp": 1551419700,
                    "value": 0
                },
                {
                    "timestamp": 1551419760,
                    "value": 0.000201
                },
                {
                    "timestamp": 1551419820,
                    "value": 0.000206
                },
                {
                    "timestamp": 1551419880,
                    "value": 0.000198
                },
                {
                    "timestamp": 1551419940,
                    "value": 0.000094
                },
                {
                    "timestamp": 1551420000,
                    "value": 0.00024
                },
                {
                    "timestamp": 1551420060,
                    "value": 0.000209
                },
                {
                    "timestamp": 1551420120,
                    "value": 0.000209
                },
                {
                    "timestamp": 1551420180,
                    "value": 0.000209
                },
                {
                    "timestamp": 1551420240,
                    "value": 0.000101
                },
                {
                    "timestamp": 1551420300,
                    "value": 0.000113
                },
                {
                    "timestamp": 1551420360,
                    "value": 0
                },
                {
                    "timestamp": 1551420420,
                    "value": 0.000145
                },
                {
                    "timestamp": 1551420480,
                    "value": 0.000154
                },
                {
                    "timestamp": 1551420540,
                    "value": 0.000163
                },
                {
                    "timestamp": 1551420600,
                    "value": 0.000169
                },
                {
                    "timestamp": 1551420660,
                    "value": 0.00015
                },
                {
                    "timestamp": 1551420720,
                    "value": 0.000106
                },
                {
                    "timestamp": 1551420780,
                    "value": 0.00015
                },
                {
                    "timestamp": 1551420840,
                    "value": 0.000108
                },
                {
                    "timestamp": 1551420900,
                    "value": 0.000215
                },
                {
                    "timestamp": 1551420960,
                    "value": 0.00015
                },
                {
                    "timestamp": 1551421020,
                    "value": 0.00015
                },
                {
                    "timestamp": 1551421080,
                    "value": 0.000146
                },
                {
                    "timestamp": 1551421140,
                    "value": 0.00013
                },
                {
                    "timestamp": 1551421200,
                    "value": 0.00016
                },
                {
                    "timestamp": 1551421260,
                    "value": 0.000164
                },
                {
                    "timestamp": 1551421320,
                    "value": 0.000106
                },
                {
                    "timestamp": 1551421380,
                    "value": 0.00015
                },
                {
                    "timestamp": 1551421440,
                    "value": 0.00012
                },
                {
                    "timestamp": 1551421500,
                    "value": 0.000155
                },
                {
                    "timestamp": 1551421560,
                    "value": 0.000155
                },
                {
                    "timestamp": 1551421620,
                    "value": 0.000115
                },
                {
                    "timestamp": 1551421680,
                    "value": 0.000106
                },
                {
                    "timestamp": 1551421740,
                    "value": 0.000116
                },
                {
                    "timestamp": 1551421800,
                    "value": 0.000129
                },
                {
                    "timestamp": 1551421860,
                    "value": 0.000106
                },
                {
                    "timestamp": 1551421920,
                    "value": 0.000115
                },
                {
                    "timestamp": 1551421980,
                    "value": 0.000106
                },
                {
                    "timestamp": 1551422040,
                    "value": 0
                },
                {
                    "timestamp": 1551422100,
                    "value": 0.000119
                },
                {
                    "timestamp": 1551422160,
                    "value": 0.000146
                }
            ]
        },
        {
            "endTime": 1551422188,
            "metric": "cpu.util",
            "metricAlias": "cpu使用率",
            "monitorTags": "",
            "resourceType": "dc2",
            "resourceUuid": "2706bbf0b09d58ef9f3989e03dc3e075",
            "startTime": 1551418588,
            "values": [
                {
                    "timestamp": 1551418620,
                    "value": 0.5
                },
                {
                    "timestamp": 1551418680,
                    "value": 0.466667
                },
                {
                    "timestamp": 1551418740,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551418800,
                    "value": 0.633333
                },
                {
                    "timestamp": 1551418860,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551418920,
                    "value": 0.666667
                },
                {
                    "timestamp": 1551418980,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551419040,
                    "value": 0.633333
                },
                {
                    "timestamp": 1551419100,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551419160,
                    "value": 0.633333
                },
                {
                    "timestamp": 1551419220,
                    "value": 0.7
                },
                {
                    "timestamp": 1551419280,
                    "value": 0.666667
                },
                {
                    "timestamp": 1551419340,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551419400,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551419460,
                    "value": 0.7
                },
                {
                    "timestamp": 1551419520,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551419580,
                    "value": 0.7
                },
                {
                    "timestamp": 1551419640,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551419700,
                    "value": 0.8
                },
                {
                    "timestamp": 1551419760,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551419820,
                    "value": 0.666667
                },
                {
                    "timestamp": 1551419880,
                    "value": 0.5
                },
                {
                    "timestamp": 1551419940,
                    "value": 0.533333
                },
                {
                    "timestamp": 1551420000,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551420060,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551420120,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551420180,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551420240,
                    "value": 0.533333
                },
                {
                    "timestamp": 1551420300,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551420360,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551420420,
                    "value": 0.8
                },
                {
                    "timestamp": 1551420480,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551420540,
                    "value": 0.533333
                },
                {
                    "timestamp": 1551420600,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551420660,
                    "value": 0.666667
                },
                {
                    "timestamp": 1551420720,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551420780,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551420840,
                    "value": 0.533333
                },
                {
                    "timestamp": 1551420900,
                    "value": 0.7
                },
                {
                    "timestamp": 1551420960,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551421020,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551421080,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551421140,
                    "value": 0.7
                },
                {
                    "timestamp": 1551421200,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551421260,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551421320,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551421380,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551421440,
                    "value": 0.533333
                },
                {
                    "timestamp": 1551421500,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551421560,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551421620,
                    "value": 0.533333
                },
                {
                    "timestamp": 1551421680,
                    "value": 0.5
                },
                {
                    "timestamp": 1551421740,
                    "value": 0.533333
                },
                {
                    "timestamp": 1551421800,
                    "value": 0.766667
                },
                {
                    "timestamp": 1551421860,
                    "value": 0.5
                },
                {
                    "timestamp": 1551421920,
                    "value": 0.5
                },
                {
                    "timestamp": 1551421980,
                    "value": 0.466667
                },
                {
                    "timestamp": 1551422040,
                    "value": 0.5
                },
                {
                    "timestamp": 1551422100,
                    "value": 0.733333
                },
                {
                    "timestamp": 1551422160,
                    "value": 0.733333
                }
            ]
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59922a5c78d367a61a0f3b03088a02"
}
```
