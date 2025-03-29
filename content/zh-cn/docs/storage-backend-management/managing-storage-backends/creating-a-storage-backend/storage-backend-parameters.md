---
title: "存储后端配置项说明"
linkTitle: "存储后端配置项说明"
description: 
weight: 2
---

后端配置文件样例模板为/examples/backend/backend.yaml，该文件为一个示例文件，具体配置项如下表所示：

**表 1**  backend配置项说明

<a name="table9126101819192"></a>
<table><thead align="left"><tr id="row10127131813194"><th class="cellrowborder" valign="top" width="13.55%" id="mcps1.2.6.1.1"><p id="p5631154913199"><a name="p5631154913199"></a><a name="p5631154913199"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="38.58%" id="mcps1.2.6.1.2"><p id="p463104991916"><a name="p463104991916"></a><a name="p463104991916"></a>描述</p>
</th>
<th class="cellrowborder" valign="top" width="7.2700000000000005%" id="mcps1.2.6.1.3"><p id="p1463134917198"><a name="p1463134917198"></a><a name="p1463134917198"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="6.5600000000000005%" id="mcps1.2.6.1.4"><p id="p6919415195119"><a name="p6919415195119"></a><a name="p6919415195119"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="34.04%" id="mcps1.2.6.1.5"><p id="p10631049171910"><a name="p10631049171910"></a><a name="p10631049171910"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row111271188193"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p1233915445454"><a name="zh-cn_topic_0000001324610777_p1233915445454"></a><a name="zh-cn_topic_0000001324610777_p1233915445454"></a>storage</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p3339204417453"><a name="zh-cn_topic_0000001324610777_p3339204417453"></a><a name="zh-cn_topic_0000001324610777_p3339204417453"></a>存储服务类型。</p>
<a name="zh-cn_topic_0000001324610777_ul713574293420"></a><a name="zh-cn_topic_0000001324610777_ul713574293420"></a><ul id="zh-cn_topic_0000001324610777_ul713574293420"><li>企业存储提供SAN存储时填写oceanstor-san。</li><li>企业存储提供NAS存储时填写oceanstor-nas。</li><li>企业存储提供Dtree类型的NAS存储时填写oceanstor-dtree。</li><li>分布式存储提供SAN存储时填写fusionstorage-san。</li><li>分布式存储提供NAS存储时填写fusionstorage-nas。</li><li>分布式储提供Dtree类型的NAS存储时填写fusionstorage-dtree。</li><li>使用OceanDisk存储时填写oceandisk-san。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p533910449459"><a name="zh-cn_topic_0000001324610777_p533910449459"></a><a name="zh-cn_topic_0000001324610777_p533910449459"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p15919151545111"><a name="p15919151545111"></a><a name="p15919151545111"></a>oceanstor-nas</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001324610777_p17339174424512"><a name="zh-cn_topic_0000001324610777_p17339174424512"></a><a name="zh-cn_topic_0000001324610777_p17339174424512"></a>一个后端只允许提供一种存储服务。如果单套华为存储系统可以同时提供SAN和NAS的存储服务时，可以配置创建多个后端，每个后端使用不同的存储服务类型。</p>
</td>
</tr>
<tr id="row15127618111910"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p733904424519"><a name="zh-cn_topic_0000001324610777_p733904424519"></a><a name="zh-cn_topic_0000001324610777_p733904424519"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p23903331109"><a name="zh-cn_topic_0000001324610777_p23903331109"></a><a name="zh-cn_topic_0000001324610777_p23903331109"></a>存储后端名称。支持小写字母、数字和特殊字符"-"，且需要以字母或数字开头，最多63个字符。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p18339944154510"><a name="zh-cn_topic_0000001324610777_p18339944154510"></a><a name="zh-cn_topic_0000001324610777_p18339944154510"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p18919015125112"><a name="p18919015125112"></a><a name="p18919015125112"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="p1874481011019"><a name="p1874481011019"></a><a name="p1874481011019"></a>请保证存储后端名称唯一。</p>
</td>
</tr>
<tr id="row765135132312"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="p1650357236"><a name="p1650357236"></a><a name="p1650357236"></a>namespace</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="p1466335142311"><a name="p1466335142311"></a><a name="p1466335142311"></a>命名空间。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="p176653592311"><a name="p176653592311"></a><a name="p176653592311"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p391981510517"><a name="p391981510517"></a><a name="p391981510517"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="p866103515237"><a name="p866103515237"></a><a name="p866103515237"></a>存储后端必须与华为CSI在相同的命名空间中。</p>
</td>
</tr>
<tr id="row184812161516"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="p38488211152"><a name="p38488211152"></a><a name="p38488211152"></a>vstoreName</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="p384813214151"><a name="p384813214151"></a><a name="p384813214151"></a>存储侧的租户名称。当对接后端是OceanStor V5存储时，需要在指定租户下发放资源时，需要指定该参数。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="p884812114157"><a name="p884812114157"></a><a name="p884812114157"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p16919131517511"><a name="p16919131517511"></a><a name="p16919131517511"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="p584814213151"><a name="p584814213151"></a><a name="p584814213151"></a>仅对接后端是OceanStor V5且需要支持租户时，需要指定该参数。</p>
</td>
</tr>
<tr id="row1218054742718"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="p14180194702714"><a name="p14180194702714"></a><a name="p14180194702714"></a>accountName</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="p1518094762719"><a name="p1518094762719"></a><a name="p1518094762719"></a>存储侧的账户名称。当对接资源是OceanStor Pacific NAS或OceanStor Pacific DTree时，需要在指定账户下发放NAS资源时，需要指定该参数。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="p14180547182717"><a name="p14180547182717"></a><a name="p14180547182717"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p20919715115120"><a name="p20919715115120"></a><a name="p20919715115120"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="p195481349369"><a name="p195481349369"></a><a name="p195481349369"></a>对接后端是OceanStor Pacific NAS或OceanStor Pacific DTree且需要支持账户时，需要指定该参数。</p>
</td>
</tr>
<tr id="row1212714182196"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p153399449451"><a name="zh-cn_topic_0000001324610777_p153399449451"></a><a name="zh-cn_topic_0000001324610777_p153399449451"></a>urls</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p430691742216"><a name="zh-cn_topic_0000001324610777_p430691742216"></a><a name="zh-cn_topic_0000001324610777_p430691742216"></a>存储设备的管理URL。参数格式为列表。支持按照域名或者IP+端口的方式进行配置。仅支持IPv4。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p1233934484518"><a name="zh-cn_topic_0000001324610777_p1233934484518"></a><a name="zh-cn_topic_0000001324610777_p1233934484518"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p691916153512"><a name="p691916153512"></a><a name="p691916153512"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001324610777_p17339144114512"><a name="zh-cn_topic_0000001324610777_p17339144114512"></a><a name="zh-cn_topic_0000001324610777_p17339144114512"></a>当对接后端是OceanStor或OceanStor Dorado存储，需要在指定租户下发放资源时，该参数配置为指定租户的逻辑管理端口URL。</p>
</td>
</tr>
<tr id="row7127101841917"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p17111241100"><a name="zh-cn_topic_0000001324610777_p17111241100"></a><a name="zh-cn_topic_0000001324610777_p17111241100"></a>pools</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p1671172411012"><a name="zh-cn_topic_0000001324610777_p1671172411012"></a><a name="zh-cn_topic_0000001324610777_p1671172411012"></a>存储设备的存储池。参数格式为列表。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p971172414020"><a name="zh-cn_topic_0000001324610777_p971172414020"></a><a name="zh-cn_topic_0000001324610777_p971172414020"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p19191715195117"><a name="p19191715195117"></a><a name="p19191715195117"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001324610777_p117122413014"><a name="zh-cn_topic_0000001324610777_p117122413014"></a><a name="zh-cn_topic_0000001324610777_p117122413014"></a>storage为oceanstor-dtree或fusionstorage-dtree时， 可以不填。</p>
</td>
</tr>
<tr id="row1312711851911"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p20613155814116"><a name="zh-cn_topic_0000001324610777_p20613155814116"></a><a name="zh-cn_topic_0000001324610777_p20613155814116"></a>parameters.protocol</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p12810447425"><a name="zh-cn_topic_0000001324610777_p12810447425"></a><a name="zh-cn_topic_0000001324610777_p12810447425"></a>存储协议。参数格式为字符串。</p>
<a name="zh-cn_topic_0000001324610777_ul5584070363"></a><a name="zh-cn_topic_0000001324610777_ul5584070363"></a><ul id="zh-cn_topic_0000001324610777_ul5584070363"><li>iscsi</li><li>fc</li><li>roce</li><li>fc-nvme</li><li>nfs</li><li>nfs+</li><li>dpc</li><li>scsi</li></ul>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p1261313581616"><a name="zh-cn_topic_0000001324610777_p1261313581616"></a><a name="zh-cn_topic_0000001324610777_p1261313581616"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p109191715115118"><a name="p109191715115118"></a><a name="p109191715115118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><a name="ul555819319152"></a><a name="ul555819319152"></a><ul id="ul555819319152"><li>使用iscsi时，请确保对接的计算节点已安装iSCSI客户端。</li><li>使用nfs时，请确保对接的计算节点已安装NFS客户端工具。</li><li>使用nfs+时，请确保对接的计算节点已安装NFS+客户端工具。</li><li>使用fc-nvme/roce时，请确保对接的计算节点已安装nvme-cli工具，工具版本仅支持1.x且版本不低于1.9。</li><li>使用dpc时，请确保对接的计算节点已安装DPC客户端，并已在待接入存储上添加为DPC计算节点。</li><li>使用scsi时，请确保对接的计算节点已安装分布式存储VBS客户端。</li></ul>
</td>
</tr>
<tr id="row61271618121913"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p12730821724"><a name="zh-cn_topic_0000001324610777_p12730821724"></a><a name="zh-cn_topic_0000001324610777_p12730821724"></a>parameters.portals</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p127300212214"><a name="zh-cn_topic_0000001324610777_p127300212214"></a><a name="zh-cn_topic_0000001324610777_p127300212214"></a>业务访问端口。节点会使用该端口对存储资源进行读写访问。参数格式为一个列表</p>
<p id="zh-cn_topic_0000001324610777_p166476473917"><a name="zh-cn_topic_0000001324610777_p166476473917"></a><a name="zh-cn_topic_0000001324610777_p166476473917"></a>iscsi，roce，nfs+协议支持配置多个端口，nfs协议仅支持配置一个端口，fc、fc-nvme、dpc协议无需配置业务端口，scsi协议的端口形式为字典格式，key为主机名称，value为IP地址，仅支持IPv4。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p8730621026"><a name="zh-cn_topic_0000001324610777_p8730621026"></a><a name="zh-cn_topic_0000001324610777_p8730621026"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p15919101510519"><a name="p15919101510519"></a><a name="p15919101510519"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><a name="ul73520114122"></a><a name="ul73520114122"></a><ul id="ul73520114122"><li>使用租户/账户对接后端时，此时portals必须配置为租户/账户所拥有的逻辑端口信息。</li><li>如果使用nfs/nfs+协议，支持填写为域名地址。</li></ul>
</td>
</tr>
<tr id="row159281476499"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="p2092814473495"><a name="p2092814473495"></a><a name="p2092814473495"></a>parameters.ALUA</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="p1292874710497"><a name="p1292874710497"></a><a name="p1292874710497"></a>存储后端ALUA参数配置。当工作节点使用操作系统原生多路径，且启用了ALUA时，需要进行配置。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="p179281474494"><a name="p179281474494"></a><a name="p179281474494"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p159191115165113"><a name="p159191115165113"></a><a name="p159191115165113"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="p592814711497"><a name="p592814711497"></a><a name="p592814711497"></a>如果主机多路径配置启用了ALUA，请确保后端ALUA配置和主机的ALUA配置一致。</p>
<p id="p9408545184515"><a name="p9408545184515"></a><a name="p9408545184515"></a>ALUA详细配置请参考<a href="/css-docs/docs/advanced-features/configuring-alua/configuring-alua-using-helm">通过Helm配置ALUA特性</a>。</p>
</td>
</tr>
<tr id="row69321538172918"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="p2932193817290"><a name="p2932193817290"></a><a name="p2932193817290"></a>parameters.parentname</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="p19753720163619"><a name="p19753720163619"></a><a name="p19753720163619"></a>当前存储上的某一个文件系统名称，在此文件系统下创建Dtree。</p>
<p id="p13753520153612"><a name="p13753520153612"></a><a name="p13753520153612"></a>storage为oceanstor-dtree或fusionstorage-dtree时可选。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="p7932338112916"><a name="p7932338112916"></a><a name="p7932338112916"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p593283812910"><a name="p593283812910"></a><a name="p593283812910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="p17932638112915"><a name="p17932638112915"></a><a name="p17932638112915"></a>请到DeviceManager文件系统界面查询。</p>
</td>
</tr>
<tr id="row158363112216"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001276213416_p1619335616176"><a name="zh-cn_topic_0000001276213416_p1619335616176"></a><a name="zh-cn_topic_0000001276213416_p1619335616176"></a>metrovStorePairID</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="p03781853135"><a name="p03781853135"></a><a name="p03781853135"></a>双活租户Pair ID。</p>
<p id="zh-cn_topic_0000001276213416_p17485124117179"><a name="zh-cn_topic_0000001276213416_p17485124117179"></a><a name="zh-cn_topic_0000001276213416_p17485124117179"></a>当需要创建PV在存储侧支持NAS双活特性时，该字段必填。此时需要填入待创建的PV所归属的存储侧双活租户Pair ID。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001276213416_p1448594113173"><a name="zh-cn_topic_0000001276213416_p1448594113173"></a><a name="zh-cn_topic_0000001276213416_p1448594113173"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p391981511519"><a name="p391981511519"></a><a name="p391981511519"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001276213416_p568210171458"><a name="zh-cn_topic_0000001276213416_p568210171458"></a><a name="zh-cn_topic_0000001276213416_p568210171458"></a>双活租户Pair ID请到DeviceManager界面查询。</p>
</td>
</tr>
<tr id="row3332581728"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001276213416_p179320619189"><a name="zh-cn_topic_0000001276213416_p179320619189"></a><a name="zh-cn_topic_0000001276213416_p179320619189"></a>metroBackend</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001276213416_p3494125991718"><a name="zh-cn_topic_0000001276213416_p3494125991718"></a><a name="zh-cn_topic_0000001276213416_p3494125991718"></a>双活对端的后端名称。参数格式为字符串。</p>
<p id="p19322352557"><a name="p19322352557"></a><a name="p19322352557"></a>当需要创建PV在存储侧支持NAS双活特性时，该字段必填。此时需要填入准备和当前后端组成双活的另一个后端名称。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001276213416_p649485911172"><a name="zh-cn_topic_0000001276213416_p649485911172"></a><a name="zh-cn_topic_0000001276213416_p649485911172"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p1791951575111"><a name="p1791951575111"></a><a name="p1791951575111"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001276213416_p768261754513"><a name="zh-cn_topic_0000001276213416_p768261754513"></a><a name="zh-cn_topic_0000001276213416_p768261754513"></a>组对的两个后端都必须将对方名称填入。这两个后端组成双活关系后，不允许再和其他后端组成双活关系。</p>
</td>
</tr>
<tr id="row36316121111"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="p2064181219115"><a name="p2064181219115"></a><a name="p2064181219115"></a>supportedTopologies</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="p18642127115"><a name="p18642127115"></a><a name="p18642127115"></a>存储拓扑感知配置。参数格式为列表类型的JSON。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="p864111251119"><a name="p864111251119"></a><a name="p864111251119"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p1191961545114"><a name="p1191961545114"></a><a name="p1191961545114"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="p176418120111"><a name="p176418120111"></a><a name="p176418120111"></a>如果启用存储拓扑感知，需要配置该参数。具体请参考<a href="/css-docs/docs/advanced-features/configuring-storage-topology-awareness/configuring-storage-topology-awareness-using-helm">通过Helm配置存储拓扑感知</a>。</p>
</td>
</tr>
<tr id="row11363104441311"><td class="cellrowborder" valign="top" width="13.55%" headers="mcps1.2.6.1.1 "><p id="p0363164461310"><a name="p0363164461310"></a><a name="p0363164461310"></a>maxClientThreads</p>
</td>
<td class="cellrowborder" valign="top" width="38.58%" headers="mcps1.2.6.1.2 "><p id="p1236374461311"><a name="p1236374461311"></a><a name="p1236374461311"></a>同时连接到存储后端的最大连接数。</p>
</td>
<td class="cellrowborder" valign="top" width="7.2700000000000005%" headers="mcps1.2.6.1.3 "><p id="p43631344161310"><a name="p43631344161310"></a><a name="p43631344161310"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="6.5600000000000005%" headers="mcps1.2.6.1.4 "><p id="p16919715145113"><a name="p16919715145113"></a><a name="p16919715145113"></a>30</p>
</td>
<td class="cellrowborder" valign="top" width="34.04%" headers="mcps1.2.6.1.5 "><p id="p7363204412133"><a name="p7363204412133"></a><a name="p7363204412133"></a>范围1~30，如果不配置该参数，或参数值不在规定范围内，则取用默认值30。</p>
</td>
</tr>
</tbody>
</table>

