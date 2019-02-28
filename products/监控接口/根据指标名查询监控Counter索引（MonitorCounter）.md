## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/m/api/counter`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| resource | 是 | array<[ResourceInput](#ResourceInput) | 要查询counter的资源列表 |


<span id="ResourceInput"></span>
ResourceInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| resourceType | 是 | string | 要查询counter的资源类型 |
| resourceUuids | 是 | array&lt;string&gt; | 要查询counter的资源uuid集合 |
| metric | 是 | array&lt;string&gt; | 要查询的指标名称（[指标名类型](#MetricEnum)） |

<span id="MetricEnum"></span>
指标名类型：
| 资源类型 | 支持的metric | metric中文名 | 单位 | 说明 |
| ------| ----- | ----- | ----- | ----- |
| dc2 | cpu.util   | cpu使用率      |  % | - |
| dc2 | disk.read  | 磁盘读	       | MB/s | DC2上挂载所有磁盘的读数据 | 
| dc2 | disk.write | 磁盘写         | MB/s | DC2上挂载所有磁盘的写数据 |
| dc2 | net.in     | 网卡接收流量    | MB/s | DC2的内网流量  |
| dc2 | net.out    | 网卡发送流量	    | MB/s | DC2的内网流量 |
| eip | rxbytes    | 入方向流量      | Bytes/10s | -  |
| eip | rxpkts     | 入方向包数	    | 个/10s | - |
| eip | txbytes     | 出方向流量	    | Bytes/10s | - |
| eip | txpkts     | 出方向包数	    | 	个/10s | - |



## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[CounterOutput](#CounterOutput)>   | 请求返回数据|

<span id="CounterOutput"></span>
CounterOutput：

|参数名称 | 类型 | 描述|
|--------|-----|-----|
| resourceType     |   string  |   资源类型     |
| resourceUuid     |   string  |   资源uuid     |
| alias     |   string  |   别名     |
| metric     |  string  |   监控指标名     |
| metricAlias     |   string  |   监控指标别名     |
| counters | array<[Counter](#Counter)> | 包含的指标曲线 |

<span id="Counter"></span>
Counter：

|参数名称 | 类型 | 描述|
|--------|-----|-----|
| monitorTags     |   string  |   资源包含的曲线tags     |
| step  |   int |  监控指标上报周期，单位为秒 | 
| dstype | string |  [数据源的统计类型](#DstypeEnum) | 

<span id="DstypeEnum"></span>
数据源的统计类型：

|dstype | 描述 |
| ----- | ----- |
| GAUGE |   实测值，存储的是实际值   |
| COUNTER  |  计数值，存储的是数值的变化率 |  


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |


## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/m/api/counter \
  -H 'Authorization: Bearer 9a23d72c1f9d5b39a2d96c474b3d308f5f3d8a5a5b865a7ea3618366cebcc0fc' \
  -H 'Content-Type: application/json;charset=UTF-8' \
  -d '{
    "regionId": "gz",
    "resource":[{
    	"resourceType":"eip",
    	"resourceUuids":["2c0faf76ff8454ec9713d808e67e7ef0"],
    	"metric":["rxbytes","txbytes"]
    }]
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": [
        {
            "alias": "116.85.255.139",
            "counters": [
                {
                    "monitorTags": "",
                    "step": 10
                }
            ],
            "metric": "rxbytes",
            "metricAlias": "入方向流量",
            "resourceType": "eip",
            "resourceUuid": "2c0faf76ff8454ec9713d808e67e7ef0"
        },
        {
            "alias": "116.85.255.139",
            "counters": [
                {
                    "monitorTags": "",
                    "step": 10
                }
            ],
            "metric": "txbytes",
            "metricAlias": "出方向流量",
            "resourceType": "eip",
            "resourceUuid": "2c0faf76ff8454ec9713d808e67e7ef0"
        }
    ],
    "requestId": "0a8450315c776fb8d44901a4efb0f3b0"
}
```
