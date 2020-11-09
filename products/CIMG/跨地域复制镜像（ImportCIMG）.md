## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/storage/cimg/import`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型                           | 描述         |
| -------- | ---- | ------------------------------ | ------------ |
| regionId | 是   | string                         | 地域id       |
| cimg     | 是   | array<[CIMGInput](#CIMGInput)> | 镜像描述信息 |

<span id="CIMGInput"></span>
CIMGInput:

| 参数名称        | 必选 | 类型   | 描述               |
| --------------- | ---- | ------ | ------------------ |
| name            | 是   | string | 镜像名称           |
| originImageUuid | 是   | string | 源镜像uuid         |
| originRegionId  | 是   | string | 源镜像所在regionId |
| description     | 否   | string | 镜像描述           |

## 输出参数

| 参数名称  | 类型                                                         | 描述         |
| --------- | ------------------------------------------------------------ | ------------ |
| errno     | int                                                          | 错误码       |
| errmsg    | string                                                       | 请求错误说明 |
| requestId | string                                                       | 请求唯一标识 |
| data      | array<[Job](/static/docs-content/products/通用响应结构.md#Job)> | 请求返回数据 |

## 错误码

| 错误码 | 说明     |
| ------ | -------- |
| 0      | 请求成功 |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/cimg/import \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "cimg":{
        "name":"openapi自定义镜像跨地域",
        "originImageUuid":"4a48f88391134a01befe88ff98b68af8",
        "originRegionId":"bj",
        "description":"openapi测试"
    }
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "051f6d7688df5542be1a91123473d0df",
            "progress": 0,
            "resourceType": "cimg",
            "resourceUuid": "cbdba09c4ad4475f9f3d399947aaa99e",
            "status": "Processing",
            "success": false,
            "type": "ImportCIMG",
            "uuid": "051f6d7688df5542be1a91123473d0df"
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a594b2a5fa0d08957c447ac033e0c02"
}
```