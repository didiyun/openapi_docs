## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/compute/dc2/count`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id，希望查询的可用区，不传则表示查询此地域下的所有可用区 |
|vpcUuids     | 否 |   array&lt;string&gt;  |   查询多个VPC下的DC2列表          |
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
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[DC2Count](#DC2Count)>   | 请求返回数据| 

<span id="DC2Count"></span>
DC2Count:

| 参数名称 | 类型 | 描述 |
|--------|-----|-----|
| totalCnt | int  |  DC2实例总量 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \https://open.didiyunapi.com/dicloud/i/compute/dc2/count \
 -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b99e6ddd6b427b4d256969534a81d0773f4d7' \
 -H 'content-type: application/json' \
 -d '{"vpcUuid":"7ba2538a5b65992dfb41a35b13c4b313","regionId":"gz"}'
 
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"totalCnt": 1
		}
	],
	"requestId": "0a60538a5b65992dfb41a35b13c403b0"
}
```
