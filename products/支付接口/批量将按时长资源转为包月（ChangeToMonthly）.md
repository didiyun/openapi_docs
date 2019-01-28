## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/changeToMonthly`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| payPeriod | 是 | int |  包月时长，单位为月，需大于等于1  |
| resource | 是 | array<[ResourceItemInput](#ResourceItemInput)> | 需要转为包月的资源信息  |

<span id="ResourceItemInput"></span>
ResourceItemInput:

| 操作类型 | 必选 |类型 |描述  |
|------|-----|-----| ----- |
| resourceType  | 是 | string | 资源类型 |
| resourceUuid  | 是 | string | 资源uuid |


## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
| data | empty array | 返回数据，此处为空 |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/changeToMonthly \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"payPeriod":1,
	"resource":[
		{
			"resourceUuid":"953777262c9e5bd48d1a5379ca220811",
			"resourceType":"dc2"
		},
		{
			"resourceUuid":"2a84e7317d235aa9a60da460bc65e102",
			"resourceType":"eip"
		}
		]
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": [],
    "requestId": "0a60538a5bd03ca2db8b0cc7715ffeb0"
}

```
