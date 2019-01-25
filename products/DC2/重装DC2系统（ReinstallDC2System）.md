## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/compute/dc2/reinstall`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id |
| dc2 | 是 | array<[ReinstallDC2Input](#ReinstallDC2Input)> | 要重装的DC2信息，一次不能超过20台 |

<span id="ReinstallDC2Input"></span>
ReinstallDC2Input：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| dc2Uuid     | 是 |   string  |   需要重装系统的DC2的uuid          |
| imgUuid |  是 | string | 需要重装的镜像Uuid（重装DC2暂时不支持使用快照Uuid重装）|
| pubKeyUuids   | 是 |   array&lt;string&gt;           |   使用公钥Uuid列表进行DC2重装，与password二选一 |
| password | 是 | string | 使用密码进行重装，需将原密码进行16进制编码传递，与pubKeyUuids二选一 |
| proSecurityAgentEnabled | 否 | bool | 是否同时安装主机安全Agent专业版 |
| monitoringAgentEnabled | 否 | bool | 是否同时安装监控Agent | 

## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>   | 请求返回数据| 

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/compute/dc2/reinstall \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz"
	"dc2": [{
		"dc2Uuid": "c04325cc49495ea1bdc302c434a343fb",
		"imgUuid":"46b447a8b0a146779bbde3ca40e56843",
		"password":"53746d333137303234"
	}]
}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "a206b86217605dbe902ba7f251fe0070",
			"progress": 0,
			"success": false,
			"type": "ReinstallDC2System"
		}
	],
	"requestId": "0a60538a5bc5d3a398860f25c0d9ebb0"
}
```