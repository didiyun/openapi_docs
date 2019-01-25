## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/snapshot/assign`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| dc2Uuid | 是 | string  | 根据DC2创建快照，与ebsUuid参数二选一   |
| ebsUuid | 是 | string  | 根据EBS创建快照，与dc2Uuid参数二选一   |
| snapName | 是 | string | 快照名称 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>	 | 请求返回数据 | 


## 错误码
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/snapshot/assign \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{	
	"regionId":"gz",
	"dc2Uuid":"b8bf159d2ce258f98b27aedafcaadc91",
	"snapName":"test"
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "d385ea9a10b85ed7b3bd1acedab746ed",
			"progress": 0,
			"success": false,
			"type": "CreateSnapshot"
		}
	],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```