## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/sshkeys/delete`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| pubKeyUuid | 是 | string | 待删除的公钥名Uuid |


## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[DeleteSSHKeyResponse](#DeleteSSHKeyResponse)>   | 请求返回数据 | 

<span id="DeleteSSHKeyResponse"></span>
DeleteSSHKeyResponse:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| pubKeyUuid | string  |  被删除的公钥Uuid |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/sshkeys/delete \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"pubKeyUuid":"12fae73187074f40ab23c50cc7997ff6"
}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"pubKeyUuid": "12fae73187074f40ab23c50cc7997ff6"
		}
	],
	"stack": [],
	"requestId": "0a60538a5bc5e17aaa590f25d518ceb0"
}

```