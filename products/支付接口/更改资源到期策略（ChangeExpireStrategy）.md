## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/changeExpireStrategy`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| autoRenewCnt | 是 | int |  资源到期之前策略，表示自动续费月数，若等于0，表示到期不自动续费  |
| autoSwitch | 是 | bool | 资源到期之后策略，true表示自动转为按时长计费，false表示删除资源，（若设置了到期前自动续费策略，此参数也将在到期前自动续费失败时起作用，因此请谨慎设置） |
| resource | 是 | [ResourceItemInput](#ResourceItemInput) | 需要设置策略的资源信息 |

<span id="ResourceItemInput"></span>
ResourceItemInput:

| 操作类型 | 必选 |类型 |描述  |
|------|-----|-----| ----- |
| resourceType   | string | 资源类型 |
| resourceUuid    | string | 资源uuid |

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
|1100017| 包月到期策略设置失败 |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/changeExpireStrategy \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"autoRenewCnt":2,
	"autoSwitch":true,
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
    "requestId": "0a60538a5bd11770dc2c50ca26c398b0"
}
```

