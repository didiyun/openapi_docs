## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/listener/delete`

请求方法：POST

## 输入参数

| 参数名称    | 必选 | 类型                  | 描述                |
| ----------- | ---- | --------------------- | ------------------- |
| slbListener | 是   | array\<[Listener](#SLBListener)\> | 待删除的SLBListener |

<span id="Listener"></span>
Listener:

| 参数名称        | 必选 | 类型                            | 描述            |
| --------------- | ---- | ------------------------------- | --------------- |
| slbListenerUuid | 是   | string                          | 待删除的UUID    |


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
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/listener/delete' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "slbListener": [
        {
            "slbListenerUuid": "bf03a39b6f3551fa842ee0e83c46b60c"
        }
    ]
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "28f68a3c8ef452a18e0454fe1712fb55",
            "progress": 0,
            "resourceUuid": "bf03a39b6f3551fa842ee0e83c46b60c",
            "success": false,
            "type": "DeleteSLBLoadBalancerListener",
            "uuid": ""
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59253c5e85d1840abd6a4406281302"
}
```

