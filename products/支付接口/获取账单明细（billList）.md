## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/billList`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| tradeType | 否 | []string |交易类型，取值列表如[TradeType](#tradeType)所示，缺省为all|
| fundType | 否 | string |入账类型，取值为in表示账户入账，例如充值，取值为out为出账，取值all为不区分出入账，缺省为all |
| startTime | 是 | int64 |查询起始时间，取毫秒为单位的unix_timestamp|
| endTime | 是 | int64 | 查询结束时间，取毫秒为单位的unix_timestamp |
| limit  | 否 | int16  | 查询限制数目，缺省为10，最大为100 |
| offset  | 否 | int32  | 查询起止index，缺省为0，配合limit使用 |

<span id="tradeType"></span>
TradeType:

| 取值 | 描述 |
| ------ | ----- |
|all|         所有类型|
|recharge|         充值|
|withdraw|         提现|
|order_refund|     退货|
|coupon_recharge|  优惠券充值|
|postpaid_consume| 后付费消费|
|prepaid_create|   预付费购买消费|
|prepaid_continue| 预付费续费消费|
|prepaid_change|   预付费升降配消费|
|sys_adjust|       系统调账|
|commission|       手续费|

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | [BillList](#billList)	 | 请求返回数据 | 

<span id="billList"></span>
BillList:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| items | [BillListDetail](#billListDetail) | 收支明细数据列表 |
| total | int64 | 总条目数 |
| in | float | 总入账金额（单位为元，保留小数点后三位） |
| out | float | 总出账金额（单位为元，保留小数点后三位） |

<span id="billListDetail"></span>
BillListDetail:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| createTime | int64 | 数据创建时间，取毫秒为单位的unix_timestamp |
| tradeType | string | 交易类型，取值列表如[TradeType](#tradeType)所示 |
| describe | string | 交易记录中文表示 |
| amount | float | 收支金额，正数为入账，负数为出账（单位为元，保留小数点后三位） |
| recordId | int64 | 交易记录的id |
| status | int16 | 状态值，0为初始值，1为已结算 |



## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/billList \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"tradeType":[
        "all"
    ],
	"fundType":"all",
	"startTime":1587387400000,
	"endTime":1587387600000,
	"offset":0,
	"limit":10
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "requestId": "0a59c12e5e9d058d7ac40eb97eb1fb02",
    "data": {
        "items": [
            {
                "createTime": 1587387600000,
                "tradeType": "postpaid_consume",
                "describe": "按时长/按量扣费",
                "amount": -0.838,
                "recordId": 129861,
                "status": 1
            },
            {
                "createTime": 1587387400000,
                "tradeType": "sys_adjust",
                "describe": "额外奖励/账户调整",
                "amount": 10,
                "recordId": 129859,
                "status": 1
            }
        ],
        "total": 2,
        "in": 10,
        "out": -0.838
    }
}
```
