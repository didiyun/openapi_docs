## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/eip/attach`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
|eip     | 是 | array<[AttachEIPToDC2Input](#AttachEIPToDC2Input)>   |EIP描述信息  |

<span id="AttachEIPToDC2Input"></span>
AttachEIPToDC2Input:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|eipUuid  | 是 |string   |EIP唯一标识 |
|bindingUuid|是|string  |待绑定的DC2的Uuid|

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>	 | 请求返回数据| 

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/eip/attach \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"eip": [{
		"eipUuid": "3117ad495d8e5d96b78f82a50007ff9b",
		"bindingUuid": "8fbed61b09a2559aba557a110b7455ff"
	}]
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [{
		"done": false,
		"jobUuid": "dde7a81bf0e158d697b696baa100a96f",
		"progress": 0,
		"success": false,
		"type": "AttachEIP"
	}],
	"requestId": "0a60538a5b65614569917431f2d90bb0"
}
```