## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/eip/assign`

请求方法：POST
## 输入参数
<span id="CreateEIPParams"></span>
CreateEIPParams:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| autoContinue      | 否 |   bool    |   是否设置EIP自动续费          |
| payPeriod | 否 | int | 购买包月时长，单位为月，范围[0,36]，不传或传0表示后付费 |
| couponId | 否 | string | 本次操作使用的优惠券id |
| count | 否 | int | 批量购买参数，不传默认购买一个EIP，不能超过20 |
|bandwidth	 | 是 | int  |EIP的带宽   |
|chargeWithFlow |否 | bool  | 是否要按流量计费（为按流量计费时，默认为后付费）  |
|bindingUuid  | 否 | string |预绑定的DC2的Uuid，如果有，则创建同时将EIP绑定至此DC2（当传此参数时，count必须不传或传1） |
|eipTags  | 否|  array&lt;string&gt;    | EIP标签  |


## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>	 | 请求返回数据| 


## 错误码
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/eip/assign \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"bandwidth":2,
	"count":2,
	"chargeWithFlow":true
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "d385ea9a10b85ed7b3bd1acedab746ed",
			"progress": 0,
			"success": false,
			"type": "CreateEIP"
		},
		{
			"done": false,
			"jobUuid": "9e07c722550f56189de1bc51564edeeb",
			"progress": 0,
			"success": false,
			"type": "CreateEIP"
		}
	],
	"requestId": "0a60538a5bc5e55145990f25b7b5aeb0"
}
```