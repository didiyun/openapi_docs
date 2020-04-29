## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/api/tags/add`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| resource | 是 | array<[AddResourceTagsInput](#AddResourceTagsInput)> | 要添加标签的资源信息 |
| tags | 是 | array&lt;string&gt; |  要添加的标签名二维(key:value)，一维（key); 最多10个标签 |

<span id="AddResourceTagsInput"></span>
AddResourceTagsInput：

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|resourceUuid | 是 |   string  | 需要操作的资源uuid |
|resourceType | 是 |   string  | 需要操作的资源类型（dc2,eip,slb,sg,ebs,mysql,vpc）|

## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  | 错误码 |
|errmsg|string| 请求错误说明   |
|data | array | 请求返回数据 |

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/api/tags/add \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
          "tags":["what:x","the:y","god:g"],
          "resource":[{
              "resourceUuid":"abc",
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
