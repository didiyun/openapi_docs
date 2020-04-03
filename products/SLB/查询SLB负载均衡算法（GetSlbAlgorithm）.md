## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/algorithm`

请求方法：GET

## 输出参数

| 参数名称  | 类型                            | 描述         |
| --------- | ------------------------------- | ------------ |
| errno     | int                             | 错误码       |
| errmsg    | string                          | 请求错误说明 |
| requestId | string                          | 请求唯一标识 |
| data      | array\<[Algorithm](#Algorithm)> | 请求返回数据 |

<span id="Algorithm"></span>
Algorithm:

| 参数名 | 类型   | 描述     |
| ------ | ------ | -------- |
| code   | string | 算法代码 |
| name   | string | 算法名称 |

## 错误码

| 错误码 | 说明     |
| ------ | -------- |
| 0      | 请求成功 |

## 示例

```
请求：
curl --location --request GET 'https://open.didiyunapi.com/dicloud/i/network/slb/algorithm' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92'
输出：
{
    "data": [
        {
            "code": "wrr",
            "name": "加权轮询"
        },
        {
            "code": "minconn",
            "name": "最少连接"
        },
        {
            "code": "srch",
            "name": "源地址散列"
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59380b5e85bc1758db76ca066c5502",
    "stack": []
}
```