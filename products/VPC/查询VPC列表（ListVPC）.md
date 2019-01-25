## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/vpc/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|regionId | 是 | string | 地域id |
|start     | 是 | int      |查询VPC列表起始index，从0开始   |
|limit     | 是 | int      |查询VPC列表元素数量           |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[VPCResponse](#VPCResponse)>| 请求返回数据| 

<span id="VPCResponse"></span>
VPCResponse：

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此VPC正在进行的任务，若无任务则没有此字段 |
|vpcUuid  | string  |VPC唯一标识   |
|name   | string  |VPC名称     |
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
|41121 | 查询VPC信息失败 |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/vpc/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{	
	"regionId":"gz",
	"start":0,
	"limit":10
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"cidr": "10.0.0.0/8",
			"createTime": 1539573721000,
			"desc": "default l2 network",
			"isDefault": true,
			"name": "default-vpc",
			"region": {
				"id": "gz",
				"name": "广州"
			},
			"updateTime": 1539573723000,
			"vpcId": "vpc-vr8s5e7q",
			"vpcTags": [],
			"vpcUuid": "ad9042b8f67f448ba640144f31636209"
		}
	],
	"requestId": "0a60538a5bc6f9cf946d43f5b7f569b0"
}
```