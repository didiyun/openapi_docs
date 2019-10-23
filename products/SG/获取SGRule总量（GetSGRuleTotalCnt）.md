## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/sg/rule/count`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|regionId | 是 | string | 地域id |
| sgUuid | 否 | string | 查看此SG下的SGRule数量，**与dc2Uuid参数二选一** |
| dc2Uuid | 否 | string | 查看此DC2遵循的SGRule数量，**与dc2Uuid参数二选一** |
| type | 否 | string | 要查询的SGRule类型，"Ingress"为入方向，"Egress"为出方向 |
## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[SGRuleCount](#SGRuleCount)>	 | 请求返回数据| 

<span id="SGRuleCount"></span>
SgRuleCount:

| 参数名称 | 类型 | 描述 |
|--------|-----|-----|
| totalCnt | int  |  SGRule总量 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/sg/rule/count \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId": "gz",
	"sgUuid": "db1a4d0fa0e14d1a93c18fadf97b3065"
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"totalCnt": 10
		}
	],
	"requestId": "0a60538a5b65992dfb41a35b13c403b0"
}
```
