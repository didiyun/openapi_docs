## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/checkPrice`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| resourceType | 是 | string |要购买的商品类型，如表[CheckPriceParams](#checkPriceParams)所示 |
| isChange | 是 | bool |是否是更改规格操作 |
| checkCoupon | 否 | bool | 询价同时是否匹配最符合的优惠券 |
| goods  | 是 | object  | 要购买的商品的输入参数,如表[CheckPriceParams](#checkPriceParams)所示 |

<span id="checkPriceParams"></span>
CheckPriceParams:

| 操作类型 | 描述 | resourceType | goods |
| ------ | ----- | ----- | ----- |
| CreateDC2 | 创建DC2  |  dc2 | [CreateDC2Params](/static/docs-content/products/DC2/创建DC2（CreateDC2）.md#CreateDC2Params) |
| ChangeDC2Spec | 更改DC2配置 | dc2 | [ChangeDC2Spec](/static/docs-content/products/DC2/更改DC2配置（ChangeDC2Spec）.md#ChangeDC2Spec) |
| CreateEIP | 创建EIP | eip | [CreateEIPParams](/static/docs-content/products/EIP/创建EIP实例（CreateEIP）.md#CreateEIPParams) |
| ChangeEIPBandwidth | 更改EIP带宽 | eip | [ChangeEIPBandwidth](/static/docs-content/products/EIP/更改EIP带宽（ChangeEIPBandwidth）.md#ChangeEIPBandwidth) |
| CreateEBS | 创建EBS | ebs | [CreateEBSParams](/static/docs-content/products/EBS/创建EBS（CreateEBS）.md#CreateEBSParams) |
| ChangeEBSSize | 更改EBS大小 | ebs | [ChangeEBSSizeParams](/static/docs-content/products/EBS/更改EBS大小（ChangeEBSSize）.md#ChangeEBSSizeParams)

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | [CheckPriceResponse](#CheckPriceResponse)	 | 请求返回数据 | 

<span id="CheckPriceResponse"></span>
CheckPriceResponse:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| bestCouponId | string | 最匹配的优惠券id，可在操作中传入 |
| cashBalance | int64 | 现金余额 |
| couponBalance | int64 | 优惠券余额 |
| frozenPrice | int64 | 当前冻结金额 |
| isClearToCreate | bool | 余额是否足够一次创建 |
| originPrice | int64 | 原价格 |
| payType | string | 付费方式，"postPaid"为后付费，"prepPaid"为先付费 |
| postPaidPrice | int64 | 后付费部分的价格，单位为月 |
| prePaidPrice | int64 | 先付费部分的价格，单位为月 |
| subPrice | int64 | 当余额不足时，表示还差多少钱可以创建此资源 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/checkPrice \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"resourceType":"dc2",
	"isChange":false,
	"goods":{
		"payPeriod":2,
		"dc2Model":"dc2.s1.small1.d20",
		"eip":{
			"bandwidth":1
		}
	}
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": {
        "bestCouponId": "",
        "cashBalance": 333300,
        "couponBalance": 1823921,
        "frozenPrice": 0,
        "isClearToCreate": true,
        "originPrice": 9200,
        "payType": "prePaid",
        "postPaidPrice": 0,
        "prePaidPrice": 9200,
        "subPrice": 0
    },
    "requestId": "0a60538a5bd03e8f6fdc1926f3dba9b0"
}
```
