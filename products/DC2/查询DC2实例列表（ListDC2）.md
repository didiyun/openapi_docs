## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/compute/dc2/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id，希望查询的可用区，不传则表示查询此地域下的所有可用区 |
|start     | 是 | int      |查询DC2列表起始index，从0开始   |
|limit     | 是 | int      |查询DC2列表元素数量     |
|simplify  | 否 | bool     |是否简化输出    |
|condition | 否 | [DC2Condition](#DC2Condition)|查询DC2列表筛选条件   |

<span id="DC2Condition"></span>
DC2Condition:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|vpcUuids     | 否 |   array&lt;string&gt;  |   查询多个VPC下的DC2列表   |
|vpcUuid      | 否 |   string         |   查询指定VPC下的DC2列表          |
|dc2Name      | 否 |   string         |   模糊查询DC2名字          |
|sgUuid       | 否 |   string         |   查询此sg下的dc2列表          |
|dc2Uuids     | 否 |   string         |   查询包含在此Uuid列表内的dc2   |
|sgExclude    | 否 |   bool           |   为true时表示查询不在此sg下的dc2列表   |
|ip           | 否 |   string         |   精确匹配内网IP   |
|eip          | 否 |   string         |   精确匹配公网EIP   |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[DC2Response](#Dc2Response)>| 请求返回数据| 

<span id="Dc2Response"></span>
DC2Response：（未指定simplify：简化输出时，不输出此字段）

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此DC2正在进行的任务，若无任务则没有此字段 |
|dc2Uuid（simplify）  | string  |DC2唯一标识   |
|name（simplify）   | string  |DC2名称     |
|createTime（simplify）     | int64  |DC2创建时间    |
|updateTime（simplify）      | int64  |DC2更新时间       |
|ip  | string  |DC2内网IP    |
|dc2Tags  | array&lt;string&gt;    |DC2的tags     |
|status   | string  | DC2状态    |
|osType  | string  |DC2操作系统发行版及版本号   |
|eip    | [EIP](#EIP)   | 与DC2关联的EIP信息，没有EIP则没有该字段 |
|ebs    |array<[EBS](#EBS)>   |与DC2关联的EBS信息，没有EBS则没有该字段，如果是通用型DC2，则必有这个字段，且根盘信息包含在内| 
|region |[Region](/static/docs-content/products/通用响应结构.md#Region) | region信息 |

<span id="EIP"></span>
EIP:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| eipUuid | string  |  EIP唯一标识     |
| ip     | string  |  EIP（DC2公网IP）        |
| createTime | int64  |  EIP创建时间     |
| updateTime   | int64  |  EIP更新时间       |

<span id="EBS"></span>
EBS:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| name | string  |  EBS名称 |
| ebsUuid | string  |  EBS唯一标识 |
| attr | string  |  EBS属性（"Root"为根盘，"Data"为数据盘）  |
| createTime | int64  |  EBS更新时间 |
| updateTime   | int64  | EBS更新时间       |
| region |[Region](/static/docs-content/products/通用响应结构.md#Region) | region信息 |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |
|41108 | 查询DC2信息失败 |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/compute/dc2/list \
 -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b99e6ddd6b427b4d256969534a81d0773f4d7' \
 -H 'content-type: application/json' \
 -d '{"start":0,"limit":10,"simplify":false,"regionId":"gz"}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [{
		"createTime": 1539592637000,
		"dc2Id": "dc2-vu22cv4l",
		"dc2Tags": ["test"],
		"dc2Uuid": "b8bf159d2ce258f98b27aedafcaadc91",
		"deviceName": "vda",
		"imgUuid": "46b447a8b0a146779bbde3ca40e56843",
		"ip": "10.255.0.93",
		"name": "1CPU-1GMEM-20GDISK",
		"osType": "CentOS 7.4",
		"platform": "Linux",
		"region": {
			"id": "gz",
			"name": "广州",
			"zone": {
				"id": "gz01",
				"name": "广州一区"
			}
		},
		"status": "Running",
		"updateTime": 1539596333000,
		"uuid": "b8bf159d2ce258f98b27aedafcaadc91"
	}],
	"requestId": "0ab753bcb7d3843214ef056f0f0c6c09"
}
```
