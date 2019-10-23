## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/ebs/changeSize`

请求方法：POST

## 输入参数
<span id="ChangeEBSSizeParams"></span>
ChangeEBSSizeParams:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| couponId | 否 | string | 本次操作使用的优惠券id |
| ebs | 是 | array<[ChangeEBSSizeInput](#ChangeEBSSizeInput)> | 要更改大小的EBS信息，一次不能超过20个 |

<span id="ChangeEBSSizeInput"></span>
ChangeEBSSizeInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|ebsUuid     | 是 |   string  |   需要更改大小的EBS的uuid          |
| size     | 是 |int64    | 需要更改的EBS大小，只能比原EBS大，单位GB，需大于等于20，并小于等于16384 |

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
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/ebs/changeSize \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{	
	"regionId":"gz",
	"ebs":[{
		"size":40,
		"ebsUuid":"fca0b70a01bd53189c2b274b65cff30c"
	}]
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
			"type": "ChangeEBSSize"
		}
	],
	"requestId": "0a60538a5bc6a7657f9543f52f0fb1b0"
}
```
