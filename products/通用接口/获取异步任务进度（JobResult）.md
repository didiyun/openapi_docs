任务是滴滴云API的基本概念之一。
所有滴滴云API的资源类操作都是以异步任务的形式存在的。
获取一个任务是否结束，结果是否成功，需要调用获取异步任务进度（JobResult）接口，对一个或多个任务的进度及结果进行查询。

## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/result`

请求方法：GET

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| jobUuids   | 是 | array&lt;string&gt;  | 任务的Uuid，多个Uuid用逗号‘,’进行连接 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[Job](#Job)>	 | 请求返回数据|

<span id="Job"></span>
Job（任务进度）:

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| jobUuid | string  |  任务唯一标识 |
| resourceUuid | string | 当前正在操作的资源Uuid |
| type | string  |  任务类型，描述这个任务在做什么事情 |
| progress | float64  |  任务执行进度，为0-100之间的一个百分比值 |
| done | bool  |  任务是否已经执行结束 |
| success | bool  |  任务执行的结果是否成功 |
| result | string  |  任务执行失败情况下，返回失败原因 |

> 滴滴云API的任务（job）具有两个关键概念`done`和`success`，表示任务的执行状态。

| done | success | 说明 | 建议的操作 |
|---|---|---|---|
| false | false | 任务尚未结束运行 | 继续轮询此任务进度 |
| true | false | 任务结束但结果为失败 | 查看result字段中的失败原因，并重新发起操作请求 |
| true | true | 任务结束，结果为成功 | 进行下一步操作 |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X GET \
  'https://open.didiyunapi.com/dicloud/i/result?jobUuids=c23fd05f26ef5b718507f1926a4271cc&regionId=gz' \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": true,
			"jobUuid": "c23fd05f26ef5b718507f1926a4271cc",
			"progress": 100,
			"resourceUuid": "c9ade20c2f485a7ead08a895eb601e37",
			"success": true,
			"type": "ChangeEipOffering",
			"uuid": "c23fd05f26ef5b718507f1926a4271cc"
		}
	],
	"requestId": "0a60538a5b656e592104969f4b9ef2b0"
}
```