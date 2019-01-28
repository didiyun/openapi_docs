## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/compute/dc2`

请求方法：GET
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id |
| dc2Uuid  | 是 | string   | 所查询DC2的Uuid   |


## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[DC2Response](#Dc2Response)>| 请求返回数据| 

<span id="Dc2Response"></span>
DC2Response：

|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此DC2正在进行的任务，若无任务则没有此字段 |
|dc2Uuid  | string  |DC2唯一标识   |
|name   | string  |DC2名称     |
|createTime     | int64  |DC2创建时间    |
|updateTime  | int64  |DC2更新时间       |
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
curl -X GET https://open.didiyunapi.com/dicloud/i/compute/dc2?dc2Uuid=b8bf159d2ce258f98b27aedafcaadc91 \
 -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b99e6ddd6b427b4d256969534a81d0773f4d7' \

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
