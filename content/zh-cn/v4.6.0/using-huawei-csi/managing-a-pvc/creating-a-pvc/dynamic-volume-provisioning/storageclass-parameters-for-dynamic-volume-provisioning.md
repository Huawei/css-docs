---
title: "动态卷供应StorageClass参数说明"
linkTitle: "动态卷供应StorageClass参数说明"
description: 
weight: 2
---

**表 1**  StorageClass配置参数说明

<a name="zh-cn_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="20.43%" id="mcps1.2.6.1.1"><p id="zh-cn_topic_0000001162111564_p875071122919"><a name="zh-cn_topic_0000001162111564_p875071122919"></a><a name="zh-cn_topic_0000001162111564_p875071122919"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="25.52%" id="mcps1.2.6.1.2"><p id="zh-cn_topic_0000001162111564_p17750131113295"><a name="zh-cn_topic_0000001162111564_p17750131113295"></a><a name="zh-cn_topic_0000001162111564_p17750131113295"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="5.18%" id="mcps1.2.6.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="9.34%" id="mcps1.2.6.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="39.53%" id="mcps1.2.6.1.5"><p id="zh-cn_topic_0000001162111564_p075011113295"><a name="zh-cn_topic_0000001162111564_p075011113295"></a><a name="zh-cn_topic_0000001162111564_p075011113295"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p4750141111292"><a name="zh-cn_topic_0000001162111564_p4750141111292"></a><a name="zh-cn_topic_0000001162111564_p4750141111292"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p475091120296"><a name="zh-cn_topic_0000001162111564_p475091120296"></a><a name="zh-cn_topic_0000001162111564_p475091120296"></a>自定义的StorageClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001162111564_p861713973915"><a name="zh-cn_topic_0000001162111564_p861713973915"></a><a name="zh-cn_topic_0000001162111564_p861713973915"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p8750161119299"><a name="zh-cn_topic_0000001162111564_p8750161119299"></a><a name="zh-cn_topic_0000001162111564_p8750161119299"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p15750201119295"><a name="zh-cn_topic_0000001162111564_p15750201119295"></a><a name="zh-cn_topic_0000001162111564_p15750201119295"></a>制备器名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>该字段需要指定为安装华为CSI时设置的驱动名称。</p>
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>取值和values.yaml文件中driverName一致。</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p119108535312"><a name="p119108535312"></a><a name="p119108535312"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p16910135393118"><a name="p16910135393118"></a><a name="p16910135393118"></a>回收策略。支持如下类型：</p>
<a name="ul5209917195517"></a><a name="ul5209917195517"></a><ul id="ul5209917195517"><li>Delete：自动回收资源。</li><li>Retain：<span>手动回收资源</span>。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li>Delete：删除PV/PVC时会关联删除存储上的资源。</li><li>Retain：删除PV/PVC时不会删除存储上的资源。</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p192771821155012"><a name="p192771821155012"></a><a name="p192771821155012"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p8277132112501"><a name="p8277132112501"></a><a name="p8277132112501"></a>是否允许卷扩展。参数设置为true 时，使用该StorageClass的PV可以进行扩容操作。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p13923171118495"><a name="p13923171118495"></a><a name="p13923171118495"></a>此功能仅可用于扩容PV，不能用于缩容PV。</p>
<p id="p1999211201535"><a name="p1999211201535"></a><a name="p1999211201535"></a>扩容PV功能在Kubernetes <span>1.14 (alpha)后才支持</span>。</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>待创建资源所在的后端名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>如果不设置，华为CSI随机选择一个满足容量要求的后端创建资源。</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>建议指定后端，确保创建的资源在预期的后端上。</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p395711171674"><a name="p395711171674"></a><a name="p395711171674"></a>parameters.pool</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p119571517771"><a name="p119571517771"></a><a name="p119571517771"></a>待创建资源所在的存储资源池名称。如果设置，则必须设置parameters.backend。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p43701077524"><a name="p43701077524"></a><a name="p43701077524"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p12398310135213"><a name="p12398310135213"></a><a name="p12398310135213"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p99571317978"><a name="p99571317978"></a><a name="p99571317978"></a>如果不设置，华为CSI会在所选后端上随机选择一个满足容量要求的存储池创建资源。建议指定存储池，确保创建的资源在预期的存储池上。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p1775061119292"><a name="zh-cn_topic_0000001162111564_p1775061119292"></a><a name="zh-cn_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p975011122920"><a name="zh-cn_topic_0000001162111564_p975011122920"></a><a name="zh-cn_topic_0000001162111564_p975011122920"></a>待创建卷类型。支持如下类型：</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li>lun：存储侧发放的资源是LUN。</li><li>fs：存储侧发放的资源是文件系统。</li><li>dtree：存储侧发放的资源是Dtree类型的卷</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul15360173513251"></a><a name="ul15360173513251"></a><ul id="ul15360173513251"><li>使用NAS存储时，必须配置为fs。</li><li>使用SAN存储时，必须配置为lun。</li><li>使用Dtree类型的NAS存储时，必须配置为dtree</li></ul>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p13750171110290"><a name="zh-cn_topic_0000001162111564_p13750171110290"></a><a name="zh-cn_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p67501211102911"><a name="zh-cn_topic_0000001162111564_p67501211102911"></a><a name="zh-cn_topic_0000001162111564_p67501211102911"></a>待创建卷的分配类型。支持如下类型：</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li>thin：创建时不会分配所有需要的空间，而是根据使用情况动态分配。</li><li>thick：创建时分配所有需要的空间。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001162111564_p57502011142910"><a name="zh-cn_topic_0000001162111564_p57502011142910"></a><a name="zh-cn_topic_0000001162111564_p57502011142910"></a>传空相当于传thin，创建时不会分配所有需要的空间，而是根据使用情况动态分配。</p>
<p id="p371813715289"><a name="p371813715289"></a><a name="p371813715289"></a>OceanStor Dorado/OceanStor Dorado V3 不支持thick</p>
</td>
</tr>
<tr id="row167642021133711"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p18750171111299"><a name="zh-cn_topic_0000001162111564_p18750171111299"></a><a name="zh-cn_topic_0000001162111564_p18750171111299"></a>parameters.fsType</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p19169191111571"><a name="p19169191111571"></a><a name="p19169191111571"></a>主机文件系统类型。支持类型为：</p>
<a name="ul9614171916576"></a><a name="ul9614171916576"></a><ul id="ul9614171916576"><li>ext2</li><li>ext3</li><li>ext4</li><li>xfs</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p937047165217"><a name="p937047165217"></a><a name="p937047165217"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1439871055220"><a name="p1439871055220"></a><a name="p1439871055220"></a>ext4</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001162111564_p8750311172910"><a name="zh-cn_topic_0000001162111564_p8750311172910"></a><a name="zh-cn_topic_0000001162111564_p8750311172910"></a>仅当StorageClass的volumeType设置为“lun”，且PVC的volumeMode配置为“Filesystem”时生效。</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p499022713590"><a name="p499022713590"></a><a name="p499022713590"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p2990182715594"><a name="p2990182715594"></a><a name="p2990182715594"></a>可访问该卷的NFS客户端IP地址信息，在指定volumeType为“fs”时必选。</p>
<p id="p1246510319510"><a name="p1246510319510"></a><a name="p1246510319510"></a>支持输入客户端主机名称（建议使用全称域名）、客户端IP地址、客户端IP地址段。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1637013765210"><a name="p1637013765210"></a><a name="p1637013765210"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p113981010185211"><a name="p113981010185211"></a><a name="p113981010185211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p466615315578"><a name="p466615315578"></a><a name="p466615315578"></a>可以使用“*”表示任意客户端。当您不确定访问客户端IP信息时，建议使用“*”防止客户端访问被存储拒绝。</p>
<p id="p164521752175617"><a name="p164521752175617"></a><a name="p164521752175617"></a>当使用客户端主机名称时建议使用全称域名。</p>
<p id="p20828214135714"><a name="p20828214135714"></a><a name="p20828214135714"></a>IP地址支持IPv4、IPv6地址或两者的混合IP地址。</p>
<p id="p208641555185710"><a name="p208641555185710"></a><a name="p208641555185710"></a>可以同时输入多个主机名称、IP地址或IP地址段，以英文分号，空格或按回车键隔开。如示例："192.168.0.10;192.168.0.0/24;myserver1.test"</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row475081162913"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p187501311122918"><a name="zh-cn_topic_0000001162111564_p187501311122918"></a><a name="zh-cn_topic_0000001162111564_p187501311122918"></a>parameters.cloneSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p77501911192918"><a name="zh-cn_topic_0000001162111564_p77501911192918"></a><a name="zh-cn_topic_0000001162111564_p77501911192918"></a>克隆速度。支持配置为1~4。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p20370157155213"><a name="p20370157155213"></a><a name="p20370157155213"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p2398810105211"><a name="p2398810105211"></a><a name="p2398810105211"></a>3</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001162111564_p1775091110298"><a name="zh-cn_topic_0000001162111564_p1775091110298"></a><a name="zh-cn_topic_0000001162111564_p1775091110298"></a>4速度最快。配置克隆PVC或从快照创建PVC时生效，参考<a href="/css-docs/v4.6.0/using-huawei-csi/managing-a-pvc/cloning-a-pvc">克隆PVC</a>或<a href="/css-docs/v4.6.0/using-huawei-csi/managing-a-pvc/creating-a-pvc-using-a-snapshot">从快照创建PVC</a>。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750161119295"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p133711471387"><a name="p133711471387"></a><a name="p133711471387"></a>parameters.applicationType</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p153378472388"><a name="p153378472388"></a><a name="p153378472388"></a>后端为OceanStor Dorado存储时，指定创建LUN/NAS时的应用类型名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p193700711523"><a name="p193700711523"></a><a name="p193700711523"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p8398201010524"><a name="p8398201010524"></a><a name="p8398201010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul2082135095716"></a><a name="ul2082135095716"></a><ul id="ul2082135095716"><li>“volumeType”为“lun”时，在DeviceManager管理界面，选择“服务 &gt; 块服务 &gt; LUN组 &gt; LUN &gt; 创建 &gt; 应用类型”，获取应用类型名称。</li><li>“volumeType”为“fs”时，在DeviceManager管理界面，选择“服务 &gt; 文件服务 &gt; 文件系统 &gt; 创建 &gt; 应用类型”，获取应用类型名称。</li></ul>
</td>
</tr>
<tr id="row15478113119190"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p18478163131914"><a name="p18478163131914"></a><a name="p18478163131914"></a>parameters.qos</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p15525175120211"><a name="p15525175120211"></a><a name="p15525175120211"></a>PV在存储侧的LUN/NAS的QoS设置。</p>
<p id="p12218174732111"><a name="p12218174732111"></a><a name="p12218174732111"></a>配置项值是字典格式的JSON字符串（字符串两边由单引号修饰，字典key由双引号修饰）。如：'{"maxMBPS": 999, "maxIOPS": 999}'</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p03704715211"><a name="p03704715211"></a><a name="p03704715211"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1439818100526"><a name="p1439818100526"></a><a name="p1439818100526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p24789316192"><a name="p24789316192"></a><a name="p24789316192"></a>支持的QoS配置请参考<a href="#table74841513116">表2</a>说明。</p>
</td>
</tr>
<tr id="row1713161417388"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p513251416380"><a name="p513251416380"></a><a name="p513251416380"></a>parameters.storageQuota</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p613221412389"><a name="p613221412389"></a><a name="p613221412389"></a>PV在存储侧配额设置。仅在对接OceanStor Pacific系列存储使用NAS时生效。</p>
<p id="p7371208112220"><a name="p7371208112220"></a><a name="p7371208112220"></a>配置项值是字典格式的JSON字符串（字符串两边由单引号修饰，字典key由双引号修饰）。如：'{"spaceQuota": "softQuota", "gracePeriod": 100}'</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p73707715210"><a name="p73707715210"></a><a name="p73707715210"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p639812105526"><a name="p639812105526"></a><a name="p639812105526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p21321014103814"><a name="p21321014103814"></a><a name="p21321014103814"></a>支持的配额配置请参考<a href="#table2083974632312">表3</a>说明。</p>
</td>
</tr>
<tr id="row87671018115219"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p74248684617"><a name="p74248684617"></a><a name="p74248684617"></a>parameters.hyperMetro</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p84244684616"><a name="p84244684616"></a><a name="p84244684616"></a>是否创建双活卷。当使用的后端是双活类型的后端需要配置。</p>
<a name="ul196431227165817"></a><a name="ul196431227165817"></a><ul id="ul196431227165817"><li>"true"：创建的卷为双活卷。对接存储后端为双活后端时，该值必须为true。</li><li>"false"：创建的卷为普通卷。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p03705765218"><a name="p03705765218"></a><a name="p03705765218"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p12398101013527"><a name="p12398101013527"></a><a name="p12398101013527"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p5697340175314"><a name="p5697340175314"></a><a name="p5697340175314"></a>当使用的后端是双活类型的后端，且需要发放双活卷时，设置该参数为"true"，若设置为"false"，在后端对接的逻辑管理端口漂移的场景下，有业务中断的风险。</p>
</td>
</tr>
<tr id="row5571122410231"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p13571162414233"><a name="p13571162414233"></a><a name="p13571162414233"></a>parameters.metroPairSyncSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p85711524172312"><a name="p85711524172312"></a><a name="p85711524172312"></a>双活Pair同步速率。支持配置为1~4。</p>
<p id="p34101616202511"><a name="p34101616202511"></a><a name="p34101616202511"></a>可选值：</p>
<a name="ul15591625182515"></a><a name="ul15591625182515"></a><ul id="ul15591625182515"><li>1：低</li><li>2：中</li><li>3：高</li><li>4：最高</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p15716241239"><a name="p15716241239"></a><a name="p15716241239"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1957172422315"><a name="p1957172422315"></a><a name="p1957172422315"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p1557114243237"><a name="p1557114243237"></a><a name="p1557114243237"></a>配置创建双活卷时生效。</p>
<p id="p688744685818"><a name="p688744685818"></a><a name="p688744685818"></a>注意：</p>
<a name="ul35821048175812"></a><a name="ul35821048175812"></a><ul id="ul35821048175812"><li>未配置该参数时，双活Pair存储速率由存储决定。</li><li>最高速率同步时可能导致主机时延增大。</li></ul>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>挂载到容器内的目录权限。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>配置格式参考Linux权限设置，如“777”、“755”等。</p>
<p id="p1551794755015"><a name="p1551794755015"></a><a name="p1551794755015"></a>支持所有的SAN存储，NAS存储仅支持OceanStor Dorado 、OceanStor、OceanStor Pacific 8.1.2及之后版本的存储设备。</p>
</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p6718844173115"><a name="p6718844173115"></a><a name="p6718844173115"></a>parameters.rootSquash</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p07183448314"><a name="p07183448314"></a><a name="p07183448314"></a><span>用于设置是否允许客户端的root权限。</span></p>
<p id="p129442384148"><a name="p129442384148"></a><a name="p129442384148"></a>可选值：</p>
<a name="ul124031949175810"></a><a name="ul124031949175810"></a><ul id="ul124031949175810"><li><span>root_squash：</span><span>表示不允许客户端以root用户访问，客户端使用root用户访问时映射为匿名用户。</span></li><li><span>no_root_squash：</span><span>表示允许客户端以root用户访问，保留root用户的权限。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p73701479521"><a name="p73701479521"></a><a name="p73701479521"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p13981710165217"><a name="p13981710165217"></a><a name="p13981710165217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p57181444183118"><a name="p57181444183118"></a><a name="p57181444183118"></a>仅支持NAS存储。</p>
</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p14519141410508"><a name="p14519141410508"></a><a name="p14519141410508"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p3644133462719"><a name="p3644133462719"></a><a name="p3644133462719"></a>用于<span>设置是否保留共享目录的UID和GID。</span></p>
<p id="p19519161416501"><a name="p19519161416501"></a><a name="p19519161416501"></a>可选值：</p>
<a name="ul14691584594"></a><a name="ul14691584594"></a><ul id="ul14691584594"><li><span>all_squash：表示共享目录的UID和GID映射为匿名用户。</span></li><li><span>no_all_squash：表示保留共享目录的UID和GID。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p163702712526"><a name="p163702712526"></a><a name="p163702712526"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p7398121045211"><a name="p7398121045211"></a><a name="p7398121045211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p618494455518"><a name="p618494455518"></a><a name="p618494455518"></a>仅支持NAS存储。</p>
</td>
</tr>
<tr id="row4779143834112"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p6779173815418"><a name="p6779173815418"></a><a name="p6779173815418"></a>parameters.accesskrb5</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p159171449164417"><a name="p159171449164417"></a><a name="p159171449164417"></a>用于配置krb5安全协议。</p>
<a name="ul957213141953"></a><a name="ul957213141953"></a><ul id="ul957213141953"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p577912382417"><a name="p577912382417"></a><a name="p577912382417"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p9779193814412"><a name="p9779193814412"></a><a name="p9779193814412"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p15292191316454"><a name="p15292191316454"></a><a name="p15292191316454"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row99331045154111"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p933031214424"><a name="p933031214424"></a><a name="p933031214424"></a>parameters.accesskrb5i</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p7359241154"><a name="p7359241154"></a><a name="p7359241154"></a>用于配置krb5i安全协议。</p>
<a name="ul149421336953"></a><a name="ul149421336953"></a><ul id="ul149421336953"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p129331245154111"><a name="p129331245154111"></a><a name="p129331245154111"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p96976291391"><a name="p96976291391"></a><a name="p96976291391"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p787455154620"><a name="p787455154620"></a><a name="p787455154620"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row47801443164117"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p11892181264220"><a name="p11892181264220"></a><a name="p11892181264220"></a>parameters.accesskrb5p</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p19699145314447"><a name="p19699145314447"></a><a name="p19699145314447"></a>用于配置krb5p安全协议。</p>
<a name="ul1713519393512"></a><a name="ul1713519393512"></a><ul id="ul1713519393512"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1780134314118"><a name="p1780134314118"></a><a name="p1780134314118"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p14114173118919"><a name="p14114173118919"></a><a name="p14114173118919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p1132519619463"><a name="p1132519619463"></a><a name="p1132519619463"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row446717321624"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p204682321028"><a name="p204682321028"></a><a name="p204682321028"></a>parameters.snapshotDirectoryVisibility</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p124681932122"><a name="p124681932122"></a><a name="p124681932122"></a>用于设置快照目录是否可见。</p>
<p id="p445010115419"><a name="p445010115419"></a><a name="p445010115419"></a>可选值：</p>
<a name="ul129350148597"></a><a name="ul129350148597"></a><ul id="ul129350148597"><li>visible：表示快照目录可见。</li><li>invisible：表示快照目录不可见。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p23707785219"><a name="p23707785219"></a><a name="p23707785219"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p14398210185219"><a name="p14398210185219"></a><a name="p14398210185219"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p1346853212219"><a name="p1346853212219"></a><a name="p1346853212219"></a>仅支持NAS存储。</p>
</td>
</tr>
<tr id="row102662571219"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p526715711214"><a name="p526715711214"></a><a name="p526715711214"></a><span>parameters.reservedSnapshotSpaceRatio</span></p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p18267205722111"><a name="p18267205722111"></a><a name="p18267205722111"></a>用于配置快照预留空间。</p>
<p id="p31927526212"><a name="p31927526212"></a><a name="p31927526212"></a>参数类型：字符串</p>
<p id="p1010918514227"><a name="p1010918514227"></a><a name="p1010918514227"></a>取值范围："0"~"50"</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p3370167175211"><a name="p3370167175211"></a><a name="p3370167175211"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p5398131019522"><a name="p5398131019522"></a><a name="p5398131019522"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p826718573213"><a name="p826718573213"></a><a name="p826718573213"></a>支持OceanStor Dorado 6.1.5+、OceanStor 6.1.5+的NAS存储。</p>
</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a><span>parameters.disableVerifyCapacity</span></p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p1899222312222"><a name="p1899222312222"></a><a name="p1899222312222"></a>是否禁用卷容量校验，禁用后将不校验卷容量是否为扇区大小整数倍。</p>
<p id="p4236912172515"><a name="p4236912172515"></a><a name="p4236912172515"></a>可选值：</p>
<a name="ul7370193012510"></a><a name="ul7370193012510"></a><ul id="ul7370193012510"><li>"true": 禁用卷容量校验。</li><li>"false": 开启卷容量校验。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"false"</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul199806344293"></a><a name="ul199806344293"></a><ul id="ul199806344293"><li>OceanStor Dorado和OceanStor的扇区大小为512 B。</li><li>OceanStor Pacific的扇区大小为1 MiB。</li></ul>
</td>
</tr>
<tr id="row4937192492016"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p1893710249209"><a name="p1893710249209"></a><a name="p1893710249209"></a><span>parameters.</span><span>description</span></p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p20937182432010"><a name="p20937182432010"></a><a name="p20937182432010"></a>用于配置创建的文件系统/LUN的描述信息。</p>
<p id="p259255182110"><a name="p259255182110"></a><a name="p259255182110"></a>参数类型：字符串</p>
<p id="p8541312112118"><a name="p8541312112118"></a><a name="p8541312112118"></a>长度限制：0-255</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p15370175529"><a name="p15370175529"></a><a name="p15370175529"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p17398151010524"><a name="p17398151010524"></a><a name="p17398151010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p8937624182011"><a name="p8937624182011"></a><a name="p8937624182011"></a>仅支持企业存储文件系统及LUN。</p>
</td>
</tr>
<tr id="row1795755912408"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p1036995916474"><a name="p1036995916474"></a><a name="p1036995916474"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p16369105917476"><a name="p16369105917476"></a><a name="p16369105917476"></a>主机侧NFS挂载选项。支持如下挂载选项：</p>
<p id="p3366172411524"><a name="p3366172411524"></a><a name="p3366172411524"></a>nfsvers：挂载NFS时的协议版本。支持配置的参数值为“3”，“4”，“4.0”，“4.1”和”4.2”。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p53719725212"><a name="p53719725212"></a><a name="p53719725212"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p13398141016526"><a name="p13398141016526"></a><a name="p13398141016526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p775515413439"><a name="p775515413439"></a><a name="p775515413439"></a>在主机执行mount命令时-o参数后的可选选项。列表格式。</p>
<p id="p486929143316"><a name="p486929143316"></a><a name="p486929143316"></a>指定NFS版本挂载时，当前支持NFS 3/4.0/4.1/4.2协议（需存储设备支持且开启）。当配置参数为nfsvers=4时，因为操作系统配置的不同，实际挂载可能为NFS 4的最高版本协议，如4.2，当需要使用4.0协议时，建议配置nfsvers=4.0。</p>
</td>
</tr>
<tr id="row122991419104113"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p743994313307"><a name="p743994313307"></a><a name="p743994313307"></a>mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p7439243173012"><a name="p7439243173012"></a><a name="p7439243173012"></a>DPC命名空间支持ACL功能。DPC客户端支持POSIX ACL、NFSv4 ACL、NT ACL的鉴权行为。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p18371167175218"><a name="p18371167175218"></a><a name="p18371167175218"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p5398121065216"><a name="p5398121065216"></a><a name="p5398121065216"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p1451716198319"><a name="p1451716198319"></a><a name="p1451716198319"></a>acl、aclonlyposix、cnflush、cflush参数描述仅供参考，详细参数说明请参考<a href="https://support.huawei.com/enterprise/zh/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">《OceanStor Pacific系列 产品文档》</a> &gt; 配置 &gt; 文件服务基础业务配置指南 &gt; 配置基础业务（DPC场景） &gt; 客户端访问DPC共享 &gt; 步骤2。</p>
</td>
</tr>
<tr id="row131796204428"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p184399439309"><a name="p184399439309"></a><a name="p184399439309"></a>mountOptions.aclonlyposix</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p13950103563719"><a name="p13950103563719"></a><a name="p13950103563719"></a>DPC命名空间支持POSIX ACL功能，DPC客户端支持POSIX ACL的鉴权行为。</p>
<p id="p1943913439308"><a name="p1943913439308"></a><a name="p1943913439308"></a>支持POSIX ACL的协议有：DPC、NFSv3、HDFS。如使用NFSv4 ACL或NT ACL，会导致DPC客户端无法识别该类型的ACL，从而导致该类型的ACL不会生效。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p103711978523"><a name="p103711978523"></a><a name="p103711978523"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p639831014524"><a name="p639831014524"></a><a name="p639831014524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p718315423511"><a name="p718315423511"></a><a name="p718315423511"></a>aclonlyposix与acl参数同时使用时，仅acl参数生效，即命名空间支持ACL功能。</p>
</td>
</tr>
<tr id="row10278171764220"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p867705717358"><a name="p867705717358"></a><a name="p867705717358"></a>mountOptions.cnflush</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p7533510163615"><a name="p7533510163615"></a><a name="p7533510163615"></a>异步刷盘模式，即关闭命名空间下的文件时不会立即刷盘。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1537112711528"><a name="p1537112711528"></a><a name="p1537112711528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p53981310175211"><a name="p53981310175211"></a><a name="p53981310175211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p46771657123516"><a name="p46771657123516"></a><a name="p46771657123516"></a>异步刷盘模式，当文件关闭时不会同步将Cache的数据持久化到存储介质中，而是通过Cache异步刷盘的方式将数据写入存储介质，Cache的后台刷盘将在写业务完成后根据刷盘周期定时刷盘。在多客户端场景下，对同一文件进行并行操作，文件Size的更新会受刷盘周期的影响，即当刷盘动作完成后才会更新文件的Size，更新通常会在数秒内完成。同步I/O不受刷盘周期影响。</p>
</td>
</tr>
<tr id="row1645871414422"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p13444191520365"><a name="p13444191520365"></a><a name="p13444191520365"></a>mountOptions.cflush</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p194444156366"><a name="p194444156366"></a><a name="p194444156366"></a>同步刷盘模式，即关闭命名空间下的文件时立即刷盘。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1837197175216"><a name="p1837197175216"></a><a name="p1837197175216"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p93981210155216"><a name="p93981210155216"></a><a name="p93981210155216"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p18444315183615"><a name="p18444315183615"></a><a name="p18444315183615"></a>默认使用同步刷盘模式。</p>
</td>
</tr>
<tr id="row17198283474"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p13195284475"><a name="p13195284475"></a><a name="p13195284475"></a>mountOptions.sec</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p919162820478"><a name="p919162820478"></a><a name="p919162820478"></a>用于指定Kerberos 5协议挂载NFS文件系统。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1719152812473"><a name="p1719152812473"></a><a name="p1719152812473"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p181910281476"><a name="p181910281476"></a><a name="p181910281476"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul196241519175315"></a><a name="ul196241519175315"></a><ul id="ul196241519175315"><li>使用Kerberos 5协议时，请配置krb5。</li><li>使用Kerberos 5i协议时，请配置krb5i。</li><li>使用Kerberos 5p协议时，请配置krb5p。</li><li>Kerberos仅支持NFSv4.0及以上版本的NFS协议。</li><li>Oceanstor Dorado和Oceanstor 6.1.3及以上版本支持Kerberos。</li></ul>
</td>
</tr>
<tr id="row16497949175212"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p22011843373"><a name="p22011843373"></a><a name="p22011843373"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p120110433710"><a name="p120110433710"></a><a name="p120110433710"></a>指定NFS挂载时使用的传输协议。</p>
<p id="p121419557439"><a name="p121419557439"></a><a name="p121419557439"></a>支持配置参数值为：“rdma”。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1520119410379"><a name="p1520119410379"></a><a name="p1520119410379"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1201844372"><a name="p1201844372"></a><a name="p1201844372"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul197311816164015"></a><a name="ul197311816164015"></a><ul id="ul197311816164015"><li>确保存储系统已启用NFS over RDMA。</li><li>华为企业存储支持OceanStor Dorado 6.1.7及以上的NAS存储。</li><li>华为分布式支持OceanStor Pacific 8.2.0及以后的NAS存储。当分布式存储使用NFS over RDMA时，mountOptions.nfsvers参数必须配置为"3"。</li></ul>
</td>
</tr>
<tr id="row33343664415"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p33347614411"><a name="p33347614411"></a><a name="p33347614411"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p285125974520"><a name="p285125974520"></a><a name="p285125974520"></a>指定NFS挂载时使用的<span>协议端口</span>。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p7334269448"><a name="p7334269448"></a><a name="p7334269448"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p163341965441"><a name="p163341965441"></a><a name="p163341965441"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p1233414615447"><a name="p1233414615447"></a><a name="p1233414615447"></a>传输协议方式使用“rdma”时，请设置为：20049。</p>
</td>
</tr>
<tr id="row11127032122910"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p612723262910"><a name="p612723262910"></a><a name="p612723262910"></a>mountOptions.discard</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p4127632172918"><a name="p4127632172918"></a><a name="p4127632172918"></a><span>挂载文件系统时自动触发Trim/Discard操作。该操作会通知块设备释放未使用的块</span>。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p191271932182911"><a name="p191271932182911"></a><a name="p191271932182911"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1712773232912"><a name="p1712773232912"></a><a name="p1712773232912"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p2127193210298"><a name="p2127193210298"></a><a name="p2127193210298"></a>支持xfs、ext4文件系统。</p>
</td>
</tr>
</tbody>
</table>

**表 2**  支持的QoS配置

<a name="table74841513116"></a>
<table><thead align="left"><tr id="row74844518118"><th class="cellrowborder" valign="top" width="13.278672132786722%" id="mcps1.2.5.1.1"><p id="p2579113031316"><a name="p2579113031316"></a><a name="p2579113031316"></a>存储类型</p>
</th>
<th class="cellrowborder" valign="top" width="15.348465153484653%" id="mcps1.2.5.1.2"><p id="p1643904313015"><a name="p1643904313015"></a><a name="p1643904313015"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="26.167383261673834%" id="mcps1.2.5.1.3"><p id="p164391543143020"><a name="p164391543143020"></a><a name="p164391543143020"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="45.205479452054796%" id="mcps1.2.5.1.4"><p id="p34393439301"><a name="p34393439301"></a><a name="p34393439301"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row18484951131113"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="p35795302132"><a name="p35795302132"></a><a name="p35795302132"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="p18524175292"><a name="p18524175292"></a><a name="p18524175292"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="p05251782913"><a name="p05251782913"></a><a name="p05251782913"></a>控制读写类型。</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="p152017102914"><a name="p152017102914"></a><a name="p152017102914"></a>可选参数（未明确指定将使用后端存储默认值，具体参考相关存储资料）。</p>
<p id="p85218172294"><a name="p85218172294"></a><a name="p85218172294"></a>有效值如下：</p>
<a name="ul5521517142918"></a><a name="ul5521517142918"></a><ul id="ul5521517142918"><li>0：读I/O</li><li>1：写I/O</li><li>2：读写I/O</li></ul>
</td>
</tr>
<tr id="row1548485117111"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p155211732919"><a name="p155211732919"></a><a name="p155211732919"></a><span>MAXBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p952111772918"><a name="p952111772918"></a><a name="p952111772918"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p352171716294"><a name="p352171716294"></a><a name="p352171716294"></a>单位MB/s，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row124848513110"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p9522175292"><a name="p9522175292"></a><a name="p9522175292"></a><span>MINBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p19522171298"><a name="p19522171298"></a><a name="p19522171298"></a>最小带宽保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p2052141711297"><a name="p2052141711297"></a><a name="p2052141711297"></a>单位MB/s，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row74854512113"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1052417132916"><a name="p1052417132916"></a><a name="p1052417132916"></a><span>MAXIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p352117102912"><a name="p352117102912"></a><a name="p352117102912"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p165211714296"><a name="p165211714296"></a><a name="p165211714296"></a>有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row1816819710019"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1316813713016"><a name="p1316813713016"></a><a name="p1316813713016"></a><span>MINIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p0521917172915"><a name="p0521917172915"></a><a name="p0521917172915"></a>最小IOPS保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p105201742914"><a name="p105201742914"></a><a name="p105201742914"></a>有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row1448555120112"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1952517192913"><a name="p1952517192913"></a><a name="p1952517192913"></a><span>LATENCY</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p85211722911"><a name="p85211722911"></a><a name="p85211722911"></a>最大时延保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p352161718293"><a name="p352161718293"></a><a name="p352161718293"></a>单位ms，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row183095010142"><td class="cellrowborder" rowspan="3" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="p38301350131417"><a name="p38301350131417"></a><a name="p38301350131417"></a>OceanStor Dorado V3</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="p1752194493315"><a name="p1752194493315"></a><a name="p1752194493315"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="p1252144463312"><a name="p1252144463312"></a><a name="p1252144463312"></a>控制读写类型。</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="p12521944143313"><a name="p12521944143313"></a><a name="p12521944143313"></a>有效值如下：</p>
<a name="ul25214449332"></a><a name="ul25214449332"></a><ul id="ul25214449332"><li>2：读写I/O</li></ul>
</td>
</tr>
<tr id="row2083035031413"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p135211344193310"><a name="p135211344193310"></a><a name="p135211344193310"></a><span>MAXBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p552117445334"><a name="p552117445334"></a><a name="p552117445334"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p11931954144519"><a name="p11931954144519"></a><a name="p11931954144519"></a>单位MB/s，整数， 范围1~999999999。</p>
</td>
</tr>
<tr id="row68311950201411"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p55218447336"><a name="p55218447336"></a><a name="p55218447336"></a><span>MAXIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p052114442338"><a name="p052114442338"></a><a name="p052114442338"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p4756182510457"><a name="p4756182510457"></a><a name="p4756182510457"></a>类型为整数， 范围100~999999999。</p>
</td>
</tr>
<tr id="row3455115971517"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="p74551059151512"><a name="p74551059151512"></a><a name="p74551059151512"></a>OceanStor Dorado/OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="p17819135614331"><a name="p17819135614331"></a><a name="p17819135614331"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="p981913567333"><a name="p981913567333"></a><a name="p981913567333"></a>控制读写类型。</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="p14819125620331"><a name="p14819125620331"></a><a name="p14819125620331"></a>有效值如下：</p>
<a name="ul17819115611331"></a><a name="ul17819115611331"></a><ul id="ul17819115611331"><li>2：读写I/O</li></ul>
</td>
</tr>
<tr id="row545565991517"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p681925616337"><a name="p681925616337"></a><a name="p681925616337"></a><span>MAXBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1381975613317"><a name="p1381975613317"></a><a name="p1381975613317"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p4819155623311"><a name="p4819155623311"></a><a name="p4819155623311"></a>单位MB/s，类型为整数， 范围1~999999999。</p>
</td>
</tr>
<tr id="row1145610595158"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p7819115610339"><a name="p7819115610339"></a><a name="p7819115610339"></a><span>MINBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p14819145633314"><a name="p14819145633314"></a><a name="p14819145633314"></a>最小带宽保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p1281945614333"><a name="p1281945614333"></a><a name="p1281945614333"></a>单位MB/s，类型为整数， 范围1~999999999。</p>
</td>
</tr>
<tr id="row34568596153"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p15819165612334"><a name="p15819165612334"></a><a name="p15819165612334"></a><span>MAXIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p18819185623315"><a name="p18819185623315"></a><a name="p18819185623315"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p15990244424"><a name="p15990244424"></a><a name="p15990244424"></a>类型为整数， 范围100~999999999。</p>
</td>
</tr>
<tr id="row11456959111513"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p178191156163318"><a name="p178191156163318"></a><a name="p178191156163318"></a><span>MINIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p11819185643319"><a name="p11819185643319"></a><a name="p11819185643319"></a>最小IOPS保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p943173717425"><a name="p943173717425"></a><a name="p943173717425"></a>类型为整数， 范围100~999999999。</p>
</td>
</tr>
<tr id="row81499500175"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p736119112181"><a name="p736119112181"></a><a name="p736119112181"></a><span>LATENCY</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p0361191131815"><a name="p0361191131815"></a><a name="p0361191131815"></a>最大时延保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p33621115182"><a name="p33621115182"></a><a name="p33621115182"></a>单位ms，仅支持配置0.5或1.5。</p>
</td>
</tr>
<tr id="row2172155111816"><td class="cellrowborder" rowspan="2" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="p13172105116189"><a name="p13172105116189"></a><a name="p13172105116189"></a>FusionStorage/OceanStor Pacific系列</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0273440106_p743994313307"><a name="zh-cn_topic_0273440106_p743994313307"></a><a name="zh-cn_topic_0273440106_p743994313307"></a>maxMBPS</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0273440106_p7439243173012"><a name="zh-cn_topic_0273440106_p7439243173012"></a><a name="zh-cn_topic_0273440106_p7439243173012"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0273440106_p184391143133017"><a name="zh-cn_topic_0273440106_p184391143133017"></a><a name="zh-cn_topic_0273440106_p184391143133017"></a>必填。有效值为大于0的整数，单位MB/s。最大值请参考存储设备实际限制，如OceanStor Pacific NAS最大值为1073741824。</p>
</td>
</tr>
<tr id="row1734105531812"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0273440106_p184399439309"><a name="zh-cn_topic_0273440106_p184399439309"></a><a name="zh-cn_topic_0273440106_p184399439309"></a><span>maxIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0273440106_p1943913439308"><a name="zh-cn_topic_0273440106_p1943913439308"></a><a name="zh-cn_topic_0273440106_p1943913439308"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0273440106_p14439114315304"><a name="zh-cn_topic_0273440106_p14439114315304"></a><a name="zh-cn_topic_0273440106_p14439114315304"></a>必填。有效值为大于0的整数。最大值请参考存储设备实际限制，如OceanStor Pacific NAS最大值为1073741824000。</p>
</td>
</tr>
</tbody>
</table>

**表 3**  支持的配额配置

<a name="table2083974632312"></a>
<table><thead align="left"><tr id="row68394463230"><th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0000001218368853_p1643904313015"><a name="zh-cn_topic_0000001218368853_p1643904313015"></a><a name="zh-cn_topic_0000001218368853_p1643904313015"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0000001218368853_p164391543143020"><a name="zh-cn_topic_0000001218368853_p164391543143020"></a><a name="zh-cn_topic_0000001218368853_p164391543143020"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0000001218368853_p34393439301"><a name="zh-cn_topic_0000001218368853_p34393439301"></a><a name="zh-cn_topic_0000001218368853_p34393439301"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row58391646142313"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001218368853_p10540642195814"><a name="zh-cn_topic_0000001218368853_p10540642195814"></a><a name="zh-cn_topic_0000001218368853_p10540642195814"></a>spaceQuota</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001218368853_p7439243173012"><a name="zh-cn_topic_0000001218368853_p7439243173012"></a><a name="zh-cn_topic_0000001218368853_p7439243173012"></a>文件配额类型。</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001218368853_p184391143133017"><a name="zh-cn_topic_0000001218368853_p184391143133017"></a><a name="zh-cn_topic_0000001218368853_p184391143133017"></a>必选。仅支持配置<span class="parmvalue" id="zh-cn_topic_0000001218368853_parmvalue6901424105917"><a name="zh-cn_topic_0000001218368853_parmvalue6901424105917"></a><a name="zh-cn_topic_0000001218368853_parmvalue6901424105917"></a>“softQuota”</span>或者<span class="parmvalue" id="zh-cn_topic_0000001218368853_parmvalue1265010297596"><a name="zh-cn_topic_0000001218368853_parmvalue1265010297596"></a><a name="zh-cn_topic_0000001218368853_parmvalue1265010297596"></a>“hardQuota”</span>。</p>
</td>
</tr>
<tr id="row13839124642310"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001218368853_p184399439309"><a name="zh-cn_topic_0000001218368853_p184399439309"></a><a name="zh-cn_topic_0000001218368853_p184399439309"></a>gracePeriod</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001218368853_p1943913439308"><a name="zh-cn_topic_0000001218368853_p1943913439308"></a><a name="zh-cn_topic_0000001218368853_p1943913439308"></a>配置软配额时，允许的超限天数。</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001218368853_p1540512282024"><a name="zh-cn_topic_0000001218368853_p1540512282024"></a><a name="zh-cn_topic_0000001218368853_p1540512282024"></a>条件可选，当<span class="parmname" id="zh-cn_topic_0000001218368853_parmname5404162815213"><a name="zh-cn_topic_0000001218368853_parmname5404162815213"></a><a name="zh-cn_topic_0000001218368853_parmname5404162815213"></a>“spaceQuota”</span>配置为<span class="parmvalue" id="zh-cn_topic_0000001218368853_parmvalue74056285216"><a name="zh-cn_topic_0000001218368853_parmvalue74056285216"></a><a name="zh-cn_topic_0000001218368853_parmvalue74056285216"></a>“softQuota”</span>时可选。</p>
<p id="zh-cn_topic_0000001218368853_p14439114315304"><a name="zh-cn_topic_0000001218368853_p14439114315304"></a><a name="zh-cn_topic_0000001218368853_p14439114315304"></a>类型为整数，支持范围为0～4294967294。</p>
</td>
</tr>
</tbody>
</table>

