## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/sshkeys/list`

请求方法：GET
## 输入参数
无


## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[SSHKeyResponse](#SSHKeyResponse)>   | 请求返回数据| 

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
curl -X GET https://open.didiyunapi.com/dicloud/i/sshkeys/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' 

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"createTime": 1533625388000,
			"fingerprint": "fe:e7:dc:c2:0d:59:8b:76:63:71:eb:6a:d7:df:4c:bb",
			"key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC+QZvthvv3t2rl9DBkMCBJIUW/49ieFou/YHtrqBcWfKaZelcC/UBYTZRnBtmuiAjKdal1G7z92GktQSdBCgKz6to+5LLBf65dCiaqbU01xDkaG0/okSIEyySMH7g2PedrplGk+M/AMsQc7nEo32/l9+HywpN3G/VFRns5GgECRXpN2mh0V2flQry+90xPBVut9zSBCE33tFu4R5iwQRvYW86NG1alyeSYfaTfpcPfH2bpBcfZxhkl4XWsvPMx6vb7O4oUvqaHhbTSsZuauMzzNKPnuqPoyYBkBZ+HmDMV1S/1dnm735jHIRzL39uwybAaaUvBmmLDavnfKQxkJGCH songtianming@didichuxing.com",
			"name": "songtianming@didichuxing.com",
			"pubKeyUuid": "fb82eff464ae48adb72f93225f53d50a"
		}
	],
	"requestId": "0a60538a5bc5decc6f930f250eee8ab0"
}
```