## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/eip/count`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| eipUuids     | 是 | array&lt;string&gt;  | 查询EIP的Uuid集合  |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[EIPCount](#EIPCount)>	 | 请求返回数据| 

<span id="EIPCount"></span>
EIPCount:

| 参数名称 | 类型 | 描述 |
|--------|-----|-----|
| totalCnt | int  |  EIP实例总量 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/eip/count \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz"
}'
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
