## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/delete`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| vpcUuid | 是 | string  | 删除此uuid对应的VPC下的SUBNET   |
| subnet | 是 | array<[DeleteSUBNETInput](#DeleteSUBNETInput)> | 需要删除的SUBNET信息 |

<span id="DeleteSUBNETInput"></span>
DeleteSUBNETInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| subnetUuid     | 是 |   string  |   SUBNET的uuid    |

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

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/delete \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"vpcUuid": "e32a224660824af1ba84ca7eeebd93ff",
	"subnet": [{
		"subnetUuid": "3bd0dce4e3e654539dea7ec5461b8fcd"
	}]
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [{
		"done": false,
		"jobUuid": "7469f7efcc805658a18c449e59a34ab1",
		"progress": 0,
		"success": false,
		"type": "DeleteSubnet"
	}],
	"requestId": "0a60538a5bd134304d4b5c80711039b0"
}
```