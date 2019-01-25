## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/snapshot/revert`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|regionId | 是 | string | 地域id |
|snap     | 是 | array<[RevertSnapInput](#RevertSnapInput)>   |SNAP描述信息|
|stopDc2 | 否 | bool | 还原前，是否执行关闭DC2(若DC2已处于关闭状态，则不需要传此参数） |
|startDc2 | 否 | bool |还原后是否需要同时启动DC2 |

<span id="RevertSnapInput"></span>
RevertSnapInput:

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
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/snapshot/revert \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"snap":[{
		"snapUuid":"3117ad495d8e5d96b78f82a50007ff9b"
	}]
	"stopDc2":true,
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
			"type": "RevertSnapshot"
		}
	],
	"requestId": "0a60538a5b6561f1623274313932acb0"
}
```