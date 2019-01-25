## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/snapshot/delete`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
|snap     | 是 | array<[DeleteSnapInput](#DeleteSnapInput)>   |SNAP描述信息  |

<span id="DeleteSnapInput"></span>
DeleteSnapInput:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|snapUuid  | 是 |string   |SNAP唯一标识 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>	 | 请求返回数据| 

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/snapshot/delete \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"snap":[{
		"snapUuid":"3117ad495d8e5d96b78f82a50007ff9b"
	}]
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "1efb7af82b225e608a86602166ba4318",
			"progress": 0,
			"success": false,
			"type": "DeleteSnapshot"
		}
	],
	"requestId": "0a60538a5b6561f1623274313932acb0"
}
```