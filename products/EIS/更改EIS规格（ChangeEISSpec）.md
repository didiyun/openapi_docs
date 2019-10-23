## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/eis/changeSpec`

请求方法：POST
## 输入参数
<span id="ChangeEISSpecParams"></span>
ChangeEISSpecParams:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| couponId | 否 | string | 本次操作使用的优惠券id |
| eis     | 是 | array<[ChangeEISSpecInput](#ChangeEISSpecInput)>   | EIS描述信息  |

<span id="ChangeEISSpecInput"></span>
ChangeEISSpecInput:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|eisUuid  | 是 |string  |EIS实例唯一标识 |
|eisQps | 是 | int | EIS实例要更改的新带宽 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/eis/changeSpec \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId": "gz",
	"eis":[
        {
            "eisUuid":"30ab971ede104c3b8cafb1a776c021d2",
            "eisQps":1
        }
    ]
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"requestId": "0a60538a5b656a44cb88969f5618f6b0"
}
```
