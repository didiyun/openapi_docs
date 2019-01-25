## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/eip`

请求方法：GET
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| eipUuid     | 是 | string  |EIP的Uuid  |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[EIPResponse](#EipResponse)>| 请求返回数据| 


<span id="EipResponse"></span>
EIPResponse：

|参数名称  | 类型 | 描述|
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此EIP正在进行的任务，若无任务则没有此字段 |
|eipUuid  | string  |EIP唯一标识   |
|ip   | string  |EIP IP地址   |
|createTime     | int64  |EIP创建时间  |
|updateTime      | int64  |EIP更新时间   |
|eipTags  | array&lt;string&gt;    |EIP的tags     |
|dc2	  | [DC2](#Dc22)   | 与EIP关联的DC2信息，没有DC2则没有该字段 |


<span id="Dc22"></span>
DC2:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
|dc2Uuid  | string  |DC2唯一标识   |
|name   | string  |DC2名称     |
|createTime     | int64  |DC2创建时间    |
|updateTime      | int64  |DC2更新时间       |
|status   | string  |DC2状态     |
|osType  | string  |DC2操作系统发行版及版本号   |


## 错误码
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X GET 'https://open.didiyunapi.com/dicloud/i/network/eip?eipUuid=c9ade20c2f485a7ead08a895eb601e37&regionId=gz' \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' 
输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": {
		"createTime": 1533371141000,
		"eipId": "eip-ke49ilpo",
		"eipTags": [],
		"eipUuid": "c9ade20c2f485a7ead08a895eb601e37",
		"ip": "172.22.52.169",
		"region": {
			"areaName": "",
			"id": "gz",
			"name": "广州"
		},
		"updateTime": 1533372998000
	},
	"requestId": "0a60538a5b659be0546fa35b9aa05cb0"
}
```