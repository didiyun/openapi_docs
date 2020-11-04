## 接口描述

请求路径：`https://open.didiyunapi.com/dicloud/i/storage/cimg/list`

请求方法：POST

## 输入参数

| 参数名称  | 必选 | 类型                            | 描述                 |
| --------- | ---- | ------------------------------- | -------------------- |
| regionId  | 是   | string                          | 地域id               |
| start     | 是   | int                             | 查询SLB列表起始index |
| limit     | 是   | int                             | 每页个数             |
| condition | 否   | [CIMGCondition](#CIMGCondition) | 查询EIP条件          |

<span id="CIMGCondition"></span>
CIMGCondition:

| 参数名称 | 必选 | 类型              | 描述                     |
| -------- | ---- | ----------------- | ------------------------ |
| names    | 否   | array&lt;string\> | 查询的镜像的名称匹配集合 |

## 输出参数

| 参数名称  | 类型                                 | 描述         |
| --------- | ------------------------------------ | ------------ |
| errno     | int                                  | 错误码       |
| errmsg    | string                               | 请求错误说明 |
| requestId | string                               | 请求唯一标识 |
| data      | array<[CIMGResponse](#CIMGResponse)> | 请求返回数据 |

<span id="CIMGResponse"></span>
CIMGResponse：

| 参数名称    | 类型                                                     | 描述                                           |
| ----------- | -------------------------------------------------------- | ---------------------------------------------- |
| job         | [Job](/static/docs-content/products/通用响应结构.md#Job) | 此镜像正在进行的任务，若无任务则没有此字段     |
| cimgUuid    | string                                                   | 镜像唯一标识                                   |
| name        | string                                                   | 镜像名称                                       |
| createTime  | int                                                      | 创建时间                                       |
| isShared    | bool                                                     | 是否是被分享的镜像（如果为true则不可进行复制） |
| regions     | array\<string\>                                          | 镜像所在的region列表                           |
| description | string                                                   | 镜像描述                                       |
| status      | string                                                   | 镜像状态                                       |
| osFamily    | string                                                   | 系统类型                                       |
| osVersion   | string                                                   | 系统版本                                       |
| platform    | string                                                   | 系统平台                                       |
| size        | int                                                      | 镜像大小                                       |

## 错误码

| 错误码 | 说明     |
| ------ | -------- |
| 0      | 请求成功 |

## 示例

```
请求：
curl --location --request POST 'https://open.didiyunapi.com/dicloud/i/storage/cimg/list' \
--header 'Authorization: Bearer b557cb1ac87055909e82f19c119f88c83e9648e891395f00950c713a239ecd92' \
--header 'Content-Type: application/json' \
--data-raw '{
    "regionId":"bj",
    "limit":1,
    "condition":{
        "names":["北京02"]
    }
}'
输出：
{
    "data": {
        "count": 1,
        "items": [
            {
                "backupStorages": [
                    {
                        "bsUuid": "257ec36487cd4c36be2e2883b0363e97",
                        "diskType": "HE",
                        "name": "ceph-bj01-he",
                        "state": "Enabled",
                        "status": "Connected",
                        "type": "Ceph",
                        "zone": "BJ01"
                    },
                    {
                        "bsUuid": "c1e6b5a214f5400082a55ad16fe4d005",
                        "diskType": "SSD",
                        "name": "S3-Backup-Storage",
                        "state": "Enabled",
                        "status": "Connected",
                        "type": "LocalStorage",
                        "zone": "BJ01"
                    },
                    {
                        "bsUuid": "f51da6e463cb45cd81393a1d21198f18",
                        "diskType": "SSD",
                        "name": "ceph-bj01-ssd",
                        "state": "Enabled",
                        "status": "Connected",
                        "type": "Ceph",
                        "zone": "BJ01"
                    }
                ],
                "checkState": "uncheck",
                "cimgId": "cimg-cy58anir",
                "cimgTags": [],
                "cimgUuid": "4a48f88391134a01befe88ff98b68a88",
                "createTime": 1603799470000,
                "description": "",
                "isExternal": true,
                "isShared": false,
                "name": "北京02",
                "osArch": "64bit",
                "osFamily": "CentOS",
                "osVersion": "7",
                "platform": "Linux",
                "regions": [
                    "bj"
                ],
                "requirement": {
                    "minDiskSize": 8589934592
                },
                "scenes": [
                    "base"
                ],
                "size": 549899264,
                "status": "Ready",
                "type": "custom",
                "updateTime": 1603799470000,
                "zones": [
                    "bj01"
                ]
            }
        ]
    },
    "errmsg": "ok",
    "errno": 0,
    "requestId": "0a59221f5fa0daae2e3b3230033d4602"
}
```