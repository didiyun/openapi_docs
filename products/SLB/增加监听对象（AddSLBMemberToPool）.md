## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/listener/pool/member/create`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型            | 描述              |
| -------- | ---- | --------------- | ----------------- |
| poolUuid | 是   | string          | 待添加的pool的uui |
| members  | 是   | array<[Member](#Member)> | 待添加的members   |

<span id="Member"></span>
Member:

| 参数名称 | 必选 | 类型   | 描述          |
| -------- | ---- | ------ | ------------- |
| dc2Uuid  | 是   | string | 添加的dc2Uuid |
| port     | 是   | int    | 端口        |
| weight   | 是   | int    | 权重          |

## 输出参数

| 参数名称  | 类型   | 描述         |
| --------- | ------ | ------------ |
| errno     | int    | 错误码       |
| errmsg    | string | 请求错误说明 |
| requestId | string | 请求唯一标识 |


## 错误码

| 错误码 | 说明     |
| ------ | -------- |
| 0      | 请求成功 |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/listener/pool/member/create' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "poolUuid": "a416efe9282b4b05b84e620040483921",
    "members": [
        {
            "dc2Uuid": "b664027f7ac85e8f846b75c40183410f",
            "weight": 100,
            "port": 80
        }
    ]
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "e3c176e6ab4f5ee58ba621886b04fc80",
            "progress": 0,
            "resourceUuid": "41a22037594e43eabda2197ef504705b",
            "success": false,
            "type": "CreateSLBPoolMember",
            "uuid": ""
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59221f5e85d29a57761ee206460a02"
}
```