## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/compute/dc2/start`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id |
| dc2 | 是 | array<[StartDC2Input](#StartDC2Input)> | 要启动的DC2信息，一次不能超过20台 |

<span id="StartDC2Input"></span>
StartDC2Input：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|dc2Uuid     | 是 |   string  |   需要启动的DC2的uuid          |

## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>   | 请求返回数据| 

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/compute/dc2/start \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"dc2": [{
		"dc2Uuid": "c04325cc49495ea1bdc302c434a343fb",
	}]
}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "b78fffe504135fb2b040b8af57c57bb1",
			"progress": 0,
			"success": false,
			"type": "StartDC2"
		}
	],
	"requestId": "0a60538a5bc5b82852200f252d882fb0"
}
```
