## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/eip/list`

请求方法：POST
## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| start     | 是 | int      |查询EIP列表起始index，从0开始 |
| limit     | 是 | int      |查询EIP列表元素数量         |
| simplify  | 否 | bool     |是否简化输出       |
| condition | 否 | [EIPCondition](#EIPCondition) | 查询EIP条件 |

<span id="EIPCondition"></span>
EIPCondition:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| eipUuids | 否  | array&lt;string&gt; | 查询的EIP的Uuid集合 |
| eip     | 否 | string      |根据EIP的公网IP地址精确查询 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[EipResponse](#EipResponse)>| 请求返回数据| 

<span id="EipResponse"></span>
EIPResponse：（未指定simplify：简化输出时，不输出此字段）

|参数名称  | 类型 | 描述|
|--------|-----|-----|
|job | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此EIP正在进行的任务，若无任务则没有此字段 |
|eipUuid（simplify）  | string  |EIP唯一标识   |
|ip（simplify）	   | string  |EIP IP地址   |
|createTime（simplify）     | int64  |EIP创建时间  |
|updateTime（simplify）      | int64  |EIP更新时间   |
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
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |
|41039 | 查询EIP信息失败 |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/network/eip/list \
 -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b99e6ddd6b427b4d256969534a81d0773f4d7' \
 -H 'content-type: application/json' \
 -d '{"start":0,"limit":10,"simplify":false,"regionId":"gz"}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
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
		}
	],
	"requestId": "0a60538a5b659a5a716ca35bc2537bb0"
}
```
