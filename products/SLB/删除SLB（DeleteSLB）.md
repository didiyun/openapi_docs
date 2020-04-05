## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/delete`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型          | 描述                |
| -------- | ---- | ------------- | ------------------- |
| slb      | 是   | array\<[SLB](#SLB)\> | 待删除的SLBListener |
<span id="SLB"></span>
SLB:

| 参数名称 | 必选 | 类型   | 描述              |
| -------- | ---- | ------ | ----------------- |
| slbUuid  | 是   | string | 待删除的slb的Uuid |

## 

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
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/delete' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "slb": [
        {
            "slbUuid": "8db9b75da124545e8e6117ea3987229a"
        }
    ]
}'

输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "fb9f796c7e7057bd9e2f931ea3c04781",
            "progress": 0,
            "resourceUuid": "8db9b75da124545e8e6117ea3987229a",
            "success": false,
            "type": "DeleteSLBLoadBalancer",
            "uuid": ""
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59380b5e85d11555d576d00669b702"
}
```

