## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/listener/pool/member/update`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型                       | 描述            |
| -------- | ---- | -------------------------- | --------------- |
| members  | 是   | array\<[Member](#Member)\> | 待更新的members |

<span id="Member"></span>
Member:

| 参数名称      | 必选 | 类型   | 描述             |
| ------------- | ---- | ------ | ---------------- |
| slbMemberUuid | 是   | string | 更改的memberUuid |
| port          | 是   | int    | 端口             |
| weight        | 是   | int    | 权重             |

## 输出参数

| 参数名称  | 类型                                                         | 描述         |
| --------- | ------------------------------------------------------------ | ------------ |
| errno     | int                                                          | 错误码       |
| errmsg    | string                                                       | 请求错误说明 |
| requestId | string                                                       | 请求唯一标识 |
| data      | array\<[Job](/static/docs-content/products/通用响应结构.md#Job)\> | job信息      |


## 错误码

| 错误码 | 说明     |
| ------ | -------- |
| 0      | 请求成功 |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/listener/pool/member/update' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "members": [
        {
            "slbMemberUuid": "f47da44335d3475ba9b66b9cbb8531c0",
            "weight": 98,
            "port": 8080
        }
    ]
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "c7e61bb21d5d5fbf989297aa1e9444af",
            "progress": 0,
            "resourceUuid": "f47da44335d3475ba9b66b9cbb8531c0",
            "success": false,
            "type": "UpdateSLBPoolMember",
            "uuid": ""
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59253c5e85cd8f11ae6a5b0623c302"
}
```

