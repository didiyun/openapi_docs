## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/eip/changeBandwidth`

请求方法：POST
## 输入参数
<span id="ChangeEIPBandwidthParams"></span>
ChangeEIPBandwidthParams:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| couponId | 否 | string | 本次操作使用的优惠券id |
| eip     | 是 | array<[ChangeEIPBandwidthInput](#ChangeEIPBandwidthInput)>   | EIP描述信息  |

<span id="ChangeEIPBandwidthInput"></span>
ChangeEIPBandwidthInput:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|eipUuid  | 是 |string  |EIP唯一标识 |
|bandwidth | 是 | int | EIP实例要更改的新带宽 |
|chargeWithFlow | 否 | bool | 是否为按流量计费，需要注意待更改EIP的原付费方式，包月（先付费）EIP无法转为按流量计费方式 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>	 | 请求返回数据| 


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/i/network/eip/changeBandwidth \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId": "gz",
	"eip": [{
		"eipUuid": "c9ade20c2f485a7ead08a895eb601e37",
		"bandwidth": 10
	}]
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"async": false,
	"data": [
		{
			"done": false,
			"jobUuid": "c23fd05f26ef5b718507f1926a4271cc",
			"progress": 0,
			"success": false,
			"type": "ChangeEipOffering"
		}
	],
	"requestId": "0a60538a5b656a44cb88969f5618f6b0"
}
```
