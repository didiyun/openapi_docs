## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/listener/update`

请求方法：POST

## 输入参数

| 参数名称    | 必选 | 类型                           | 描述 |
| ----------- | ---- | ------------------------------ | ---- |
| slbListener | 是   | array\<[Listener](#Listener)\> |      |



<span id="Listener"></span>
Listener:

| 参数名称        | 必选 | 类型                            | 描述            |
| --------------- | ---- | ------------------------------- | --------------- |
| slbListenerUuid | 是   | string                          | 待更新的UUID    |
| name            | 是   | string                          | Listener名称    |
| algorithm       | 是   | string                          | 算法名称        |
| protocol        | 是   | string                          | 监听协议        |
| listenerPort    | 是   | int                             | 监听的Port      |
| backProtocol    | 是   | string                          | 转发协议        |
| healthMonitor   | 是   | [HealthMonitor](#HealthMonitor) | healMonitor信息 |



<span id="HealthMonitor"></span>
HealthMonitor:

| 参数名称           | 必选 | 类型   | 描述       |
| ------------------ | ---- | ------ | ---------- |
| protocol           | 是   | string | 协议       |
| interval` `        | 是   | int    | 检查间隔   |
| timeout            | 是   | int    | 超时时间   |
| healthyThreshold   | 是   | int    | 健康阈值   |
| unhealthyThreshold | 是   | int    | 不健康阈值 |

## 输出参数

| 参数名称  | 类型                                                         | 描述         |
| --------- | ------------------------------------------------------------ | ------------ |
| errno     | int                                                          | 错误码       |
| errmsg    | string                                                       | 请求错误说明 |
| requestId | string                                                       | 请求唯一标识 |
| data      | array\<[Job](/static/docs-content/products/通用响应结构.md#Job)\> | job信息      |


## 错误码

| 错误码 | 说明     |
| ------ | -------- |
| 0      | 请求成功 |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/listener/update' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "slbListener": [
        {
            "algorithm": "minconn",
            "backProtocol": "TCP",
            "createTime": 1585826468000,
            "healthStatus": {
                "healthyMemberCnt": 0,
                "totalMemberCnt": 1
            },
            "listenerPort": 81,
            "memberPorts": [
                8080
            ],
            "monitor": {
                "healthyThreshold": 3,
                "interval": 15,
                "protocol": "TCP",
                "slbHealthMonitorUuid": "fae38beaaaff4fbf9c5f5c5d1a39dafc",
                "timeout": 5,
                "unhealthyThreshold": 3
            },
            "name": "test",
            "poolUuid": "669d6b7b23a0417ebdfd4e382298bf9e",
            "protocol": "TCP",
            "slbListenerId": "slbl-os4scyij",
            "slbListenerTags": [],
            "slbListenerUuid": "9b41e8a1f80f5a728bc9f40151ecd5e5",
            "updateTime": 1585826468000,
            "edit": true
        }
    ]
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "669784316dc954e1b48883b06ff0b0f9",
            "progress": 0,
            "resourceUuid": "9b41e8a1f80f5a728bc9f40151ecd5e5",
            "success": false,
            "type": "UpdateSLBLoadBalancerListener",
            "uuid": ""
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59253c5e85cded0e516a56068bbe02"
}
```