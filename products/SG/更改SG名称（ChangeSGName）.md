## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/sg/changeName`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| sg | 是 | array<[ChangeSGNameInput](#ChangeSGNameInput)> | 需要改名的SG信息 |

<span id="ChangeSGNameInput"></span>
ChangeSGNameInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| sgUuid     | 是 |   string  |  待改名的SG的uuid    |
| name     | 是 |   string  |  更改的名称    |


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
curl -X POST https://open.didiyunapi.com/dicloud/i/network/sg/changeName \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "regionId":"gz",
	"sg": [{
		"sgUuid": "3eb1f286b01f59d08228e4bbe319eb6f",
		"name": "test-sg"
	}]
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [{
		"done": false,
		"jobUuid": "3eb1f286b01f59d08228e4bbe319eb6f",
		"progress": 0,
		"success": false,
		"type": "ChangeSecurityGroupName"
	}],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```
