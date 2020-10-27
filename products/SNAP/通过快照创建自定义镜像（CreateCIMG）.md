## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/storage/cimg/create`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型                           | 描述         |
| -------- | ---- | ------------------------------ | ------------ |
| regionId | 是   | string                         | 地域id       |
| cimg     | 是   | array<[CIMGInput](#CIMGInput)> | SNAP描述信息 |

<span id="CIMGInput"></span>
CIMGInput:

| 参数名称    | 必选 | 类型   | 描述         |
| ----------- | ---- | ------ | ------------ |
| name        | 是   | string | 镜像名称     |
| snapUuid    | 是   | string | SNAP唯一标识 |
| description | 否   | string | 镜像描述     |

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
curl -X POST https://open.didiyunapi.com/dicloud/i/storage/cimg/create \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
    	"cimg":{
        "name":"openapi自定义镜像",
        "snapUuid":"3fd352092a3f553cb124223f6a7f09b4",
        "description":"测试自定义镜像"
    		}
}'
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "1efb7af82b225e608a86602166ba4318",
			"progress": 0,
			"success": false,
			"type": "ChangeSnapshotName"
		}
	],
	"requestId": "0a60538a5b6561f1623274313932acb0"
}
```