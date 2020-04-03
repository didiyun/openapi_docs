## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/list`

请求方法：POST

## 输入参数

| 参数名称  | 必选 | 类型                          | 描述                 |
| --------- | ---- | ----------------------------- | -------------------- |
| regionId  | 是   | string                        | 地域id               |
| start     | 是   | int                           | 查询SLB列表起始index |
| limit     | 是   | int                           | 每页个数             |
| condition | 否   | [SLBCondition](#SLBCondition) | 查询EIP条件          |

<span id="SLNCondition"></span>
SLBCondition:

| 参数名称 | 必选 | 类型                | 描述                |
| -------- | ---- | ------------------- | ------------------- |
| slbUuids | 否   | array&lt;string&gt; | 查询的SLB的Uuid集合 |
| vpcUuids | 否   | array&lt;string\>   | 根据vpc uuid查询    |
| beips    | 否   | array&lt;string\>   | 根据eip查询         |
| dc2ips   | 否   | array&lt;string\>   | 根据监听对象ip查询  |
| ips      | 否   | array&lt;string\>   | 根据ip查询          |

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
| createTime | int64                                                        | SLB创建时间                                            |
| updateTime | int64                                                        | SLB更新时间                                            |
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
| ip         | string | SLB-EIP（DC2公网IP） |
| createTime | int64  | SLB-EIP 创建时间     |
| updateTime | int64  | SLB-EIP 更新时间     |

<span id="VPC"></span>
VPC:

| 参数名称   | 类型   | 描述          |
| ---------- | ------ | ------------- |
| vpcUuid    | string | VPC唯一标识   |
| name       | string | VPC名称       |
| isDefault  | bool   | 是否是默认VPC |
| createTime | int64  | VPC创建时间   |
| updateTime | int64  | VPC更新时间   |

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
| 41070  | 查询SLB信息失败 |

## 示例

```
请求：
curl --location --request POST 'https://open.didicloud.io/dicloud/i/network/slb/list' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "regionId": "pre",
    "start": 0,
    "limit": 2,
    "simplify": false
}'
输出：
{
    "data": [
        {
            "createTime": 1585729576000,
            "flow": {
                "in": 0,
                "out": 0
            },
            "ip": "10.255.1.124",
            "listenerCnt": {
                "healthyListenerCnt": 1,
                "l4ListenerCnt": 1,
                "l7ListenerCnt": 0,
                "totalListenerCnt": 1
            },
            "name": "测试",
            "region": {
                "id": "pre",
                "name": "预发",
                "zone": {
                    "id": ""
                }
            },
            "slbId": "slb-f9g90r1y",
            "slbProject": "DefaultProject",
            "slbProjectId": "project-r614cxbvi4",
            "slbTags": [],
            "slbUuid": "8e5e41d4d42b57d5aa4ca1a6a8435f57",
            "updateTime": 1585729576000,
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
        },
        {
            "beip": {
                "beipId": "beip-ac96vy8f",
                "beipProject": "DefaultProject",
                "beipProjectId": "project-r614cxbvi4",
                "beipTags": [],
                "beipUuid": "4ee68f3070a05ebf98b3be7f5398ac17",
                "createTime": 1585708278000,
                "ip": "116.85.255.52",
                "region": {
                    "id": "pre",
                    "name": "预发",
                    "zone": {
                        "id": ""
                    }
                },
                "updateTime": 1585708278000
            },
            "createTime": 1585708278000,
            "flow": {
                "in": 0,
                "out": 0
            },
            "ip": "10.255.1.86",
            "listenerCnt": {
                "healthyListenerCnt": 0,
                "l4ListenerCnt": 1,
                "l7ListenerCnt": 0,
                "totalListenerCnt": 1
            },
            "name": "测试2",
            "region": {
                "id": "pre",
                "name": "预发",
                "zone": {
                    "id": ""
                }
            },
            "slbId": "slb-6nuau44t",
            "slbProject": "DefaultProject",
            "slbProjectId": "project-r614cxbvi4",
            "slbTags": [
                "测试"
            ],
            "slbUuid": "e5a06811a5fa50f2af315f8c9befbc4f",
            "updateTime": 1585708278000,
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
    "requestId": "0a59380b5e85c0925c4c76d9064d2f02",
    "stack": []
}
```