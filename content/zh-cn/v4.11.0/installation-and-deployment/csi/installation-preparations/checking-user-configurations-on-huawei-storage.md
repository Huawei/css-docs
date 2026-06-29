---
title: "检查华为存储上的用户配置"
linkTitle: "检查华为存储上的用户配置"
description: 
weight: 3
---

当华为存储接入容器平台后，华为CSI需要在华为存储上根据业务要求管理存储资源，如创建卷、映射卷等操作。此时，华为CSI需要使用华为存储上已经创建的用户和华为存储进行通信。针对不同存储设备所需要的用户信息如下表所示。

**表 1**  存储对接CSI时使用的用户要求

<a name="zh-cn_topic_0214996140_table14321516134313"></a>
<table><thead align="left"><tr id="zh-cn_topic_0214996140_row5326166437"><th class="cellrowborder" valign="top" width="29.13%" id="mcps1.2.6.1.1"><p id="zh-cn_topic_0214996140_p1832131654315"><a name="zh-cn_topic_0214996140_p1832131654315"></a><a name="zh-cn_topic_0214996140_p1832131654315"></a>存储类型</p>
</th>
<th class="cellrowborder" valign="top" width="20.97%" id="mcps1.2.6.1.2"><p id="zh-cn_topic_0214996140_p240885914315"><a name="zh-cn_topic_0214996140_p240885914315"></a><a name="zh-cn_topic_0214996140_p240885914315"></a>用户类型</p>
</th>
<th class="cellrowborder" valign="top" width="17.119999999999997%" id="mcps1.2.6.1.3"><p id="zh-cn_topic_0214996140_p15321716184318"><a name="zh-cn_topic_0214996140_p15321716184318"></a><a name="zh-cn_topic_0214996140_p15321716184318"></a>角色</p>
</th>
<th class="cellrowborder" valign="top" width="17.61%" id="mcps1.2.6.1.4"><p id="zh-cn_topic_0214996140_p432316124312"><a name="zh-cn_topic_0214996140_p432316124312"></a><a name="zh-cn_topic_0214996140_p432316124312"></a>级别</p>
</th>
<th class="cellrowborder" valign="top" width="15.17%" id="mcps1.2.6.1.5"><p id="zh-cn_topic_0214996140_p83251674311"><a name="zh-cn_topic_0214996140_p83251674311"></a><a name="zh-cn_topic_0214996140_p83251674311"></a>类型</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0214996140_row132121615432"><td class="cellrowborder" rowspan="2" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p1232416104313"><a name="zh-cn_topic_0214996140_p1232416104313"></a><a name="zh-cn_topic_0214996140_p1232416104313"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p9115125319436"><a name="zh-cn_topic_0214996140_p9115125319436"></a><a name="zh-cn_topic_0214996140_p9115125319436"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p203211654314"><a name="zh-cn_topic_0214996140_p203211654314"></a><a name="zh-cn_topic_0214996140_p203211654314"></a>管理员</p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p1732191664311"><a name="zh-cn_topic_0214996140_p1732191664311"></a><a name="zh-cn_topic_0214996140_p1732191664311"></a>管理员</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0214996140_p1532116144311"><a name="zh-cn_topic_0214996140_p1532116144311"></a><a name="zh-cn_topic_0214996140_p1532116144311"></a>本地用户/LDAP用户<sup id="sup1258215209344"><a name="sup1258215209344"></a><a name="sup1258215209344"></a>2</sup></p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row217510214456"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p1517512154515"><a name="zh-cn_topic_0214996140_p1517512154515"></a><a name="zh-cn_topic_0214996140_p1517512154515"></a>租户用户</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p161761824457"><a name="zh-cn_topic_0214996140_p161761824457"></a><a name="zh-cn_topic_0214996140_p161761824457"></a>租户管理员</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p71768264519"><a name="zh-cn_topic_0214996140_p71768264519"></a><a name="zh-cn_topic_0214996140_p71768264519"></a>管理员</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p111763294517"><a name="zh-cn_topic_0214996140_p111763294517"></a><a name="zh-cn_topic_0214996140_p111763294517"></a>本地用户/LDAP用户<sup id="sup1536971923412"><a name="sup1536971923412"></a><a name="sup1536971923412"></a>2</sup></p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row163581026142419"><td class="cellrowborder" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p335942672413"><a name="zh-cn_topic_0214996140_p335942672413"></a><a name="zh-cn_topic_0214996140_p335942672413"></a>OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p1129916445242"><a name="zh-cn_topic_0214996140_p1129916445242"></a><a name="zh-cn_topic_0214996140_p1129916445242"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p12299194414240"><a name="zh-cn_topic_0214996140_p12299194414240"></a><a name="zh-cn_topic_0214996140_p12299194414240"></a>管理员/自定义角色<sup id="sup19138264283"><a name="sup19138264283"></a><a name="sup19138264283"></a>1</sup></p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p329910440244"><a name="zh-cn_topic_0214996140_p329910440244"></a><a name="zh-cn_topic_0214996140_p329910440244"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0214996140_p11299154442413"><a name="zh-cn_topic_0214996140_p11299154442413"></a><a name="zh-cn_topic_0214996140_p11299154442413"></a>本地用户/LDAP用户<sup id="sup922520918341"><a name="sup922520918341"></a><a name="sup922520918341"></a>2</sup></p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row143210168434"><td class="cellrowborder" rowspan="2" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p23218164437"><a name="zh-cn_topic_0214996140_p23218164437"></a><a name="zh-cn_topic_0214996140_p23218164437"></a>OceanStor Dorado</p>
<p id="p58501367152"><a name="p58501367152"></a><a name="p58501367152"></a></p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p13170324518"><a name="zh-cn_topic_0214996140_p13170324518"></a><a name="zh-cn_topic_0214996140_p13170324518"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p2045125319467"><a name="zh-cn_topic_0214996140_p2045125319467"></a><a name="zh-cn_topic_0214996140_p2045125319467"></a>管理员/自定义角色<sup id="sup221894516187"><a name="sup221894516187"></a><a name="sup221894516187"></a>1</sup></p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p845125344614"><a name="zh-cn_topic_0214996140_p845125344614"></a><a name="zh-cn_topic_0214996140_p845125344614"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0214996140_p124515539466"><a name="zh-cn_topic_0214996140_p124515539466"></a><a name="zh-cn_topic_0214996140_p124515539466"></a>本地用户/LDAP用户<sup id="sup1214418156345"><a name="sup1214418156345"></a><a name="sup1214418156345"></a>2</sup></p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row9761201434620"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p117072165112"><a name="zh-cn_topic_0214996140_p117072165112"></a><a name="zh-cn_topic_0214996140_p117072165112"></a>租户用户</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p14452053154610"><a name="zh-cn_topic_0214996140_p14452053154610"></a><a name="zh-cn_topic_0214996140_p14452053154610"></a>租户管理员</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p15451053204616"><a name="zh-cn_topic_0214996140_p15451053204616"></a><a name="zh-cn_topic_0214996140_p15451053204616"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p1745125312460"><a name="zh-cn_topic_0214996140_p1745125312460"></a><a name="zh-cn_topic_0214996140_p1745125312460"></a>本地用户/LDAP用户<sup id="sup28828162341"><a name="sup28828162341"></a><a name="sup28828162341"></a>2</sup></p>
</td>
</tr>
<tr id="row466420754719"><td class="cellrowborder" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="p7664197204713"><a name="p7664197204713"></a><a name="p7664197204713"></a>OceanStor A系列</p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="p18664147194715"><a name="p18664147194715"></a><a name="p18664147194715"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="p156645774719"><a name="p156645774719"></a><a name="p156645774719"></a>管理员</p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="p566427134715"><a name="p566427134715"></a><a name="p566427134715"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="p12738104818475"><a name="p12738104818475"></a><a name="p12738104818475"></a>本地用户/LDAP用户<sup id="sup1373810487475"><a name="sup1373810487475"></a><a name="sup1373810487475"></a>2</sup></p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row85331119464"><td class="cellrowborder" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p10532011104612"><a name="zh-cn_topic_0214996140_p10532011104612"></a><a name="zh-cn_topic_0214996140_p10532011104612"></a>OceanStor Pacific系列</p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p145391184612"><a name="zh-cn_topic_0214996140_p145391184612"></a><a name="zh-cn_topic_0214996140_p145391184612"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p1453151116467"><a name="zh-cn_topic_0214996140_p1453151116467"></a><a name="zh-cn_topic_0214996140_p1453151116467"></a><span>管理员</span></p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p1753131112468"><a name="zh-cn_topic_0214996140_p1753131112468"></a><a name="zh-cn_topic_0214996140_p1753131112468"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0214996140_p4533113468"><a name="zh-cn_topic_0214996140_p4533113468"></a><a name="zh-cn_topic_0214996140_p4533113468"></a>本地用户</p>
</td>
</tr>
<tr id="row27531822552"><td class="cellrowborder" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="p1575442105515"><a name="p1575442105515"></a><a name="p1575442105515"></a>OceanDisk</p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="p77542219556"><a name="p77542219556"></a><a name="p77542219556"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="p1175472185518"><a name="p1175472185518"></a><a name="p1175472185518"></a>管理员</p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="p375414285512"><a name="p375414285512"></a><a name="p375414285512"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="p19754152135515"><a name="p19754152135515"></a><a name="p19754152135515"></a>本地用户</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>-   使用自定义角色，需要给角色配置权限，最小权限请参考[配置自定义权限](/docs/appendix/configuring-custom-permissions)章节配置。
>-   使用LDAP认证方式，需要在创建后端时配置authenticationMode参数，参考[配置存储后端](/docs/basic-services/storage-backend-management/configuring-the-storage-backend)中的参数说明。
>-   基于最小权限原则和系统安全要求，不推荐使用“超级管理员”角色下的用户。

