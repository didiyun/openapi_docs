## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/storage/cimg/changeName`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型                           | 描述         |
| -------- | ---- | ------------------------------ | ------------ |
| cimg     | 是   | array<[CIMGInput](#CIMGInput)> | 镜像描述信息 |

<span id="CIMGInput"></span>
CIMGInput:

| 参数名称          | 必选 | 类型     | 描述             |
| --------------- | ---- | ------ | ---------------- |
| cimgUuid       | 是   | string | 镜像唯一标识        |
| name          | 是   | string | 修改后的镜像名称     |


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
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/cimg/changeName \
  -H 'authorization: Bearer 2cafde94854e51908187f777611b081d1ca894a581b554159d6ebcd6b905e8d9' \
  -H 'content-type: application/json' \
  -d '{
    "cimg":[
        {"cimgUuid":"cbdba09c4ad4475f9f3d399947aaa99e",
         "name":"openapi自定义镜像修改名称_test"}
    ]
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "72e3500c85675df7b59a025e5e784426",
            "progress": 0,
            "resourceType": "cimg",
            "resourceUuid": "cbdba09c4ad4475f9f3d399947aaa99e",
            "status": "Processing",
            "success": false,
            "type": "ChangeCIMGName",
            "uuid": "72e3500c85675df7b59a025e5e784426"
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a594b2a5fdb03ddc11e075003e95502"
}
```