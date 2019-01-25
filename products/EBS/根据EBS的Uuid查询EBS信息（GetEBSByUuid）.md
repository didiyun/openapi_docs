## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/ebs`

请求方法：GET
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| ebsUuid     | 是 | string  |EBS的Uuid  |

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
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X GET 'https://open.didiyunapi.com/dicloud/i/storage/ebs?ebsUuid=83f3dbfd91b25154a5aa422f39298a83&regionId=gz' \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' 
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
	"requestId": "0a60538a5bc6036bd9170f2588ff7bb0"
}
```