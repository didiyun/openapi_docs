## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/listener/pool/member/delete`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型             | 描述           |
| -------- | ---- | ---------------- | -------------- |
| members  | 是   | array<Member&gt; | 待删除的Member |

<span id="Member"></span>
Member:

| 参数名称      | 必选 | 类型   | 描述               |
| ------------- | ---- | ------ | ------------------ |
| slbMemberUuid | 是   | string | 待删除的memberUuid |

## 输出参数

| 参数名称  | 类型                                                         | 描述         |
| --------- | ------------------------------------------------------------ | ------------ |
| errno     | int                                                          | 错误码       |
| errmsg    | string                                                       | 请求错误说明 |
| requestId | string                                                       | 请求唯一标识 |
| data      | array\<[Job](/static/docs-content/products/通用响应结构.md#Job)\> | job信息      |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/listener/pool/member/delete' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "members": [
        {
            "slbMemberUuid": "89607a0c02b940c79d351bfff643c8e4"
        }
    ]
}'

输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "50c0321ffd1251b4a94db43b3a7fe19d",
            "progress": 0,
            "resourceUuid": "89607a0c02b940c79d351bfff643c8e4",
            "success": false,
            "type": "DeleteSLBPoolMember",
            "uuid": ""
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59253c5e85d1f20abe6a430689ee02"
}
```

