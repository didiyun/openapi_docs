## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb`

请求方法：POST

## 输入参数

| 参数名称 | 必选 | 类型   | 描述              |
| -------- | ---- | ------ | ----------------- |
| regionId | 是   | string | 地域id            |
| slbUuid  | 是   | string | 查询指定slb的uuid |

## 输出参数

| 参数名称  | 类型                               | 描述         |
| --------- | ---------------------------------- | ------------ |
| errno     | int                                | 错误码       |
| errmsg    | string                             | 请求错误说明 |
| requestId | string                             | 请求唯一标识 |
| data      | array<[SLBResponse](#SLBResponse)> | 请求返回数据 |

<span id="SLBResponse"></span>
SLBResponse：

| 参数名称   | 类型                                                         | 描述                                                   |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------ |
| job        | [Job](/static/docs-content/products/通用响应结构.md#Job)     | 此SLB正在进行的任务，若无任务则没有此字段              |
| slbUuid    | string                                                       | SLB唯一标识                                            |
| name       | string                                                       | SLB名称                                                |
| ip         | string                                                       | SLB内网IP                                              |
| wafStatus  | string                                                       | WAF状态，Disabled/Enabled                              |
| createTime | int                                                          | SLB创建时间                                            |
| updateTime | int                                                          | SLB更新时间                                            |
| beip       | [BEIP](#BEIP)                                                | 与SLB关联的SLB-EIP信息，没有EIP则为内网SLB，没有该字段 |
| vpc        | [VPC](#VPC)                                                  | SLB相关的VPC信息                                       |
| flow       | [Flow](#Flow)                                                | 流量信息，单位Kbps                                     |
| spec       | [Spec](#Spec)                                                | SLB规格信息                                            |
| region     | [Region](/static/docs-content/products/通用响应结构.md#Region) | SLB所处Region信息                                      |

<span id="BEIP"></span>
BEIP:

| 参数名称   | 类型   | 描述                 |
| ---------- | ------ | -------------------- |
| beipUuid   | string | SLB-EIP唯一标识      |
| ip         | string | SLB-EIP（SLB公网IP） |
| createTime | int    | SLB-EIP 创建时间     |
| updateTime | int    | SLB-EIP 更新时间     |

<span id="VPC"></span>
VPC:

| 参数名称   | 类型   | 描述          |
| ---------- | ------ | ------------- |
| vpcUuid    | string | VPC唯一标识   |
| name       | string | VPC名称       |
| isDefault  | bool   | 是否是默认VPC |
| createTime | int    | VPC创建时间   |
| updateTime | int    | VPC更新时间   |

<span id="Flow"></span>
Flow:

| 参数名称 | 类型  | 描述   |
| -------- | ----- | ------ |
| in       | float | 入流量 |
| out      | float | 出流量 |

<span id="Spec"></span>
Spec:

| 参数名称     | 类型   | 描述         |
| ------------ | ------ | ------------ |
| offeringUuid | string | 规格唯一标识 |

## 错误码

| 错误码 | 说明            |
| ------ | --------------- |
| 0      | 请求成功        |
| 41039  | 查询EIP信息失败 |

## 示例

```
请求：
curl --location --request GET 'https://open.didicloud.io/dicloud/i/network/slb' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
	"regionId":"pre",
    "slbUuid": "8db9b75da124545e8e6117ea3987229a"
}'
输出：
{
    "data": [
        {
            "beip": {
                "beipId": "beip-ayyirl9l",
                "beipProject": "DefaultProject",
                "beipProjectId": "project-r614cxbvi4",
                "beipTags": [],
                "beipUuid": "532a8fa540c05942a9cee6bbdc8a938d",
                "createTime": 1585826046000,
                "ip": "116.85.255.156",
                "region": {
                    "id": "pre",
                    "name": "预发",
                    "zone": {
                        "id": ""
                    }
                },
                "updateTime": 1585826046000
            },
            "createTime": 1585826046000,
            "flow": {
                "in": 0,
                "out": 0
            },
            "ip": "10.255.1.169",
            "listenerCnt": {
                "healthyListenerCnt": 1,
                "l4ListenerCnt": 1,
                "l7ListenerCnt": 0,
                "totalListenerCnt": 1
            },
            "name": "slb_test",
            "region": {
                "id": "pre",
                "name": "预发",
                "zone": {
                    "id": ""
                }
            },
            "slbId": "slb-tkuh0oqy",
            "slbProject": "DefaultProject",
            "slbProjectId": "project-r614cxbvi4",
            "slbTags": [],
            "slbUuid": "8db9b75da124545e8e6117ea3987229a",
            "updateTime": 1585826046000,
            "vpc": {
                "cidr": "10.0.0.0/8",
                "createTime": 1510819511000,
                "desc": "default l2 network",
                "isDefault": true,
                "name": "default-vpc",
                "updateTime": 1525423711000,
                "vpcId": "vpc-adub9dcp",
                "vpcProject": "DefaultProject",
                "vpcProjectId": "project-r614cxbvi4",
                "vpcTags": [],
                "vpcUuid": "feca9662bffc46328e786b917e86c0ca"
            }
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59253c5e85c9e40abd6a440627b202",
    "stack": []
}
```