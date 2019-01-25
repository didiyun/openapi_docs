## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/ebs/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id，希望查询的可用区，不传则表示查询此地域下的所有可用区 |
| start     | 是 | int      |查询EBS列表起始index，从0开始 |
| limit     | 是 | int      |查询EBS列表元素数量         |
| condition | 否 | [EBSCondition](#EBSCondition) | 查询EBS条件 |

<span id="EBSCondition"></span>
EBSCondition:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| dc2Uuids | 否  | array&lt;string&gt; | 查询此dc2Uuid集合绑定的EBS实例 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[EBSResponse](#EbsResponse)>| 请求返回数据| 

<span id="EbsResponse"></span>
EBSResponse：

|参数名称  | 类型 | 描述|
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此EBS正在进行的任务，若无任务则没有此字段 |
|ebsUuid  | string  |EBS唯一标识   |
|name	   | string  |EIP IP地址   |
|attr | string | EBS属性（"Root"为根盘，"Data"为数据盘） |
|createTime     | int64  |EBS创建时间  |
|updateTime      | int64  |EBS更新时间       |
|ebsTags  | array&lt;string&gt;    |EBS的tags     |
|dc2	  | [DC2](#Dc23)   | 与EBS绑定的DC2信息，未绑定则没有该字段 |

<span id="Dc23"></span>
Dc2:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| dc2Uuid  | string  |DC2唯一标识   |
| name   | string  |DC2名称     |
| createTime     | int64  |DC2创建时间    |
| updateTime      | int64  |DC2更新时间       |
| status   | string  |DC2状态     |
| osType  | string  |DC2操作系统发行版及版本号   |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |
|41094 | 查询EBS信息失败 |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/ebs/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
		"regionId":"gz",
		"start":0,
		"limit":10,
		"condition":{}
	}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"attr": "Data",
			"createTime": 1539676804000,
			"deviceName": "vdb",
			"ebsId": "ebs-x4o03bh9",
			"ebsTags": [],
			"ebsUuid": "83f3dbfd91b25154a5aa422f39298a83",
			"name": "DATA-for-1CPU-1GMEM-20GDISK",
			"region": {
				"id": "gz",
				"name": "广州",
				"zone": {
					"id": "gz01",
					"name": "广州一区"
				}
			},
			"size": 21474836480,
			"updateTime": 1539680464000
		}
	],
	"requestId": "0a60538a5bc5e92e0cff0f25551400b0"
}
```