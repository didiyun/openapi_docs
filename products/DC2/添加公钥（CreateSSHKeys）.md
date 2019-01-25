## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/sshkeys/create`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| name | 是 | string | 待添加的公钥名称 |
| key | 是 | string | 待添加的公钥 |


## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[SSHKeyResponse](#SSHKeyResponse)>   | 请求返回数据 | 

<span id="SSHKeyResponse"></span>
SSHKeyResponse:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| pubKeyUuid | string  |  公钥Uuid |
| name | string | 公钥名称 |
| key | string  |  公钥  |
| fingerprint | string  |  公钥指纹 |
| createTime | int64  |  公钥创建时间戳，单位为毫秒 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/sshkeys/create \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"name": "test",
	"key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD1FzlCjtZSZe3lQxZm1eYg7aiU0YzZFPUOlw3H9LVbhCUP2TrkFZDRreMEi3a2bR9r60cZzJQqBp1+spJDFOdfMNmkysQsGobQca01qATuo4slqNP7JLiEoHwG3aPtx/zONxbDF4fJIB3n7zIJkcIgkPpeWyTxO0xV4V4TdX4dvG29/owhEAQZeC78/YKHK3lTNb9gLa64zoc1ReUaqTLioVJd+VD5Xm1Pl/aM9JypW7e1Bmk7O/kHJ9lmlgOAomXoNJb2E5NYu2jiFiMXapkULc0OO3XO6WpbolX00Zv1udXlum/N3B0JBO3XZVswSgE6N7jgpyU3oge08sndWWVZ didi@localhost"
}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"createTime": 1539694795000,
			"fingerprint": "d5:bb:ce:8c:05:46:53:bc:bd:1a:66:ba:f1:4e:7e:e4",
			"key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD1FzlCjtZSZe3lQxZm1eYg7aiU0YzZFPUOlw3H9LVbhCUP2TrkFZDRreMEi3a2bR9r60cZzJQqBp1+spJDFOdfMNmkysQsGobQca01qATuo4slqNP7JLiEoHwG3aPtx/zONxbDF4fJIB3n7zIJkcIgkPpeWyTxO0xV4V4TdX4dvG29/owhEAQZeC78/YKHK3lTNb9gLa64zoc1ReUaqTLioVJd+VD5Xm1Pl/aM9JypW7e1Bmk7O/kHJ9lmlgOAomXoNJb2E5NYu2jiFiMXapkULc0OO3XO6WpbolX00Zv1udXlum/N3B0JBO3XZVswSgE6N7jgpyU3oge08sndWWVZ didi@localhost",
			"name": "test",
			"pubKeyUuid": "12fae73187074f40ab23c50cc7997ff6"
		}
	],
	"requestId": "0a60538a5bc5e0cb7fe10f2566d7a0b0"
}
```