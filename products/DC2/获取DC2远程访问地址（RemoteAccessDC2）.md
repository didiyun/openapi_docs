## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/websockify/dc2/remoteAccess`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| dc2Uuid | 是 | string | 需要远程访问的DC2的uuid |
| type | 否 | string | 远程访问模式，默认为“vnc”，可以指定为“webconsole”，两种访问模式交互不同 |

## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | [RemoteAccess](#RemoteAccess)   | 请求返回数据| 

<span id="RemoteAccess"></span>
RemoteAccess:

| 参数名称 | 类型 | 描述 |
|--------|-----|-----|
| URL | string  | 远程访问地址 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/websockify/dc2/remoteAccess \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"dc2Uuid": "c04325cc49495ea1bdc302c434a343fb"
}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": {
		"URL":"https://app.didiyun.com/vnc/?uuid=2606a53f17be5daab3d0c712ff48d6b0&access=zpgw7mk7054ndgc7twygqubgj5xr5sto"
	},
	"requestId": "0a60538a5bc5b82852200f252d882fb0"
}
```
