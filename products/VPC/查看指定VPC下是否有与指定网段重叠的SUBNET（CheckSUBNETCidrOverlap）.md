## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/checkCidrOverlap`

请求方法：GET
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| vpcUuid | 是 | string  | 检查此VPC下的SUBNET   |
| cidr | 是 | string  | 需要检查的网段  |


## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[IsOverlapOutput](#IsOverlapOutput)>	 | 请求返回数据 | 

<span id="IsOverlapOutput"></span>
IsOverlapOutput：

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| isOverlap   |  bool  | 是否有重叠  |


## 错误码
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X GET https://open.didiyunapi.com/dicloud/i/network/vpc/subnet/checkCidrOverlap?cidr=10.0.0.0%2F23&vpcUuid=e32a224660824af1ba84ca7eeebd93ff \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [{
		"isOverlap": false
	}],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```