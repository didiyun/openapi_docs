## 接口描述
请求路径：`https://open.didiyunapi.com/dicloud/i/compute/dc2/assign`

请求方法：POST
## 输入参数
<span id="CreateDC2Params"></span>
CreateDC2Params:

|参数名称 | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| regionId | 是 | string | 地域id |
| zoneId | 否 | string | 可用区id，在何可用区创建此DC2，**不传subnetUuid参数时必传** |
| autoContinue      | 否 |   bool    |   是否设置DC2自动续费          |
| payPeriod | 否 | int | 购买包月时长，单位为月，不传或传0表示后付费 |
| count | 否 | int | 批量购买参数，不传默认购买一台DC2，不能超过20 |
| couponId | 否 | string | 本次创建使用的优惠券id |
| subnetUuid     | 否 |   string  |   在此指定子网下创建DC2，**不传zoneId参数时必传。如果未传，则会在目标地域的默认VPC下对应可用区的默认子网中创建DC2**  |
| dc2Model | 是 | string | 要创建的dc2型号 [常用的DC2型号列表](#Dc2Models) |
| imgUuid    | 是 |   string   |   使用何镜像创建DC2，与snapUuid二选一  |
| snapUuid  | 是 |   string  |   使用何快照创建DC2，与imgUuid二选一。**注意：使用快照创建DC2时，通用型DC2与本地型DC2的快照不可互通。关于DC2型号信息可参阅**[常用的DC2型号列表](#Dc2Models)  |
| pubKeyUuids   | 是 |   array&lt;string&gt;           |   使用公钥Uuid列表进行DC2创建，与password参数二选一。**注意：Windows实例不支持公钥创建** |
| password | 是 | string | 使用密码进行创建，需将原密码进行16进制编码传递，与pubKeyUuids参数二选一 |
| rootDiskSize | 是 | int | 根盘大小，单位GB，**当所选规格族为通用型（e1,g1,g2）时需要传递，需大于等于40，且小于等于500** |
| rootDiskType | 是 | string | 根盘类型（"HDD"、"SSD"或"HE"），**当所选规格族为通用型（e1,g1,g2）时需要传递** |
| dc2Tags | 否 | array&lt;string&gt; |  DC2标签  |
| name      | 否 |   string         |   DC2名字   |
| proSecurityAgentEnabled | 否 |bool | 是否同时安装主机安全Agent专业版 |
| monitoringAgentEnabled | 否 |bool | 是否同时安装监控Agent |
| sgUuids        | 否 |   array&lt;string&gt;         |   此DC2将要加入的安全组列表   |
| eip  | 否 |   [EIPInput](#EIPInput)        |   同时创建的EIP信息   |
| ebs | 否 | array<[EBSInput](#EBSInput)> | 同时创建的EBS信息 |

<span id="EIPInput"></span>
EIPInput：

|参数名称  | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
|bandwidth	 | 是 | int  |EIP的带宽，为1-100之间的值   |
|chargeWithFlow |否 | bool  | 是否要按流量计费 （为按流量计费时，默认为后付费）  |
|eipTags  | 否|  array&lt;string&gt;    | EIP标签    |

<span id="EBSInput"></span>
EBSInput：

|参数名称  | 必选 | 类型 | 描述|
|--------|-----|-----|-----|
| count   | 否 | int | 批量购买参数，不传默认购买一块EBS，不能超过5 |
| name     | 否 |string   | 创建的EBS名称 |
| size     | 是 |int64    | 创建的EBS大小，单位GB，需大于等于20，并小于等于16384 |
| diskType | 是 |string   | 创建的EBS类型（"HDD"或"SSD"）|
| snapUuid | 否 |string   | 通过此快照创建EBS |
| ebsTags   | 否 |  array&lt;string&gt; | EBS标签 |


<span id="Dc2Models"></span>
## 常用DC2型号列表（DC2Model）

DC2的型号是创建、管理DC2的必要参数之一，常用的DC2型号如下：

<table>
<tr>
	<th> 类型/族群 </th>
	<th> CPU数量</th>
	<th>内存大小（GB）</th>
	<th>磁盘大小（GB）</th>
	<th>GPU数量</th>
	<th>GPU型号</th>
	<th>型号</th>
</tr>
<tr>
	<td rowspan="10" >本地SSD型（s1）</td>
	<td> 1</td>
	<td> 1</td>
	<td> 20</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.small1.d20</td>
</tr>
<tr>
	<td> 1</td>
	<td> 2</td>
	<td> 40</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.small2.d40</td>
</tr>
<tr>
	<td> 2</td>
	<td> 4</td>
	<td> 40</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.large4.d40</td>
</tr>
<tr>
	<td> 2</td>
	<td> 4</td>
	<td> 80</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.large4.d80</td>
</tr>
<tr>
	<td> 4</td>
	<td> 8</td>
	<td> 80</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.xlarge8.d80</td>
</tr>
<tr>
	<td> 4</td>
	<td> 8</td>
	<td> 160</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.xlarge8.d160</td>
</tr>
<tr>
	<td> 8</td>
	<td> 16</td>
	<td> 240</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.2xlarge16.d240</td>
</tr>
<tr>
	<td> 8</td>
	<td> 16</td>
	<td> 320</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.2xlarge16.d320</td>
</tr>
<tr>
	<td> 16</td>
	<td> 32</td>
	<td> 320</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.4xlarge32.d320</td>
</tr>
<tr>
	<td> 16</td>
	<td> 32</td>
	<td> 480</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.s1.4xlarge32.d480</td>
</tr>
<tr>
	<td rowspan="6" > 通用型（e1）</td>
	<td> 1</td>
	<td> 1</td>
	<td> -</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.e1.small1</td>
</tr>
<tr>
	<td> 1</td>
	<td> 2</td>
	<td> -</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.e1.small2</td>
</tr>
<tr>
	<td> 2</td>
	<td> 4</td>
	<td> -</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.e1.large4</td>
</tr>
<tr>
	<td> 4</td>
	<td> 8</td>
	<td> -</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.e1.xlarge8</td>
</tr>
<tr>
	<td> 8</td>
	<td> 16</td>
	<td> -</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.e1.2xlarge16</td>
</tr>
<tr>
	<td> 16</td>
	<td> 32</td>
	<td> -</td>
	<td> -</td>
	<td> -</td>
	<td> dc2.e1.4xlarge32</td>
</tr>
<tr>
	<td rowspan="4" > 本地型P4（gn1）</td>
	<td> 2</td>
	<td> 4</td>
	<td> 80</td>
	<td> 1</td>
	<td> P4</td>
	<td> dc2.gn1.large4g1.d80</td>
</tr>
<tr>
	<td> 4</td>
	<td> 8</td>
	<td> 160</td>
	<td> 1</td>
	<td> P4</td>
	<td> dc2.gn1.xlarge8g1.d160</td>
</tr>
<tr>
	<td> 8</td>
	<td> 16</td>
	<td> 320</td>
	<td> 1</td>
	<td> P4</td>
	<td> dc2.gn1.2xlarge16g1.d320</td>
</tr>
<tr>
	<td> 16</td>
	<td> 32</td>
	<td> 320</td>
	<td> 1</td>
	<td> P4</td>
	<td> dc2.gn1.4xlarge32g1.d480</td>
</tr>
<tr>
	<td rowspan="4" > 通用型P4（g1）</td>
	<td> 2</td>
	<td> 4</td>
	<td> -</td>
	<td> 1</td>
	<td> P4</td>
	<td> dc2.g1.large4g1</td>
</tr>
<tr>
	<td> 4</td>
	<td> 8</td>
	<td> -</td>
	<td> 1</td>
	<td> P4</td>
	<td> dc2.g1.xlarge8g1</td>
</tr>
<tr>
	<td> 8</td>
	<td> 16</td>
	<td> -</td>
	<td> 1</td>
	<td> P4</td>
	<td> dc2.g1.2xlarge16g1</td>
</tr>
<tr>
	<td> 16</td>
	<td> 32</td>
	<td> -</td>
	<td> 1</td>
	<td> P4</td>
	<td> dc2.g1.4xlarge32g1</td>
</tr>

</table>

## 输出参数
|参数名称  | 类型 | 描述 |
|--------|-----|-----|
|errno | int  |错误码 |
|errmsg|string|请求错误说明   |
|requestId |string|请求唯一标识 |
|data | array<[Job](/static/docs-content/products/通用响应结构.md#Job)>   | 请求返回数据| 

## 错误码
|错误码 | 说明    |
|------|--------|
| 0    | 请求成功  |

## 示例

```
请求：
curl -X POST https://open.didiyunapi.com/dicloud/i/compute/dc2/assign \
  -H 'authorization: Bearer 9a609744ad675e8fbfcdbf14511b24e6ddd6b427b4d256969534a81d0773f4d7' \
  -H 'content-type: application/json' \
  -d '{
	"regionId":"gz",
	"name":"test",
	"imgUuid":"46b447a8b0a146779bbde3ca40e56843",
	"dc2Model":"dc2.s1.small1.d20",
	"password":"53746d333137303234",
	"subnetUuid":"f2513581ccd048dc9d0ccec32114b7cd",
	"eip":{
		"bandwidth":1,
		"tags":["testeip"]
	},
	"ebs":[{
		"size":20,
		"diskType":"SSD"
	}],
	"tags":["testdc2"]
}'

输出：
{
	"errno": 0,
	"errmsg": "ok",
	"data": [
		{
			"done": false,
			"jobUuid": "c572fb9bd52e5e70874bc0b3b0451106",
			"progress": 0,
			"success": false,
			"type": "CreateDC2"
		}
	],
	"requestId": "0a60538a5bc59a824f129a79b71d40b0"
}
```
