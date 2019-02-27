## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/sg/rule/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| start     | 是 | int      |查询SGRule列表起始index，从0开始   |
| limit     | 是 | int      |查询SGRule列表元素数量           |
| condition | 否 | [SGRuleCondition](#SGRuleCondition) | 查询SGRule条件 |

<span id="SGRuleCondition"></span>
SGRuleCondition:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| sgUuid | 否 | string | 查看此SG下的SGRule列表，**与dc2Uuid参数二选一** |
| dc2Uuid | 否 | string | 查看此DC2遵循的SGRule列表，**与sgUuid参数二选一** |
| type | 否 | string |  要查询的SGRule类型，"Ingress"为入方向，"Egress"为出方向 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[SGRuleResponse](#SGRuleResponse)>| 请求返回数据| 

<span id="SGRuleResponse"></span>
SGRuleResponse：

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此SGRule正在进行的任务，若无任务则没有此字段 |
|sgRuleUuid  | string  | SGRule唯一标识   |
| type     |   string  | SGRule的类型，"Ingress"表示入方向，"Egress"表示出方向    |
| protocol |  string    |   此SGRule支持的协议，"TCP"、"UDP"或"ICMP"    |
| startPort | int | 此规则允许端口从startPort值开始，在0-65535之间 |
| endPort | int | 此SGRule的允许端口从endPort结束，当等于startPort时，表示SGRule只对startPort的端口开放，在0-65535之间 |
|allowedCidr | string | SGRule允许的网段 |
|createTime   | int64  | SG创建时间  |
|updateTime      | int64  | SG更新时间       |
|isDefault  | bool  | 是否为SG下的默认SGRule    |
|sg | [SGOutput](#SGOutput) | 此SGRule所属的SG信息 |
|vpc | [VPCOutput](#VPCOutput2) | 此SGRule所属的VPC信息 |

<span id="SGOutput"></span>
SGOutput:

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|sgUuid  | string  | SG唯一标识   |
|name   | string  | SG名称     |
|createTime   | int64  |SG创建时间   |
|updateTime      | int64  | SG更新时间      |
|isDefault  | bool  | 此SG是否为其所属VPC下的默认SG   |

<span id="VPCOutput2"></span>
VPCOutput:

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|vpcUuid  | string  | VPC唯一标识   |
|name   | string  | VPC名称     |
|createTime   | int64  |VPC创建时间    |
|updateTime      | int64  |VPC更新时间       |
|isDefault  | bool  | VPC是否是当前region的默认VPC    |
|desc  | string  | VPC描述信息    |
|cidr   | string  | VPC的网段    |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |
|41053 | 查询安全组规则失败 |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/sg/rule/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
 -d '{
	"regionId": "gz",
	"start": 0,
	"limit": 10,
	"condition": {
		"sgUuid": "db1a4d0fa0e14d1a93c18fadf97b3065"
	}
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [{
		"allowedCidr": "0.0.0.0/0",
		"createTime": 1539767815000,
		"endPort": 65535,
		"isDefault": false,
		"protocol": "TCP",
		"sg": {
			"createTime": 1539767815000,
			"dc2Cnt": 0,
			"isDefault": true,
			"name": "sg-default-vpc",
			"sgId": "sg-9riujc66",
			"sgRuleCnt": 0,
			"sgTags": [],
			"sgUuid": "db1a4d0fa0e14d1a93c18fadf97b3065",
			"updateTime": 1539767815000
		},
		"sgRuleId": "sgr-ge7hzqmn",
		"sgRuleTags": [],
		"sgRuleUuid": "33a5c55e14e043669b2a1931eaae5f01",
		"startPort": 1,
		"type": "Egress",
		"updateTime": 1539767815000,
		"vpc": {
			"cidr": "10.0.0.0/8",
			"createTime": 1539767814000,
			"desc": "default l2 network",
			"isDefault": true,
			"name": "default-vpc",
			"updateTime": 1539767815000,
			"vpcId": "vpc-94hgk1oe",
			"vpcTags": [],
			"vpcUuid": "e32a224660824af1ba84ca7eeebd93ff"
		}
	}],
	"requestId": "0a60538a5bc6f9cf946d43f5b7f569b0"
}
```
