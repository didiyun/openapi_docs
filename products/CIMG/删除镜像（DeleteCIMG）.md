## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/storage/cimg/delete`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型                           | 描述         |
| -------- | ---- | ------------------------------ | ------------ |
| cimg     | 是   | array<[CIMGInput](#CIMGInput)> | 镜像描述信息 |

<span id="CIMGInput"></span>
CIMGInput:

| 参数名称        | 必选 | 类型   | 描述               |
| --------------- | ---- | ------ | ------------------ |
| cimgUuid        | 是   | string | 镜像唯一标识         |

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
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/cimg/delete \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    "cimg":[{"cimgUuid":"579ddc8d6c364e6fa798698113260e6b"}]
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "7b78be0bd59e5938bf149f60f0958b09",
            "progress": 0,
            "resourceType": "cimg",
            "resourceUuid": "579ddc8d6c364e6fa798698113260e6b",
            "status": "Processing",
            "success": false,
            "type": "DeleteCIMG",
            "uuid": "7b78be0bd59e5938bf149f60f0958b09"
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59922a5fdafbd48d6d451003e75202"
}
```