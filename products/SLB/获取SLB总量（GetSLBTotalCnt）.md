## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/count`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型                | 描述     |
| -------- | ---- | ------------------- | -------- |
| vpcUuids | 是   | array&lt;string&gt; | VPC Uuid |

## 输出参数

| 参数名称  | 类型                 | 描述         |
| --------- | -------------------- | ------------ |
| errno     | int                  | 错误码       |
| errmsg    | string               | 请求错误说明 |
| requestId | string               | 请求唯一标识 |
| data      | array<[Data](#Data)> | 请求返回数据 |

<span id="Data"></span>
Data：

| 参数名称 | 类型  | 描述          |
| -------- | ----- | ------------- |
| totalCnt | int64 | 拥有的SLB总数 |

## 错误码

| 错误码 | 说明     |
| ------ | -------- |
| 0      | 请求成功 |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/count' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
	"vpcUuid":"feca9662bffc46328e786b917e86c0ca"
}'

输出：
{
    "data": [
        {
            "totalCnt": 20
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59380b5e85cfe4482276bb064d2f02"
}
```

