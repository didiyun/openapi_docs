## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 查询此zone下的SUBNET |
|start     | 是 | int      |查询SUBNET列表起始index，从0开始   |
|limit     | 是 | int      |查询SUBNET列表元素数量           |
|condition | 否 | [SUBNETCondition](#SUBNETCondition) | 查询SUBNET条件 |

<span id="SUBNETCondition"></span>
SUBNETCondition:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| vpcUuid | 否  | string | 查询此VPC下的SUBNET |


## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[SUBNETResponse](#SUBNETResponse)>| 请求返回数据| 

<span id="SUBNETResponse"></span>
SUBNETResponse：

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此SUBNET正在进行的任务，若无任务则没有此字段 |
|subnetUuid  | string  |SUBNET唯一标识   |
|name   | string  |SUBNET名称     |
|createTime   | int64  |SUBNET创建时间    |
|updateTime      | int64  |SUBNET更新时间       |
|isDefault  | bool  | SUBNET是否是zone下的默认SUBNET    |
|cidr   | string  | SUBNET的网段    |
|zone |[Zone](/static/docs-content/products/通用响应结构.md#Zone#Zone) | SUBNET所在的Zone信息 |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |
|41126 | 查询SUBNET信息失败 |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId": "gz",
	"start": 0,
	"limit": 10,
	"condition": {
		"vpcUuid": "ad9042b8f67f448ba640144f31636209"
	}
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [ 
		{
			"cidr": "10.255.1.0/24",
			"createTime": 1539573724000,
			"isDefault": true,
			"name": "default-subnet-for-GZ02",
			"subnetId": "subnet-d4a6fd5n",
			"subnetTags": [],
			"subnetUuid": "ab7b2816b0b64f59b8574f0501e3949a",
			"totalIpCnt": 249,
			"updateTime": 1539573724000,
			"usedIpCnt": 0,
			"zone": {
				"id": "gz02",
				"name": "广州二区"
			}
		},
		{
			"cidr": "10.255.0.0/24",
			"createTime": 1539573724000,
			"isDefault": true,
			"name": "default-subnet-for-GZ01",
			"subnetId": "subnet-mysmm873",
			"subnetTags": [],
			"subnetUuid": "f2513581ccd048dc9d0ccec32114b7cd",
			"totalIpCnt": 249,
			"updateTime": 1539573724000,
			"usedIpCnt": 5,
			"zone": {
				"id": "gz01",
				"name": "广州一区"
			}
		}
	],
	"requestId": "0a60538a5bc6fe05f73443f5d6f057b0"
}
```