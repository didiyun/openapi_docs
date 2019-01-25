## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/snapshot/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 查询可用区id |
| start     | 是 | int      |查询SNAP列表起始index，从0开始 |
| limit     | 是 | int      |查询SNAP元素数量         |
| simplify  | 否 | bool     |是否简化输出       |
| condition | 否 | [SNAPCondition](#SNAPCondition) | 查询SNAP条件 |

<span id="SNAPCondition"></span>
SNAPCondition: 

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| dc2Uuid | 否 | string | 查询此uuid的DC2的根盘及数据盘快照 |
| ebsUuid | 否  | string | 查询此uuid的EBS的快照 |
| snapName | 否 | string | 查询快照的名称，模糊匹配 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[SNAPResponse](#SNAPResponse)>| 请求返回数据| 

<span id="SNAPResponse"></span>
SNAPResponse：

|参数名称  | 类型 | 描述|
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此EIP正在进行的任务，若无任务则没有此字段 |
|snapUuid  | string  |SNAP唯一标识   |
|name | string | SNAP名称 |
|canBeReverted	   | bool  | 是否可回滚  |
|isGeneral    | bool  |是否是通用系列（e1,g1,g2）DC2快照(通用系列DC2快照目前只支持用于创建通用系列DC2) |
|createTime | int64 | SNAP创建时间 |
|updateTime     | int64  | SNAP 更新时间  |
|size     | int64  | SNAP大小       |
|volumeSize | int64 | SNAP源盘大小 |
| type | string | SNAP类型，为"Root"为系统盘快照，为"Data"为数据盘快照，只有系统盘快照可以用于创建新的DC2 |
| dc2	  | [DC2](#Dc24)   | 与SNAP关联的DC2信息，没有DC2则没有该字段 |
| ebs | [EBS](#EBS2) | 与SNAP关联的EBS信息，没有EBS则没有该字段 | 
| region | [Region](/static/docs-content/products/通用响应结构.md#Region) | region与zone的信息 |

<span id="Dc24"></span>
DC2:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
|dc2Uuid  | string  |DC2唯一标识   |
|name   | string  |DC2名称     |

<span id="EBS2"></span>
EBS:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
|ebsUuid  | string  |EBS唯一标识   |
|name   | string  |EBS名称     |
|type     | string  |EBS类型，"HDD"、"HE"或"SSD"   |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |
|41017 | 查询SNAP信息失败 |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/snapshot/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{	
	"regionId":"gz",
	"start":0,
	"limit":10,
	"condition":{"snapName":"test"}
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"attr": "User",
			"canBeReverted": true,
			"createTime": 1539761242000,
			"dc2": {
				"dc2Uuid": "b8bf159d2ce258f98b27aedafcaadc91",
				"name": "1CPU-1GMEM-20GDISK"
			},
			"imgScenes": [
				"base"
			],
			"imgUuid": "c246f4034faa4313bc4c5709e81e4497",
			"isGeneral": false,
			"name": "test",
			"region": {
				"id": "gz",
				"name": "广州",
				"zone": {
					"id": "gz01",
					"name": "广州一区"
				}
			},
			"size": 2253979648,
			"snapUuid": "5e424b25acec5a819cedd56e813416ae",
			"type": "Root",
			"updateTime": 1539761268000,
			"volumeSize": 21474836480
		}
	],
	"requestId": "0a60538a5bc6e4eb2d3f43f5810447b0"
}
```