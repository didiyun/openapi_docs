## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/listener/list`

请求方法：POST

## 输入参数

| 参数名称  | 必选 | 类型                          | 描述                          |
| --------- | ---- | ----------------------------- | ----------------------------- |
| regionId  | 是   | string                        | 地域id                        |
| start     | 是   | int                           | 查询EIP列表起始index，从0开始 |
| limit     | 是   | int                           | 查询EIP列表元素数量           |
| condition | 否   | [SLBCondition](#SLBCondition) | 查询EIP条件                   |

<span id="EIPCondition"></span>
SLBCondition:

| 参数名称 | 必选 | 类型                | 描述                       |
| -------- | ---- | ------------------- | -------------------------- |
| slbUuids | 否   | array\<string\> | 查询的EIP查询指定slb的列表 |

## 输出参数

| 参数名称  | 类型                                       | 描述         |
| --------- | ------------------------------------------ | ------------ |
| errno     | int                                        | 错误码       |
| errmsg    | string                                     | 请求错误说明 |
| requestId | string                                     | 请求唯一标识 |
| data      | array\<[ListnerResponse](#ListnerResponse)\> | 请求返回数据 |

<span id="ListnerResponse"></span>
ListnerResponse：

| 参数名称        | 类型                                                     | 描述                                      |
| --------------- | -------------------------------------------------------- | ----------------------------------------- |
| job             | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此EIP正在进行的任务，若无任务则没有此字段 |
| slbListenerUuid | string                                                   | SLBL唯一标识                              |
| protocol        | string                                                   | listener的Protocol                        |
| listenerPort    | int64                                                    | listener的Port                            |
| backProtocol    | string                                                   | member的Protocol                          |
| memberPorts     | array\<int\>                                             | members的端口集合                         |
| poolUuid        | string                                                   | pool的uuid                                |
| createTime      | int64                                                    | SLBL创建时间                              |
| updateTime      | int64                                                    | SLBL更新时间                              |
| algorithm       | [algorithm](#algorithm)                                  | 负载均衡算法                              |
| healthStatus    | [healthStatus](#healthStatus)                            | 健康情况                                  |
| monitor         | [healthMonitor](#healthMonitor)                          | 健康monitor                               |

<span id="Algorithm"></span>
Algorithm:

| 参数名称 | 类型   | 描述         |
| -------- | ------ | ------------ |
| code     | string | 算法英文code |
| name     | string | 算法中文名   |

<span id="HealthStatus"></span>
HealthStatus:

| 参数名称         | 类型 | 描述           |
| ---------------- | ---- | -------------- |
| healthyMemberCnt | int  | 健康member数量 |
| totalMemberCnt   | int  | member数量     |

<span id="HealthMonitor"></span>
HealthMonitor:

| 参数名称             | 类型   | 描述          |
| -------------------- | ------ | ------------- |
| slbHealthMonitorUuid | string | monitor的Uuid |
| protocol             | string | monitor协议   |
| interval             | int    | 轮训间隔      |
| timeout              | int    | 超时时间      |
| unhealthyThreshold   | int    | 不健康阈值    |
| healthyThreshold     | int    | 健康阈值      |



## 错误码

| 错误码 | 说明             |
| ------ | ---------------- |
| 0      | 请求成功         |
| 41071  | 查询Listener失败 |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/listener/list' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "start": 0,
    "limit": 1000,
    "simplify": false,
    "condition": {
        "slbUuid": "e5a06811a5fa50f2af315f8c9befbc4f"
    }
}'

输出：
{
    "data": [
        {
            "algorithm": {
                "code": "wrr",
                "name": "加权轮询"
            },
            "backProtocol": "TCP",
            "createTime": 1585708281000,
            "healthStatus": {
                "healthyMemberCnt": 0,
                "totalMemberCnt": 1
            },
            "listenerPort": 80,
            "memberPorts": [
                80
            ],
            "monitor": {
                "healthyThreshold": 3,
                "interval": 10,
                "protocol": "TCP",
                "slbHealthMonitorUuid": "e7392ba694634b23b1592ed4f51e2f4f",
                "timeout": 5,
                "unhealthyThreshold": 3
            },
            "name": "test2",
            "poolUuid": "a416efe9282b4b05b84e620040483921",
            "protocol": "TCP",
            "slbListenerId": "slbl-sbaydyg9",
            "slbListenerTags": [],
            "slbListenerUuid": "87528a001ef659c8a494efeb69a794ba",
            "updateTime": 1585708281000
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59922a5e85c759460925a406642002"
}
```
