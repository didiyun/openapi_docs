## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/checkBalance`

请求方法：GET

## 输入参数
无额外输入参数

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | [Balance](#balance)	 | 请求返回数据 | 

<span id="balance"></span>
Balance:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| balance | float| 剩余金额（包含冻结金额，单位为元，保留小数点后三位） |
| creditLine | float| 可欠费额度（单位为元，保留小数点后三位） |
| frozenBalance | float | 已被冻结金额（未完成订单、未结算扣费等引起，单位为元，保留小数点后三位）|

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X GET \
  https://open.didiyunapi.com/dicloud/w/checkBalance \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' 
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "requestId": "0a59c12e5e9d058d7ac40eb97eb1fb02",
    "data": {
        "balance": 2.011,
        "creditLine": 0,
        "frozenBalance": 0.05
    }
}
```
