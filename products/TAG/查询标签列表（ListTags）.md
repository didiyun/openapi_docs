## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/api/tags/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| start | 否 | int | 起始记录位置 |
| limit | 是 | int | 一次最多显示多少个 |
| condition | 是   | [Condition](#Condition) | 查询条件 |

<span id="Condition"></span>
Condition:

| 参数名称 | 必选 | 类型   | 描述  |
| ------ | ---- | ------ | ---------- |
| name | 是 | string | 标签名二维(key:value)，一维（key）；前缀匹配 |

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
## 资源标签查询
  资源的标签信息可通过对应资源查询接口得到。
