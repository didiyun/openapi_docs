## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/api/tags/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| name | 否 | string | 标签名(key:value) |
| start | 否 | int | 起始记录位置 |
| limit | 是 | int | 一次最多显示多少个 |

## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|data | array | 请求返回数据 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/api/tags/list \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
          "condition":{
              "name":"abc:def"
          }
          "limit":10,
          "start":0
}'

输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": [
        "abc:def",
        "abc:defg",
        "abc:defh"
    ]
}
```
