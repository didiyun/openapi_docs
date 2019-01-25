## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/sg/rule/assign`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| sgUuid | 是 | string  | 待创建的SGRule所属的SG的uuid   |
| sgRule | 是 | array<[CreateSGRuleInput](#CreateSGRuleInput2)> | 创建的SGRule信息 |

<span id="CreateSGRuleInput2"></span>
CreateSGRuleInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| type     | 是 |   string  | SGRule的类型，"Ingress"表示入方向，"Egress"表示出方向    |
| protocol | 是 |  string    |   此SGRule支持的协议，"TCP"、"UDP"或"ICMP"    |
| startPort | 是 | int | 此SGRule允许端口从startPort值开始，需要在0-65535之间 |
| endPort | 是 | int | 此SGRule的允许端口从endPort结束，当等于startPort时，表示SGRule只对startPort的端口开放，需要在0-65535之间 |
| allowedCidr | 是 |string |  此SGRule允许的网段地址，格式如"10.0.0.0/24"|


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
curl -X POST https://open.didiyunapi.com/dicloud/i/network/sg/rule/assign \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "regionId": "gz",
	"sgUuid": "ce62656b22165a7293e9d009bd72ce76",
	"sgRule": [{
		"type": "Ingress",
		"startPort": 80,
		"endPort": 80,
		"protocol": "TCP",
		"allowedCidr": "0.0.0.0/0"
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
		"type": "AddRuleToSecurityGroup"
	}],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```