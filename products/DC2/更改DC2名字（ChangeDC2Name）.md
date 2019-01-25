## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/compute/dc2/changeName`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id |
| dc2 | 是 | array<[ChangeDC2NameInput](#ChangeDC2NameInput)> | 要更改名称的DC2信息，一次不能超过20台 |

<span id="ChangeDC2NameInput"></span>
ChangeDC2NameInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| dc2Uuid     | 是 |   string  |   需要更改名称的DC2的uuid          |
| name | 是 | string | DC2的新名称 |

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
curl -X POST https://open.didiyunapi.com/dicloud/i/compute/dc2/changeName \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz"
	"dc2": [{
		"dc2Uuid": "c04325cc49495ea1bdc302c434a343fb",
		"name":"test"
	}]
}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "a206b86217605dbe902ba7f251fe0070",
			"progress": 0,
			"success": false,
			"type": "ChangeDC2Name"
		}
	],
	"requestId": "0a60538a5bc5d3a398860f25c0d9ebb0"
}
```