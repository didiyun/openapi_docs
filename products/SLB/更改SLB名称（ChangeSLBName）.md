## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/changeName`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型                | 描述                  |
| -------- | ---- | ------------------- | --------------------- |
| slb      | 是   | array<[SLB](#SLB)\> | 所需修改的SLB相关参数 |

<span id="Member"></span>
Member:

| 参数名称 | 类型   | 描述              |
| -------- | ------ | ----------------- |
| slbUuid  | string | 待改名的slb的Uuid |
| name     | string | 待改的名字        |

## 输出参数

| 参数名称  | 类型                                                         | 描述         |
| --------- | ------------------------------------------------------------ | ------------ |
| errno     | int                                                          | 错误码       |
| errmsg    | string                                                       | 请求错误说明 |
| requestId | string                                                       | 请求唯一标识 |
| data      | array\<[Job](/static/docs-content/products/通用响应结构.md#Job)\> |              |

## 错误码

| 错误码 | 说明     |
| ------ | -------- |
| 0      | 请求成功 |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/changeName' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "slb": [
        {
            "slbUuid": "8db9b75da124545e8e6117ea3987229a",
            "name": "slb_test_test"
        }
    ]
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "c0d53f4a7af95643ab8ae2321840cc47",
            "progress": 0,
            "resourceUuid": "8db9b75da124545e8e6117ea3987229a",
            "success": false,
            "type": "ChangeSLBLoadBalancerName",
            "uuid": ""
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59380b5e85cf4a51df76d206689902"
}
```