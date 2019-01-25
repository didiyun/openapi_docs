## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/region/list`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| condition   | 是 | [ListRegionAndZoneCondition](#ListRegionAndZoneCondition)  | 查询某产品的筛选条件  |

<span id="ListRegionAndZoneCondition"></span>
ListRegionAndZoneCondition:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| product | string  |  需要查询的产品名称 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[RegionResponse](#RegionResponse)>	 | 请求返回数据 | 

<span id="RegionResponse"></span>
RegionResponse:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| areaName | string  |  区域名称 |
| id       | string  |  region id |
| name     | string   |  regin name |
| zone     | array<[Zone](/static/docs-content/products/通用响应结构.md#Zone)> | 此region下所有zone信息 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/region/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{"condition":{"product":"dc2"}}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"areaName": "华南地区",
			"id": "gz",
			"name": "广州",
			"zone": [
				{
					"id": "gz01",
					"name": "广州一区"
				},
				{
					"id": "gz02",
					"name": "广州二区"
				}
			]
		},
		{
			"areaName": "华北地区",
			"id": "bj",
			"name": "北京",
			"stage": "公测",
			"zone": [
				{
					"id": "bj01",
					"name": "北京一区"
				}
			]
		}
	],
	"requestId": "0a59221f5bc58964741d7b9605b4b602"
}
```