## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/network/slb/create`

请求方法：POST

## 输入参数

<span id="Request"></span>
Request:

| 参数名称                    | 必选 | 类型                | 描述                                          |
| --------------------------- | ---- | ------------------- | --------------------------------------------- |
| regionId                    | 是   | string              | 地域id                                        |
| zoneId                      | 是   | string              | 可用区id，在何可用区创建EBS实例               |
| autoContinue                | 是   | bool                | 是否设置EBS自动续费                           |
| payPeriod                   | 是   | int                 | 购买包月时长，单位为月，不传或传0表示后付费   |
| count                       | 是   | int                 | 批量购买参数，不传默认购买一台EBS，不能超过20 |
| couponId                    | 否   | string              | 本次操作使用的优惠券id                        |
| name                        | 是   | string              | SLB的名称                                     |
| [v](http://dc2.name/)pcUuid | 是   | string              | SLB所在VPC                                    |
| listeners                   | 否   | array\<Liststener\> | SLB要添加的监听信息                           |

<span id="Liststener"></span>
Liststener:

| 参数名称     | 必选 | 类型                       | 描述            |      |
| ------------ | ---- | -------------------------- | --------------- | ---- |
| name         | 是   | string                     | Listener名称    |      |
| algorithm    | 是   | string                     | 算法名称        |      |
| protocol     | 是   | string                     | 监听协议        |      |
| listenerPort | 是   | int                        | 监听的Port      |      |
| backProtocol | 是   | string                     | 转发协议        |      |
| monitor      | 是   | [Monitor](#Monitor)        | healMonitor信息 |      |
| members      | 是   | array\<[Member](#Member)\> | 成员信息        |      |

<span id="Monitor"></span>
Monitor:

| 参数名称           | 必选 | 类型   | 描述       |
| ------------------ | ---- | ------ | ---------- |
| protocol           | 是   | string | 协议       |
| interval` `        | 是   | int    | 检查间隔   |
| timeout            | 是   | int    | 超时时间   |
| healthyThreshold   | 是   | int    | 健康阈值   |
| unhealthyThreshold | 是   | int    | 不健康阈值 |

<span id="Member"></span>
Member:

| 参数名称 | 必选 | 类型   | 描述      |
| -------- | ---- | ------ | --------- |
| dc2Uuid  | 是   | string | dc2的Uuid |
| weight   | 是   | int    | 权重      |
| port     | 是   | int    | 端口      |

## 

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
curl --location --request POST 'http://open.didiyunapi.com/dicloud/i/network/slb/create' \
--header 'Authorization: Bearer bf049d6790195956913fef791f041d066727e881532b5e55b5acb1bcfcc14965' \
--header 'Content-Type: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{
    "payPeriod":1,
    "count":3,
    "name": "openapi_test_2",
    "addressType": "internet",
    "vpcUuid": "990f4ef591294df289630586f6d6fb47",
    "autoContinue": true,
    "listeners": [
        {
            "protocol": "TCP",
            "listenerPort": 80,
            "backProtocol": "TCP",
            "memberPort": 80,
            "algorithm": "wrr",
            "monitor": {
                "protocol": "TCP",
                "interval": 10,
                "timeout": 5,
                "healthyThreshold": 3,
                "unhealthyThreshold": 3,
                "httpMethod": "GET"
            },
            "members": [],
            "name": "tttt"
        }
    ],
    "bandwidth": 5
}'
输出：
{
    "data": [
        {
            "done": false,
            "jobUuid": "20528005d1685ef6a788cf916b7e1049",
            "progress": 0,
            "resourceUuid": "397ef267774f5e3fa1b19f9d8e514f54",
            "success": false,
            "type": "CreateSLBLoadBalancer",
            "uuid": ""
        },
        {
            "done": false,
            "jobUuid": "8354f82330bc579784b6c4a1be5ac8b7",
            "progress": 0,
            "resourceUuid": "83603501b37e5bce920b65d1a8e9acdd",
            "success": false,
            "type": "CreateSLBLoadBalancer",
            "uuid": ""
        },
        {
            "done": false,
            "jobUuid": "0766f19353345c15be816a06e2164575",
            "progress": 0,
            "resourceUuid": "e3991e4b2c8f5ef8bb1da7baaf5e1633",
            "success": false,
            "type": "CreateSLBLoadBalancer",
            "uuid": ""
        }
    ],
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0ab335b85e85d369fee1a03ce40831b0",
    "stack": []
}
```