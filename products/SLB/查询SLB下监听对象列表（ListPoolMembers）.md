## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/listener/pool/member/list`

请求方法：POST

## 输入参数

| 参数名称  | 必选 | 类型                    | 描述                          |
| --------- | ---- | ----------------------- | ----------------------------- |
| regionId  | 是   | string                  | 地域id                        |
| start     | 是   | int                     | 查询EIP列表起始index，从0开始 |
| limit     | 是   | int                     | 查询EIP列表元素数量           |
| condition | 是   | [Condition](#Condition) | 查询EIP条件                   |

<span id="Condition"></span>
SLBCondition:

| 参数名称 | 必选 | 类型   | 描述                         |
| -------- | ---- | ------ | ---------------------------- |
| poolUuid | 是   | string | 查询指定资源池下Member的列表 |

## 输出参数

| 参数名称  | 类型                     | 描述         |
| --------- | ------------------------ | ------------ |
| errno     | int                      | 错误码       |
| errmsg    | string                   | 请求错误说明 |
| requestId | string                   | 请求唯一标识 |
| data      | array<[Member](#Member)> | 请求返回数据 |

<span id="Member"></span>
Member：

| 参数名称          | 类型   | 描述               |
| ----------------- | ------ | ------------------ |
| slbMemberUuid     | string | member的UUID       |
| healthState       | string | unhealth表示不健康 |
| unhealthyDuration | int    | 不健康时长         |
| port              | int    | 端口               |
| weight            | int    | 权重               |
| createTime        | int  | 创建时间           |
| updateTime        | int  | 更新时间           |
| dc2               | [DC2](#DC2)    | member对应的DC2    |

<span id="DC2"></span>
DC2:

| 参数名称   | 类型   | 描述        |
| ---------- | ------ | ----------- |
| dc2Uuid    | bool   | dc2Uuid     |
| name       | bool   | dc2名称     |
| ip         | string | dc2的内网ip |
| createTime | int    |             |
| updateTime | int    |             |



## 错误码

| 错误码 | 说明                |
| ------ | ------------------- |
| 0      | 请求成功            |
| 41072  | 查询SLB监听对象失败 |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/network/slb/listener/pool/member/list' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
	"regionId":"pre",
    "start": 0,
    "limit": 10,
    "simplify": false,
    "condition": {
        "poolUuid": "a416efe9282b4b05b84e620040483921"
    }
}'

输出：
{
    "data": [
        {
            "createTime": 1585708280000,
            "dc2": {
                "createTime": 1585647253000,
                "dc2Id": "dc2-gumedcq3",
                "dc2Project": "DefaultProject",
                "dc2ProjectId": "project-r614cxbvi4",
                "dc2Tags": [
                    "包月资源升配"
                ],
                "dc2Uuid": "b4395a390f1e54b19b75df7a6a078671",
                "ip": "10.254.1.66",
                "name": "测试",
                "updateTime": 1585648091000
            },
            "healthState": "unhealth",
            "port": 80,
            "slbMemberId": "pm-79y11fz2",
            "slbMemberTags": [],
            "slbMemberUuid": "89607a0c02b940c79d351bfff643c8e4",
            "unhealthyDuration": 116991,
            "updateTime": 1585708280000,
            "weight": 100
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59380b5e85c5fd53c576cf068d4702"
}
```