## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/image/list`

请求方法：GET
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |


## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[ImageResponse](#ImageResponse)>   | 请求返回数据| 

<span id="ImageResponse"></span>
ImageResponse:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| imgUuid | string  |  镜像Uuid |
| name | string | 镜像名称 |
| osFamily | string  |  操作系统发行版本  |
| osVersion | string  |  操作系统版本号 |
| platform | string  |  镜像平台，"Linux"或"Windows" |
| scenes | array&lt;string&gt;  |  镜像使用场景，"base"为基础镜像，"gpu"为带GPU驱动的镜像 |
| type | string  |  镜像类型，"standard"为标准镜像，"oneClick"为一键部署镜像 |
| requirement | [ImageRequirement](#ImageRequirement) | 镜像对于DC2配置的最小要求 | 

<span id="ImageRequirement"></span>
ImageRequirement:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| minCpuNum | int | 最小CPU数量 |
| minDiskSize | int64 | 最小磁盘大小，单位为Byte |
| minMemorySize | int64 | 最小内存大小，单位为Byte |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X GET https://open.didiyunapi.com/dicloud/i/image/list?regionId=gz \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' 

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"imgUuid": "a6c61db4b7bb4959b406a64989d7152a",
			"name": "Gpu-image-test",
			"osFamily": "Ubuntu",
			"osVersion": "16.04_CUDA9.0",
			"platform": "Linux",
			"requirement": {
				"minDiskSize": 990707712
			},
			"scenes": [
				"gpu"
			],
			"type": "standard"
		},
		{
			"imgUuid": "76df94ed692a4104acfd5d7c91afbb65",
			"name": "Docker on Ubuntu:16.04",
			"osFamily": "Ubuntu",
			"osVersion": "16.04",
			"platform": "Linux",
			"scenes": [
				"base"
			],
			"type": "oneClick"
		}
	],
	"requestId": "0a60538a5bc5dca81b130f25d377d9b0"
}
```