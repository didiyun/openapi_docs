## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/w/continueList`

请求方法：POST

## 输入参数
|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| start | 是 | int |  查询资源列表起始index，从0开始  |
| limit | 是 | int | 查询资源列表元素数量  |
| condition | 是 | [ContinueListCondition](#ContinueListCondition) |是否是更改规格操作 |

<span id="ContinueListCondition"></span>
ContinueListCondition:

| 操作类型 | 必选 |类型 |描述  |
|------|-----|-----| ----- |
| startTime | 否 | int64 |筛选在此时间之后到期的资源，单位为毫秒时间戳 | 
| endTime | 否 | int64 |筛选在此时间之前到期的资源，单位为毫秒时间戳 |
| resourceType | 否 | string | 筛选此资源类型，不传则显示全部 |
| regionId | 否 | string | 筛选此地域下的资源 |
| autoRenewFilter | 否 | string | 到期前是否自动续费筛选，不传或传空表示显示所有，"enabled"表示查看已开通自动续费的资源，"disabled"表示查看未开通的 |

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | [ContinueListResponse](#ContinueListResponse)	 | 请求返回数据 | 

<span id="ContinueListResponse"></span>
ContinueListResponse:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| continueList | array<[ContinueListData](#ContinueListData)> | 待续费资源列表 |
| total | int | 资源总量 |

<span id="ContinueListData"></span>
ContinueListData:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| resourceType   | string | 资源类型 |
| resourceUuid    | string | 资源uuid |
| name     | string | 资源名称 |
| regionId    | string | 资源所在区域 |
| endTime    | int64 | 资源到期时间，单位毫秒时间戳 |
| autoRenewCnt | int | 资源到期前是否自动续费，为0表示不续费，大于0表示一次续费月数 |
| autoSwitch | bool | 资源到期时策略：当autoRenewCnt为0，如果autoSwitch为true，表示资源到期后自动转为按时长计费，为false表示到期删除；如果autoRenewCnt大于0，该参数无意义 |
| spec     |  [ResourceSpec](/static/docs-content/products/通用响应结构.md#ResourceSpec)  | 资源的规格信息，不同资源对应的信息结构可参考[资源规格相关](/static/docs-content/products/通用响应结构.md#ResourceSpec)项 |
| bindingResources | array<[ResourceItemOutput](#ResourceItemOutput)> | 此资源上绑定的资源，如EIP，数据盘EBS等，强绑定的资源（如系统盘EBS）信息不包含在内 |

<span id="ResourceItemOutput"></span>
ResourceItemOutput:

|参数名称  | 类型 | 描述 |
| -------- | ----- | ----- |
| resourceType   | string | 资源类型 |
| resourceUuid    | string | 资源uuid |
| spec     | [ResourceSpec](/static/docs-content/products/通用响应结构.md#ResourceSpec)  | 资源的规格信息，不同资源对应的信息结构可参考[资源规格相关](/static/docs-content/products/通用响应结构.md#ResourceSpec)项 |


## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST \
  https://open.didiyunapi.com/dicloud/w/continueList \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' 
  -H 'content-type: application/json' \
  -d '{
	"start":0,
	"limit":10,
	"condition":{}
}'
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": {
        "continueList": [
            {
                "autoSwitch": false,
                "autoRenewCnt": 1,
                "bindingResources": [
                    {
                        "resourceType": "eip",
                        "resourceUuid": "2a84e7317d235aa9a60da460bc65e102",
                        "spec": {
                            "bandwidth": 1024,
                            "chargeType": "bandwidth",
                            "inboundBandwidth": 1024,
                            "name": "eip-with-1M-bandwidth",
                            "offeringUuid": "35f588654ed44c13a4cfebaf1470549b",
                            "outboundBandwidth": 1024,
                            "peerOfferingUuid": "bac92fe5275f47f8aa03b795c43bd2ca",
                            "uuid": "35f588654ed44c13a4cfebaf1470549b"
                        }
                    }
                ],
                "endTime": 1543044423000,
                "name": "CentOS7.4-1G-1M",
                "regionId": "gz",
                "resourceType": "dc2",
                "resourceUuid": "953777262c9e5bd48d1a5379ca220811",
                "spec": {
                    "cpuModel": 79,
                    "cpuNum": 1,
                    "cpuSpeed": 1,
                    "diskSize": 21474836480,
                    "diskType": "SSD",
                    "gpuDeviceOfferingUuid": "",
                    "gpuNum": 0,
                    "instanceOfferingUuid": "7ff66afe78a442fcbda81e90dd74ab5f",
                    "memorySize": 1073741824,
                    "model": "dc2.s1.small1.d20",
                    "name": "1CPU-1GMEM-20GDISK",
                    "offeringUuid": "c5ac494a0c28d2c9195dc67bba5d9e4f",
                    "rootDiskOfferingUuid": "c8c1e998e772426eb0bf38af8b0ba1b4",
                    "type": "local.ssd"
                }
            }
        ],
        "total": 5
    },
    "requestId": "0a60538a5bd03c76bf4e0cc7f0987db0"
}
```
