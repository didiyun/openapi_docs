## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/sg/count`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
|sgUuids | 否  | array&lt;string&gt; | 查询此uuid集合下的SG数量 |
|vpcUuid | 否 | string | 查询此uuid对应的VPC下的SG数量 |
|dc2Uuid | 否 | string | 查询此uuid对应的DC2相关的SG数量 |
|dc2Exclude | 否 | bool | 与dc2Uuid配合使用，不传或传false，表示查询此DC2所绑定的SG数量，传true表示查询此DC2未绑定的SG数量 |
## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[SGCount](#SGCount)>	 | 请求返回数据| 

<span id="SGCount"></span>
SGCount:

| 参数名称 | 类型 | 描述 |
|--------|-----|-----|
| totalCnt | int  |  SG总量 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/sg/count \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz"
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"totalCnt": 1
		}
	],
	"requestId": "0a60538a5b65992dfb41a35b13c403b0"
}
```
