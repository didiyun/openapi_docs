对于计费资源，本接口提供批量查询资源的计费与规格信息的能力。
## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/getResourceChargeInfo`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| resource   | 是 | array<[ChargeInfoAndSpecInput](#ChargeInfoAndSpecInput)>  | 需要查询的资源信息  |

<span id="ChargeInfoAndSpecInput"></span>
ChargeInfoAndSpecInput:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| resourceUuid | string  | 需要查询的资源Uuid |
| resourceType | string  | 需要查询的资源类型 |	

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[ChargeInfoAndSpecResponse](#ChargeInfoAndSpecResponse)>	 | 请求返回数据 | 

<span id="ChargeInfoAndSpecResponse"></span>
ChargeInfoAndSpecResponse:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| resourceUuid | string  |  资源Uuid |
| charge       | [Charge](/static/docs-content/products/通用响应结构.md#Charge)  |  资源的计费信息 |
| spec     |  [ResourceSpec](/static/docs-content/products/通用响应结构.md#ResourceSpec)  |  资源的规格信息，不同资源对应的信息结构可参考[资源规格相关](/static/docs-content/products/通用响应结构.md#ResourceSpec)项 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/getResourceChargeInfo \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"resource":[{
		"resourceUuid":"18994c152f0d504ebb9cf3e69bf55aee",
		"resourceType":"eip"
	}]
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": [
        [
            {
                "charge": {
                    "chargeInfo": {
                        "period": {
                            "autoRenewCnt": 0,
                            "autoSwitch": false,
                            "payType": "postPaid",
                        }
                    },
                    "costThisMonth": 0,
                    "endTime": 0,
                },
                "resourceUuid": "18994c152f0d504ebb9cf3e69bf55aee",
                "spec": {
                    "bandwidth": 1024,
                    "chargeType": "bandwidth",
                    "inboundBandwidth": 1024,
                    "name": "eip-with-1M-bandwidth",
                    "offeringUuid": "35f588654ed44c13a4cfebaf1470549b",
                    "outboundBandwidth": 1024,
                    "peerOfferingUuid": "bac92fe5275f47f8aa03b795c43bd2ca",
                    "uuid": "35f588654ed44c13a4cfebaf1470549b"
                }
            }
        ]
    ],
    "requestId": "0a60538a5c0e17e7e1fd5c623ce623b0"
}
```