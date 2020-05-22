## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/api/tags/delete`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| resource | 是 | array<[DeleteResourceTagsInput](#DeleteResourceTagsInput)> | 要删除标签的资源信息 |
| tags | 是 | array&lt;string&gt; | 要删除的标签(key:value) |

<span id="DeleteResourceTagsInput"></span>
DeleteResourceTagsInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|resourceUuid | 是 | string | 需要操作的资源uuid |
|resourceType | 是 | string | 需要操作的资源类型 |

## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|data | array | 请求返回数据 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功 |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/api/tags/delete \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
          "tags":["what:x","the:y","god:g"],
          "resource":[{
              "resourceUuid":"c04325cc49495ea1bdc302c434a343fb",
              "resourceType":"dc2"
          }]
}'

输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": []
}
```
