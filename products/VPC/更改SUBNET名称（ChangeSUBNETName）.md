## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/changeName`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| vpcUuid | 是 | string  | 删除此uuid对应的VPC下的SUBNET   |
| subnet | 是 | array<[ChangeSUBNETNameInput](#ChangeSUBNETNameInput)> | 需要改名的SUBNET信息 |

<span id="ChangeSUBNETNameInput"></span>
ChangeSUBNETNameInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| subnetUuid     | 是 |   string  |   SUBNET的uuid    |
| name | 是 | string | SUBNET的新名称 |


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
curl -X POST https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/changeName \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "regionId": "gz",
	"vpcUuid": "e32a224660824af1ba84ca7eeebd93ff",
	"subnet": [{
		"subnetUuid": "3bd0dce4e3e654539dea7ec5461b8fcd"
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
		"type": "ChangeSubnetName"
	}],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```