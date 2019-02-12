## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/vpc/delete`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| vpc | 是 | array<[DeleteVPCInput](#DeleteVPCInput)> | 需要删除的VPC信息 |

<span id="DeleteVPCInput"></span>
DeleteVPCInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| vpcUuid     | 是 |   string  |  待删除的VPC的uuid    |


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
curl -X POST https://open.didiyunapi.com/dicloud/i/network/vpc/delete \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "regionId":"gz",
	"vpc": [{
		"vpcUuid": "3eb1f286b01f59d08228e4bbe319eb6f"
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
		"type": "DeleteVPC"
	}],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```
