## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/ebs/assign`

请求方法：POST
## 输入参数
<span id="CreateEBSParams"></span>
CreateEBSParams:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 是 | string | 可用区id，在何可用区创建EBS实例 |
| autoContinue    | 否 |   bool    |   是否设置EBS自动续费          |
| payPeriod | 否 | int | 购买包月时长，单位为月，不传或传0表示后付费 |
| count | 否 | int | 批量购买参数，不传默认购买一台EBS，不能超过20 |
| couponId | 否 | string | 本次操作使用的优惠券id |
| name     | 否 |string   | 创建的EBS名称 |
| size     | 是 |int64    | 创建的EBS大小，单位GB，需大于等于20，并小于等于16384 |
| diskType | 是 |string   | 创建的EBS类型（"HE"或"SSD"）|
| dc2Uuid | 否 | string |  创建此EBS实例时同时将其绑定DC2的uuid |
| snapUuid | 否 |string   | 通过此快照创建EBS |
| ebsTags   | 否 |  array&lt;string&gt; | EBS标签 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>   | 请求返回数据| 


## 错误码
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/ebs/assign \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{	
	"regionId":"gz",
	"zoneId":"gz01",
	"size":30,
	"diskType":"SSD"
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "40719cee4b90536591660d651d56f533",
			"progress": 0,
			"success": false,
			"type": "CreateEBS"
		}
	],
	"requestId": "0a60538a5bc6a7657f9543f52f0fb1b0"
}
```
