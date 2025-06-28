---
title: "纳管卷供应StorageClass参数说明"
linkTitle: "纳管卷供应StorageClass参数说明"
description: 
weight: 2
---

[存储类（StorageClass）](https://kubernetes.io/docs/concepts/storage/storage-classes/)为管理员提供了描述存储 "类" 的方法。 不同的类型可能会映射到一组不同的能力定义。Kubernetes集群用户可基于StorageClass进行动态卷制备。

StorageClass支持配置如下参数信息。

使用SAN存储时可参考示例文件/examples/sc-lun.yaml，使用NAS存储时可参考示例文件/examples/sc-fs.yaml。

**表 1**  StorageClass配置参数说明

<a name="zh-cn_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="20.57%" id="mcps1.2.6.1.1"><p id="zh-cn_topic_0000001162111564_p875071122919"><a name="zh-cn_topic_0000001162111564_p875071122919"></a><a name="zh-cn_topic_0000001162111564_p875071122919"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="25.41%" id="mcps1.2.6.1.2"><p id="zh-cn_topic_0000001162111564_p17750131113295"><a name="zh-cn_topic_0000001162111564_p17750131113295"></a><a name="zh-cn_topic_0000001162111564_p17750131113295"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="6.959999999999999%" id="mcps1.2.6.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="9.15%" id="mcps1.2.6.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="37.91%" id="mcps1.2.6.1.5"><p id="zh-cn_topic_0000001162111564_p075011113295"><a name="zh-cn_topic_0000001162111564_p075011113295"></a><a name="zh-cn_topic_0000001162111564_p075011113295"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p4750141111292"><a name="zh-cn_topic_0000001162111564_p4750141111292"></a><a name="zh-cn_topic_0000001162111564_p4750141111292"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p475091120296"><a name="zh-cn_topic_0000001162111564_p475091120296"></a><a name="zh-cn_topic_0000001162111564_p475091120296"></a>自定义的StorageClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001162111564_p861713973915"><a name="zh-cn_topic_0000001162111564_p861713973915"></a><a name="zh-cn_topic_0000001162111564_p861713973915"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p8750161119299"><a name="zh-cn_topic_0000001162111564_p8750161119299"></a><a name="zh-cn_topic_0000001162111564_p8750161119299"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p15750201119295"><a name="zh-cn_topic_0000001162111564_p15750201119295"></a><a name="zh-cn_topic_0000001162111564_p15750201119295"></a>制备器名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>该字段需要指定为安装华为CSI时设置的驱动名。</p>
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>取值和values.yaml文件中driverName一致。</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p119108535312"><a name="p119108535312"></a><a name="p119108535312"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p16910135393118"><a name="p16910135393118"></a><a name="p16910135393118"></a>回收策略。支持如下类型：</p>
<a name="ul5209917195517"></a><a name="ul5209917195517"></a><ul id="ul5209917195517"><li>Delete：自动回收资源。</li><li>Retain：<span>手动回收资源</span>。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li>Delete：删除PV/PVC时会关联删除存储上的资源。</li><li>Retain：删除PV/PVC时不会删除存储上的资源。</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p192771821155012"><a name="p192771821155012"></a><a name="p192771821155012"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p8277132112501"><a name="p8277132112501"></a><a name="p8277132112501"></a>是否允许卷扩展。参数设置为true 时，使用该StorageClass的PV可以进行扩容操作。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p112771521135014"><a name="p112771521135014"></a><a name="p112771521135014"></a>此功能仅可用于扩容PV，不能用于缩容PV。</p>
<p id="p1999211201535"><a name="p1999211201535"></a><a name="p1999211201535"></a>扩容PV功能在Kubernetes <span>1.14 (alpha)后才支持</span>。</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>待创建资源所在的后端名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>如果不设置，华为CSI随机选择一个满足容量要求的后端创建资源。</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>建议指定后端，确保创建的资源在预期的后端上。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p1775061119292"><a name="zh-cn_topic_0000001162111564_p1775061119292"></a><a name="zh-cn_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p975011122920"><a name="zh-cn_topic_0000001162111564_p975011122920"></a><a name="zh-cn_topic_0000001162111564_p975011122920"></a>待创建卷类型。支持如下类型：</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li>lun：存储侧发放的资源是LUN。</li><li>fs：存储侧发放的资源是文件系统。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><a name="ul15360173513251"></a><a name="ul15360173513251"></a><ul id="ul15360173513251"><li>使用NAS存储时，必须配置为fs。</li><li>使用SAN存储时，必须配置为lun。</li></ul>
</td>
</tr>
<tr id="row167642021133711"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p18750171111299"><a name="zh-cn_topic_0000001162111564_p18750171111299"></a><a name="zh-cn_topic_0000001162111564_p18750171111299"></a>parameters.fsType</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p19169191111571"><a name="p19169191111571"></a><a name="p19169191111571"></a>主机文件系统类型。支持类型为：</p>
<a name="ul9614171916576"></a><a name="ul9614171916576"></a><ul id="ul9614171916576"><li>ext2</li><li>ext3</li><li>ext4</li><li>xfs</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p435413852915"><a name="p435413852915"></a><a name="p435413852915"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p9690143918526"><a name="p9690143918526"></a><a name="p9690143918526"></a>ext4</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001162111564_p8750311172910"><a name="zh-cn_topic_0000001162111564_p8750311172910"></a><a name="zh-cn_topic_0000001162111564_p8750311172910"></a>仅当StorageClass的volumeType设置为“lun”，且PVC的volumeMode配置为“Filesystem”时生效。</p>
</td>
</tr>
<tr id="row1175164935614"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p133711471387"><a name="p133711471387"></a><a name="p133711471387"></a>parameters.applicationType</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p153378472388"><a name="p153378472388"></a><a name="p153378472388"></a>后端为OceanStor Dorado存储时，指定创建LUN/NAS时的应用类型名称。</p>
<p id="p15301351175010"><a name="p15301351175010"></a><a name="p15301351175010"></a>后端为OceanDisk存储时，指定创建Namespace时的应用类型名称。</p>
<div class="note" id="note161704482570"><a name="note161704482570"></a><a name="note161704482570"></a><span class="notetitle"> 说明： </span><div class="notebody"><p id="p131701948105720"><a name="p131701948105720"></a><a name="p131701948105720"></a>若卷纳管前已配置应用类型，applicationType必须与已配置的应用类型保持一致。</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p193700711523"><a name="p193700711523"></a><a name="p193700711523"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p8398201010524"><a name="p8398201010524"></a><a name="p8398201010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><a name="ul2082135095716"></a><a name="ul2082135095716"></a><ul id="ul2082135095716"><li>“volumeType”为“lun”时，在DeviceManager管理界面，选择“服务 &gt; 块服务 &gt; LUN组(Namespace组) &gt; LUN(Namespace) &gt; 创建 &gt; 应用类型”，获取应用类型名称。</li><li>“volumeType”为“fs”时，在DeviceManager管理界面，选择“服务 &gt; 文件服务 &gt; 文件系统 &gt; 创建 &gt; 应用类型”，获取应用类型名称。</li></ul>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>挂载到容器内的目录权限。</p>
<p id="p11862561310"><a name="p11862561310"></a><a name="p11862561310"></a></p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p99211326131"><a name="p99211326131"></a><a name="p99211326131"></a>配置格式参考Linux权限设置，如“777”、“755”等。</p>
<p id="p248531271420"><a name="p248531271420"></a><a name="p248531271420"></a>支持所有的SAN存储，NAS存储仅支持OceanStor Dorado 、OceanStor、OceanStor Pacific 8.1.2及之后版本的存储设备。</p>
</td>
</tr>
<tr id="row1638737115618"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a><span>parameters.disableVerifyCapacity</span></p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p1899222312222"><a name="p1899222312222"></a><a name="p1899222312222"></a>是否禁用卷容量校验，禁用后将不校验卷容量是否为扇区大小整数倍。</p>
<p id="p4236912172515"><a name="p4236912172515"></a><a name="p4236912172515"></a>可选值：</p>
<a name="ul7370193012510"></a><a name="ul7370193012510"></a><ul id="ul7370193012510"><li>"true": 禁用卷容量校验。</li><li>"false": 开启卷容量校验。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"false"</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><a name="ul199806344293"></a><a name="ul199806344293"></a><ul id="ul199806344293"><li>OceanStor Dorado和OceanStor的扇区大小为512 B。</li><li>OceanStor Pacific NAS的扇区大小为1 KB。</li><li>OceanStor Pacific SAN的扇区大小为1 MiB。</li><li>OceanDisk 的扇区大小为512 B。</li></ul>
</td>
</tr>
<tr id="row1795755912408"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p1036995916474"><a name="p1036995916474"></a><a name="p1036995916474"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p16369105917476"><a name="p16369105917476"></a><a name="p16369105917476"></a>主机侧NFS挂载选项。支持如下挂载选项：</p>
<p id="p3366172411524"><a name="p3366172411524"></a><a name="p3366172411524"></a>nfsvers：挂载NFS时的协议版本。支持配置的参数值为“3”，“4”，“4.0”，“4.1”和”4.2”。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p53719725212"><a name="p53719725212"></a><a name="p53719725212"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p13398141016526"><a name="p13398141016526"></a><a name="p13398141016526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p775515413439"><a name="p775515413439"></a><a name="p775515413439"></a>在主机执行mount命令时-o参数后的可选选项。列表格式。</p>
<p id="p486929143316"><a name="p486929143316"></a><a name="p486929143316"></a>指定NFS版本挂载时，当前支持NFS 3/4.0/4.1/4.2协议（需存储设备支持且开启）。当配置参数为nfsvers=4时，因为操作系统配置的不同，实际挂载可能为NFS 4的最高版本协议，如4.2，当需要使用4.0协议时，建议配置nfsver:ws=4.0。</p>
</td>
</tr>
<tr id="row122991419104113"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p743994313307"><a name="p743994313307"></a><a name="p743994313307"></a>mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p7439243173012"><a name="p7439243173012"></a><a name="p7439243173012"></a>DPC命名空间支持ACL功能。DPC客户端支持POSIX ACL、NFSv4 ACL、NT ACL的鉴权行为。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p18371167175218"><a name="p18371167175218"></a><a name="p18371167175218"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p5398121065216"><a name="p5398121065216"></a><a name="p5398121065216"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p1451716198319"><a name="p1451716198319"></a><a name="p1451716198319"></a>acl、aclonlyposix、cnflush、cflush参数描述仅供参考，详细参数说明请参考<a href="https://support.huawei.com/enterprise/zh/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">《OceanStor Pacific系列 产品文档》</a> &gt; 配置 &gt; 文件服务基础业务配置指南 &gt; 配置基础业务（DPC场景） &gt; 客户端访问DPC共享 &gt; 步骤2。</p>
</td>
</tr>
<tr id="row131796204428"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p184399439309"><a name="p184399439309"></a><a name="p184399439309"></a>mountOptions.aclonlyposix</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p13950103563719"><a name="p13950103563719"></a><a name="p13950103563719"></a>DPC命名空间支持POSIX ACL功能，DPC客户端支持POSIX ACL的鉴权行为。</p>
<p id="p1943913439308"><a name="p1943913439308"></a><a name="p1943913439308"></a>支持POSIX ACL的协议有：DPC、NFSv3、HDFS。如使用NFSv4 ACL或NT ACL，会导致DPC客户端无法识别该类型的ACL，从而导致该类型的ACL不会生效。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p103711978523"><a name="p103711978523"></a><a name="p103711978523"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p639831014524"><a name="p639831014524"></a><a name="p639831014524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p718315423511"><a name="p718315423511"></a><a name="p718315423511"></a>aclonlyposix与acl参数同时使用时，仅acl参数生效，即命名空间支持ACL功能。</p>
</td>
</tr>
<tr id="row10278171764220"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p867705717358"><a name="p867705717358"></a><a name="p867705717358"></a>mountOptions.cnflush</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p7533510163615"><a name="p7533510163615"></a><a name="p7533510163615"></a>异步刷盘模式，即关闭命名空间下的文件时不会立即刷盘。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p1537112711528"><a name="p1537112711528"></a><a name="p1537112711528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p53981310175211"><a name="p53981310175211"></a><a name="p53981310175211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p46771657123516"><a name="p46771657123516"></a><a name="p46771657123516"></a>异步刷盘模式，当文件关闭时不会同步将Cache的数据持久化到存储介质中，而是通过Cache异步刷盘的方式将数据写入存储介质，Cache的后台刷盘将在写业务完成后根据刷盘周期定时刷盘。在多客户端场景下，对同一文件进行并行操作，文件Size的更新会受刷盘周期的影响，即当刷盘动作完成后才会更新文件的Size，更新通常会在数秒内完成。同步I/O不受刷盘周期影响。</p>
</td>
</tr>
<tr id="row1645871414422"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p13444191520365"><a name="p13444191520365"></a><a name="p13444191520365"></a>mountOptions.cflush</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p194444156366"><a name="p194444156366"></a><a name="p194444156366"></a>同步刷盘模式，即关闭命名空间下的文件时立即刷盘。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p1837197175216"><a name="p1837197175216"></a><a name="p1837197175216"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p93981210155216"><a name="p93981210155216"></a><a name="p93981210155216"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p18444315183615"><a name="p18444315183615"></a><a name="p18444315183615"></a>默认使用同步刷盘模式。</p>
</td>
</tr>
<tr id="row1510837583"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p13195284475"><a name="p13195284475"></a><a name="p13195284475"></a>mountOptions.sec</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p919162820478"><a name="p919162820478"></a><a name="p919162820478"></a>用于指定Kerberos 5协议挂载NFS文件系统。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p1719152812473"><a name="p1719152812473"></a><a name="p1719152812473"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p181910281476"><a name="p181910281476"></a><a name="p181910281476"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><a name="ul196241519175315"></a><a name="ul196241519175315"></a><ul id="ul196241519175315"><li>使用Kerberos 5协议时，请配置krb5。</li><li>使用Kerberos 5i协议时，请配置krb5i。</li><li>使用Kerberos 5p协议时，请配置krb5p。</li><li>Kerberos仅支持NFSv4.0及以上版本的NFS协议。</li><li>OceanStor Dorado和OceanStor 6.1.3及以上版本支持Kerberos。</li></ul>
</td>
</tr>
<tr id="row128563915810"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p22011843373"><a name="p22011843373"></a><a name="p22011843373"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p120110433710"><a name="p120110433710"></a><a name="p120110433710"></a>指定NFS挂载时使用的传输协议。</p>
<p id="p121419557439"><a name="p121419557439"></a><a name="p121419557439"></a>支持配置参数值为：“rdma”。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p1520119410379"><a name="p1520119410379"></a><a name="p1520119410379"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p1201844372"><a name="p1201844372"></a><a name="p1201844372"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><a name="ul197311816164015"></a><a name="ul197311816164015"></a><ul id="ul197311816164015"><li>确保存储系统已启用NFS over RDMA。</li><li>华为企业存储支持OceanStor Dorado和OceanStor 6.1.7及以上的NAS存储。</li><li>华为分布式支持OceanStor Pacific 8.2.0及以后的NAS存储。当分布式存储使用NFS over RDMA时，mountOptions.nfsvers参数必须配置为"3"。</li></ul>
</td>
</tr>
<tr id="row17614421981"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p33347614411"><a name="p33347614411"></a><a name="p33347614411"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p285125974520"><a name="p285125974520"></a><a name="p285125974520"></a>指定NFS挂载时使用的<span>协议端口</span>。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p7334269448"><a name="p7334269448"></a><a name="p7334269448"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p163341965441"><a name="p163341965441"></a><a name="p163341965441"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p1233414615447"><a name="p1233414615447"></a><a name="p1233414615447"></a>传输协议方式使用“rdma”时，请设置为：20049。</p>
</td>
</tr>
<tr id="row72168231837"><td class="cellrowborder" valign="top" width="20.57%" headers="mcps1.2.6.1.1 "><p id="p612723262910"><a name="p612723262910"></a><a name="p612723262910"></a>mountOptions.discard</p>
</td>
<td class="cellrowborder" valign="top" width="25.41%" headers="mcps1.2.6.1.2 "><p id="p4127632172918"><a name="p4127632172918"></a><a name="p4127632172918"></a><span>挂载文件系统时自动触发Trim/Discard操作。该操作会通知块设备释放未使用的块</span>。</p>
</td>
<td class="cellrowborder" valign="top" width="6.959999999999999%" headers="mcps1.2.6.1.3 "><p id="p191271932182911"><a name="p191271932182911"></a><a name="p191271932182911"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.15%" headers="mcps1.2.6.1.4 "><p id="p1712773232912"><a name="p1712773232912"></a><a name="p1712773232912"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="37.91%" headers="mcps1.2.6.1.5 "><p id="p2127193210298"><a name="p2127193210298"></a><a name="p2127193210298"></a>支持xfs、ext4文件系统。</p>
</td>
</tr>
</tbody>
</table>

