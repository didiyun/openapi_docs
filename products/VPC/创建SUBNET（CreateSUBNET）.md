## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/assign`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| vpcUuid | 是 | string  | 在此uuid对应的VPC下创建SUBNET   |
| subnet | 是 | array<[CreateSUBNETInput](#CreateSUBNETInput2)> | 需要创建的SUBNET信息 |

<span id="CreateSUBNETInput2"></span>
CreateSUBNETInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| name     | 是 |   string  |   SUBNET名称    |
| cidr | 是 |  string    |   SUBNET网段，格式如"10.0.0.0/24"    |
| zoneId | 是 | string | 需要在哪个可用区创建SUBNET |


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
curl -X POST https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/assign \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"vpcUuid": "e32a224660824af1ba84ca7eeebd93ff",
	"subnet": [{
		"name": "test-subnet",
		"cidr": "10.0.0.0/16",
		"zoneId": "gz01"
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
		"type": "CreateSubnet"
	}],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```