本节汇总了滴滴云目前所有可调用API，具体接口信息请参阅相关文档。

## 通用接口

|接口名称|接口功能|
|-------|-------|
| [JobResult](/static/docs-content/products/通用接口/获取异步任务进度（JobResult）.md) | 查看异步任务进度 |
| [ListRegionAndZone](/static/docs-content/products/通用接口/获取当前产品所支持的区域信息（ListRegionAndZone）.md) | 获取当前产品所支持的区域信息 |
| [GetChargeInfoAndSpec](/static/docs-content/products/通用接口/获取资源的计费信息与规格信息（GetChargeInfoAndSpec）.md) | 获取资源的计费信息与规格信息 |

## 支付相关接口

|接口名称|接口功能|
|-------|-------|
| [CheckPrice](/static/docs-content/products/支付接口/询价（CheckPrice）.md) | 询价，获取当前预购买商品的价格等信息 |
| [ContinueList](/static/docs-content/products/支付接口/获取待续费包月资源列表（ContinueList）.md) | 获取当前待续费的包月资源列表 |
| [ContinueMonthly](/static/docs-content/products/支付接口/批量续费包月资源（ContinueMonthly）.md) | 批量包月续费资源 |
| [ChangeToMonthly](/static/docs-content/products/支付接口/批量将按时长资源转为包月（ChangeToMonthly）.md) | 批量将按时长资源转为包月 |
| [ChangeExpireStrategy](/static/docs-content/products/支付接口/更改资源到期策略（ChangeExpireStrategy）.md) | 更改包月到期资源策略 |

## DC2相关接口

|接口名称|接口功能|
|-------|-------|
| [ListDC2](/static/docs-content/products/DC2/查询DC2实例列表（ListDC2）.md)| 查看DC2实例列表 |
| [GetDC2ByUuid](/static/docs-content/products/DC2/获取DC2详情（GetDC2ByUuid）.md)| 获取DC2详情 |
| [GetDC2TotalCnt](/static/docs-content/products/DC2/获取DC2总量（GetDC2TotalCnt）.md)| 查询DC2的总量 |
| [CreateDC2](/static/docs-content/products/DC2/创建DC2（CreateDC2）.md)| 创建DC2 |
| [DeleteDC2](/static/docs-content/products/DC2/删除DC2（DeleteDC2）.md)| 删除DC2 |
| [StartDC2](/static/docs-content/products/DC2/启动DC2（StartDC2）.md)| 启动DC2 |
| [StopDC2](/static/docs-content/products/DC2/关闭DC2（StopDC2）.md)| 关闭DC2 |
| [RebootDC2](/static/docs-content/products/DC2/重启DC2（RebootDC2）.md)| 重启DC2 |
| [ReinstallDC2System](/static/docs-content/products/DC2/重装DC2系统（ReinstallDC2System）.md)| 重装DC2系统 |
| [ChangeDC2Password](/static/docs-content/products/DC2/更改DC2密码（ChangeDC2Password）.md)| 更改DC2密码 |
| [ChangeDC2Name](/static/docs-content/products/DC2/更改DC2名字（ChangeDC2Name）.md)| 更改DC2名字 |
| [ChangeDC2Spec](/static/docs-content/products/DC2/更改DC2配置（ChangeDC2Spec）.md)| 更改DC2配置 |
| [ListImage](/static/docs-content/products/DC2/查看镜像列表（ListImage）.md)| 查看镜像列表 |
| [ListSSHKeys](/static/docs-content/products/DC2/查询公钥列表（ListSSHKeys）.md)| 查看公钥列表 |
| [CreateSSHKeys](/static/docs-content/products/DC2/添加公钥（CreateSSHKeys）.md)| 添加公钥 |
| [DeleteSSHKeys](/static/docs-content/products/DC2/删除公钥（DeleteSSHKeys）.md)| 删除公钥 |

## EIP相关接口
| 接口名称 | 接口功能 |
|-------|-------|
| [ListEIP](/static/docs-content/products/EIP/查询EIP实例列表（ListEIP）.md)| 查看EIP实例列表 |
| [GetEIPByUuid](/static/docs-content/products/EIP/根据EIP的Uuid查询EIP信息（GetEIPByUuid）.md)| 根据EIP的Uuid查询EIP信息 |
| [GetEIPTotalCnt](/static/docs-content/products/EIP/获取EIP总量（GetEIPTotalCnt）.md)| 查询EIP的总量 |
| [CreateEIP](/static/docs-content/products/EIP/创建EIP实例（CreateEIP）.md)| 创建EIP实例 |
| [DetachEIPFromDC2](/static/docs-content/products/EIP/解绑EIP实例与DC2实例（DetachEIPFromDC2）.md)| 解绑EIP实例 |
| [AttachEIPToDC2](/static/docs-content/products/EIP/绑定EIP实例到DC2实例（AttachEIPToDC2）.md)| 绑定EIP实例 |
| [DeleteEIP](/static/docs-content/products/EIP/删除EIP实例（DeleteEIP）.md)| 删除EIP实例 |
| [ChangeEIPBandwidth](/static/docs-content/products/EIP/更改EIP带宽（ChangeEIPBandwidth）.md)| 更改EIP的带宽规格 |

## EBS相关接口
| 接口名称 | 接口功能 |
| ------- | ------- |
| [ListEBS](/static/docs-content/products/EBS/查询EBS实例列表（ListEBS）.md) | 查看EBS实例列表 |
| [GetEBSByUuid](/static/docs-content/products/EBS/根据EBS的Uuid查询的EBS信息.md) | 根据EBS的Uuid查询EBS信息 |
| [GetEBSTotalCnt](/static/docs-content/products/EBS/查询EBS的总量（GetEBSTotalCnt）.md) | 查询EBS的总量 |
| [CreateEBS](/static/docs-content/products/EBS/创建EBS（CreateEBS）.md) | 创建EBS |
| [DeleteEBS](/static/docs-content/products/EBS/删除EBS（DeleteEBS）.md) | 删除EBS |
| [AttachEBS](/static/docs-content/products/EBS/绑定EBS（AttachEBS）.md) | 绑定EBS |
| [DetachEBS](/static/docs-content/products/EBS/解绑EBS（DetachEBS）.md) | 解绑EBS |
| [ChangeEBSName](/static/docs-content/products/EBS/更改EBS名称（ChangeEBSName）.md) | 更改EBS名称 |
| [ChangeEBSSize](/static/docs-content/products/EBS/更改EBS大小（ChangeEBSSize）.md) | 更改EBS大小 |

## SNAP相关接口
| 接口名称 | 接口功能 |
| ------- | ------- |
| [ListSNAP](/static/docs-content/products/SNAP/查询快照列表（ListSNAP）.md) | 查看快照列表 |
| [GetSNAPTotalCnt](/static/docs-content/products/SNAP/查询快照数量（GetSNAPTotalCnt）.md) | 查询快照数量 |
| [CreateSNAP](/static/docs-content/products/SNAP/根据DC2或EBS创建快照（CreateSNAP）.md) | 根据DC2/EBS创建快照 |
| [DeleteSNAP](/static/docs-content/products/SNAP/删除快照（DeleteSNAP）.md) | 删除快照 |
| [RevertSNAP](/static/docs-content/products/SNAP/通过快照还原源盘（RevertSNAP）.md) | 通过快照还原源盘 |
| [ChangeSnapshotName](/static/docs-content/products/SNAP/更改快照名称（ChangeSNAPName）.md) | 更改快照名称 |

## VPC相关接口

| 接口名称 | 接口功能 |
| ------- | ------- |
| [ListVPC](/static/docs-content/products/VPC/查询VPC列表（ListVPC）.md) | 查看VPC列表 |
| [GetVPCByUuid](/static/docs-content/products/VPC/查询VPC详情（GetVPCByUuid）.md) | 根据VPC的uuid获取VPC详情 |
| [GetVPCTotalCnt](/static/docs-content/products/VPC/获取VPC总量（GetVPCTotalCnt）.md) | 查询VPC数量 |
| [CreateVPC](/static/docs-content/products/VPC/创建VPC（CreateVPC）.md) | 创建VPC |
| [DeleteVPC](/static/docs-content/products/VPC/删除VPC（DeleteVPC）.md) | 删除VPC |
| [ChangeVPCName](/static/docs-content/products/VPC/更改VPC名称（ChangeVPCName）.md) | 更改VPC名称 |
| [ListVPCAvailableCidr](/static/docs-content/products/VPC/获取VPC可用网段（ListVPCAvailableCidr）.md) | 查看VPC可用网段 |
| [ListSUBNET](/static/docs-content/products/VPC/查询SUBNET列表（ListSUBNET）.md) | 查看SUBNET列表 |
| [GetSUBNETByUuid](/static/docs-content/products/VPC/查询SUBNET详情（GetSUBNETByUuid）.md) | 根据SUBNET的uuid获取SUBNET详情 |
| [GetSUBNETTotalCnt](/static/docs-content/products/VPC/获取SUBNET总量（GetSUBNETTotalCnt）.md) | 查询SUBNET数量 |
| [CreateSUBNET](/static/docs-content/products/VPC/创建SUBNET（CreateSUBNET）.md) | 创建SUBNET |
| [DeleteSUBNET](/static/docs-content/products/VPC/删除SUBNET（DeleteSUBNET）.md) | 删除SUBNET |
| [ChangeSUBNETName](/static/docs-content/products/VPC/更改SUBNET名称（ChangeSUBNETName）.md) | 更改SUBNET名称 |
| [CheckSubnetCidrOverlap](/static/docs-content/products/VPC/查看指定VPC下是否有与指定网段重叠的SUBNET（CheckSUBNETCidrOverlap）.md) | 查看指定VPC下是否有与指定网段重叠的SUBNET |

## SG相关接口
| 接口名称 | 接口功能 |
| ------- | ------- |
| [ListSG](/static/docs-content/products/SG/查询SG列表（ListSG）.md) | 查询SG列表 |
| [GetSGTotalCnt](/static/docs-content/products/SG/获取SG总量（GetSGTotalCnt）.md) | 获取SG总量 |
| [CreateSG](/static/docs-content/products/SG/创建SG（CreateSG）.md) | 创建SG |
| [DeleteSG](/static/docs-content/products/SG/删除SG（DeleteSG）.md) | 删除SG |
| [ChangeSGName](/static/docs-content/products/SG/更改SG名称（ChangeSGName）.md) | 更改SG名称 |
| [AttachDC2ToSG](/static/docs-content/products/SG/绑定DC2到SG（AttachDC2ToSG）.md) | 绑定DC2到SG |
| [DetachDC2FromSG](/static/docs-content/products/SG/从SG解绑DC2（DetachDC2FromSG）.md) | 绑定DC2到SG |
| [ListSGRule](/static/docs-content/products/SG/查询SGRule列表（ListSGRule）.md) | 查看SG下的规则列表 |
| [GetSGRuleTotalCnt](/static/docs-content/products/SG/获取SGRule总量（GetSGRuleTotalCnt）.md) | 获取SG下的规则总量 |
| [CreateSGRule](/static/docs-content/products/SG/创建SGRule（CreateSGRule）.md) | 创建SG规则 |
| [DeleteSGRule](/static/docs-content/products/SG/删除SGRule（DeleteSGRule）.md) | 删除SG规则 |
