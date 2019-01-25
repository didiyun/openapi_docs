## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/compute/dc2/changeSpec`

请求方法：POST
## 输入参数
<span id="ChangeDC2SpecParams"></span>
ChangeDC2SpecParams:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id |
| couponId | 否 | string | 本次操作使用的优惠券id |
| dc2 | 是 | array<[ChangeDC2SpecInput](#ChangeDC2SpecInput)> | 要更改规格的DC2信息，一次不能超过20台 |

<span id="ChangeDC2SpecInput"></span>
ChangeDC2SpecInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|dc2Uuid     | 是 |   string  |   需要更改规格的DC2的uuid          |
|dc2Model| 是 |   string         |   需要更改的型号，只能升配      |

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
curl -X POST https://open.didiyunapi.com/dicloud/i/compute/dc2/changeSpec \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"dc2": [{
		"dc2Uuid": "c04325cc49495ea1bdc302c434a343fb",
		"dc2Model": "dc2.s1.large4.d20"
	}]
}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "2c9a98cc9f9b524fbc32ca0613156426",
			"progress": 0,
			"success": false,
			"type": "ChangeDC2Offering"
		}
	],
	"requestId": "0a60538a5bc5a6cab0d30f2517939eb0"
}
```