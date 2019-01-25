## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/sg/attach`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| sg | 是 | array<[SGInputForAttachDC2ToSG](#SGInputForAttachDC2ToSG)> | 需要绑定的SG信息 |
| dc2 | 是 | array<[DC2InputForAttachDC2ToSG](#DC2InputForAttachDC2ToSG)> | 需要绑定的DC2信息 |

<span id="SGInputForAttachDC2ToSG"></span>
SGInputForAttachDC2ToSG：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| sgUuid     | 是 |   string  |  需绑定的SG的uuid    |

<span id="DC2InputForAttachDC2ToSG"></span>
DC2InputForAttachDC2ToSG：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| dc2Uuid     | 是 |   string  |  需绑定的DC2的uuid    |



## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>	 | 请求返回数据 | 


## 错误码
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |
| 41056 | 绑定DC2至安全组失败 |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/network/sg/attach \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "regionId":"gz"
	"sg": [{
		"sgUuid": "ce62656b22165a7293e9d009bd72ce76"
	},
	"dc2": [{
		"dc2Uuid": "953777262c9e5bd48d1a5379ca220811"
	}]
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [{
		"done": false,
		"jobUuid": "3eb1f286b01f59d08228e4bbe319eb6f",
		"progress": 0,
		"success": false,
		"type": "AttachDC2ToSecurityGroup"
	}],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```