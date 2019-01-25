## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/network/vpc/cidr`

请求方法：GET
## 输入参数
无

## 输出参数
|参数名称  | 类型 | 描述|
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明	|
|requestId |string|请求唯一标识 |
|data | array<[VPCAvailableCidr](#VPCAvailableCidr)>	 | 请求返回数据 | 

<span id="VPCAvailableCidr"></span>
VPCAvailableCidr：

|参数名称  | 类型 | 描述|
|--------|-----|-----|
| availableCidr   |  array&lt;string&gt;  | VPC可用网段  |



## 错误码
| 错误码 | 说明    |
|-------|---------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X GET https://open.didiyunapi.com/dicloud/i/network/vpc/cidr \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' 
输出：
{
    "errno": 0,
    "errmsg": "ok",
    "data": [
        {
            "availableCidr": [
                "10.0.0.0/8",
                "172.16.0.0/12",
                "192.168.0.0/16"
            ]
        }
    ],
    "requestId": "0a60538a5bd12c6a885c5c80854896b0"
}
```