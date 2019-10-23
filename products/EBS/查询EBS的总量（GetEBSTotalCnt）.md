## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/storage/ebs/count`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id，不传则查询当前区域下全部可用区 |
| dc2Uuids | 否  | array&lt;string&gt; | 查询此dc2Uuid集合绑定的EBS实例 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[EBSCount](#EBSCount)>   | 请求返回数据| 

<span id="EBSCount"></span>
Count:

| 参数名称 | 类型 | 描述 |
|--------|-----|-----|
| totalCnt | int  |  EBS实例总量 |

## 错误码
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/ebs/count \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{"regionId":"gz"}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"totalCnt": 1
		}
	],
	"requestId": "0a60538a5bc6053e33070f2587beb1b0"
}
```
