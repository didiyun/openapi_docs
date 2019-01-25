## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/sg/assign`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| name | 是 | string  | SG名称   |
| vpcUuid | 否 | string | 此SG要创建的VPC的uuid，不传则创建在指定region的默认VPC下 |
| sgRule | 否 | array<[CreateSGRuleInput](#CreateSGRuleInput)> | 同时在此SG下创建的规则信息 |
| dc2 | 否 | array<[DC2InputForCreateSG](#DC2InputForCreateSG)> | 需要同时添加至此SG的DC2信息 | 

<span id="CreateSGRuleInput"></span>
CreateSGRuleInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| type     | 是 |   string  | SGRule的类型，"Ingress"表示入方向，"Egress"表示出方向    |
| protocol | 是 |  string    |   此SGRule支持的协议    |
| startPort | 是 | int | 此规则允许端口从startPort值开始，需要在0-65535之间 |
| endPort | 是 | int | 此SGRule的允许端口从endPort结束，当等于startPort时，表示SGRule只对startPort的端口开放，需要在0-65535之间 |
| allowedCidr | 是 |string |  此规则允许的网段地址，格式如"10.0.0.0/24" |

<span id="DC2InputForCreateSG"></span>
DC2InputForCreateSG：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| dc2Uuid   | 是 |   string  |   DC2的uuid    |

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
curl -X POST https://open.didiyunapi.com/dicloud/i/network/sg/create \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "regionId": "gz",
	"name": "test-sg",
	"vpcUuid": "e32a224660824af1ba84ca7eeebd93ff",
	"sgRule": [{
		"type": "Ingress",
		"protocol": "TCP",
		"startPort": 22,
		"endPort": 22,
		"allowedCidr": "0.0.0.0/0"
	}, {
		"type": "Egress",
		"protocol": "UDP",
		"startPort": 8000,
		"endPort": 9000,
		"allowedCidr": "10.0.0.0/16"
	}],
	"dc2": [{
		"dc2Uuid": "953777262c9e5bd48d1a5379ca220811"
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
		"type": "CreateSecurityGroup"
	}],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```