## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/sg/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| start     | 是 | int      |查询SG列表起始index，从0开始   |
| limit     | 是 | int      |查询SG列表元素数量           |
| condition | 否 | [SGCondition](#SGCondition) | 查询SG条件 |

<span id="SGCondition"></span>
SGCondition:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|sgUuids | 否  | array&lt;string&gt; | 查询此uuid集合的SG |
|vpcUuid | 否 | string | 查询此uuid对应的VPC下的SG |
|dc2Uuid | 否 | string | 查询此uuid对应的DC2相关的SG |
|dc2Exclude | 否 | bool | 与dc2Uuid配合使用，不传或传false，表示查询此DC2所绑定的SG列表，传true表示查询此DC2未绑定的SG列表 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[SGResponse](#SGResponse)>| 请求返回数据| 

<span id="SGResponse"></span>
SGResponse：

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此SG正在进行的任务，若无任务则没有此字段 |
|sgUuid  | string  | SG唯一标识   |
|name   | string  | SG名称     |
|createTime   | int64  | SG创建时间  |
|updateTime      | int64  | SG更新时间       |
|isDefault  | bool  | 是否为当前VPC下的默认SG    |
|dc2Cnt   | int  | SG绑定的DC2数量   |
|sgRuleCnt| int |  SG中的规则数量 |
|region |[Region](/static/docs-content/products/通用响应结构.md#Region) | region信息 |
|vpc | [VPCOutput](#VPCOutput) | 此SG所在的VPC信息 |

<span id="VPCOutput"></span>
VPCOutput:

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|vpcUuid  | string  | VPC唯一标识   |
|name   | string  | VPC名称     |
|createTime   | int64  |VPC创建时间    |
|updateTime      | int64  |VPC更新时间       |
|isDefault  | bool  | VPC是否是当前region的默认VPC    |
|desc  | string  |VPC描述信息    |
|cidr   | string  | VPC的网段    |
|region |[Region](/static/docs-content/products/通用响应结构.md#Region) | region信息 |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |
|41052 | 查询SG信息失败 |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/sg/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "regionId": "gz",
	"start": 0,
	"limit": 10,
	"condition": {}
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [{
		"category": "DEFAULT",
		"createTime": 1539767815000,
		"dc2Cnt": 1,
		"isDefault": true,
		"name": "sg-default-vpc",
		"region": {
			"id": "gz",
			"name": "广州"
		},
		"sgId": "sg-9riujc66",
		"sgRuleCnt": 10,
		"sgTags": [],
		"sgUuid": "db1a4d0fa0e14d1a93c18fadf97b3065",
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