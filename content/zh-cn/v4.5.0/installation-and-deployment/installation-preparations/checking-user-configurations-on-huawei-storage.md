---
title: "检查华为存储上的用户配置"
linkTitle: "检查华为存储上的用户配置"
description: 
weight: 3
---

当华为存储接入容器平台后，华为CSI需要在华为存储上根据业务要求，管理存储资源，如创建卷、映射卷等操作。此时，华为CSI需要使用华为存储上已经创建的用户和华为存储进行通信。针对不同存储设备所需要的用户信息如下表所示。

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
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0214996140_p1532116144311"><a name="zh-cn_topic_0214996140_p1532116144311"></a><a name="zh-cn_topic_0214996140_p1532116144311"></a>本地用户</p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row217510214456"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p1517512154515"><a name="zh-cn_topic_0214996140_p1517512154515"></a><a name="zh-cn_topic_0214996140_p1517512154515"></a>租户用户</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p161761824457"><a name="zh-cn_topic_0214996140_p161761824457"></a><a name="zh-cn_topic_0214996140_p161761824457"></a>租户管理员</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p71768264519"><a name="zh-cn_topic_0214996140_p71768264519"></a><a name="zh-cn_topic_0214996140_p71768264519"></a>管理员</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p111763294517"><a name="zh-cn_topic_0214996140_p111763294517"></a><a name="zh-cn_topic_0214996140_p111763294517"></a>本地用户</p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row66361943164415"><td class="cellrowborder" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p66361843174416"><a name="zh-cn_topic_0214996140_p66361843174416"></a><a name="zh-cn_topic_0214996140_p66361843174416"></a>OceanStor Dorado V3</p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p84081753144412"><a name="zh-cn_topic_0214996140_p84081753144412"></a><a name="zh-cn_topic_0214996140_p84081753144412"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p1293710272510"><a name="zh-cn_topic_0214996140_p1293710272510"></a><a name="zh-cn_topic_0214996140_p1293710272510"></a>管理员</p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p18937927175118"><a name="zh-cn_topic_0214996140_p18937927175118"></a><a name="zh-cn_topic_0214996140_p18937927175118"></a>管理员</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0214996140_p293715275511"><a name="zh-cn_topic_0214996140_p293715275511"></a><a name="zh-cn_topic_0214996140_p293715275511"></a>本地用户</p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row163581026142419"><td class="cellrowborder" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p335942672413"><a name="zh-cn_topic_0214996140_p335942672413"></a><a name="zh-cn_topic_0214996140_p335942672413"></a>OceanStor 6.1.3, 6.1.5, 6.1.6, 6.1.7, 6.1.8</p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p1129916445242"><a name="zh-cn_topic_0214996140_p1129916445242"></a><a name="zh-cn_topic_0214996140_p1129916445242"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p12299194414240"><a name="zh-cn_topic_0214996140_p12299194414240"></a><a name="zh-cn_topic_0214996140_p12299194414240"></a>管理员/自定义角色<sup id="sup19138264283"><a name="sup19138264283"></a><a name="sup19138264283"></a>1</sup></p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p329910440244"><a name="zh-cn_topic_0214996140_p329910440244"></a><a name="zh-cn_topic_0214996140_p329910440244"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0214996140_p11299154442413"><a name="zh-cn_topic_0214996140_p11299154442413"></a><a name="zh-cn_topic_0214996140_p11299154442413"></a>本地用户</p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row143210168434"><td class="cellrowborder" rowspan="2" valign="top" width="29.13%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p23218164437"><a name="zh-cn_topic_0214996140_p23218164437"></a><a name="zh-cn_topic_0214996140_p23218164437"></a>OceanStor Dorado 6.1.0, 6.1.2, 6.1.3, 6.1.5, 6.1.6, 6.1.7, 6.1.8</p>
</td>
<td class="cellrowborder" valign="top" width="20.97%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p13170324518"><a name="zh-cn_topic_0214996140_p13170324518"></a><a name="zh-cn_topic_0214996140_p13170324518"></a>系统用户</p>
</td>
<td class="cellrowborder" valign="top" width="17.119999999999997%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p2045125319467"><a name="zh-cn_topic_0214996140_p2045125319467"></a><a name="zh-cn_topic_0214996140_p2045125319467"></a>管理员/自定义角色<sup id="sup221894516187"><a name="sup221894516187"></a><a name="sup221894516187"></a>1</sup></p>
</td>
<td class="cellrowborder" valign="top" width="17.61%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p845125344614"><a name="zh-cn_topic_0214996140_p845125344614"></a><a name="zh-cn_topic_0214996140_p845125344614"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.17%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0214996140_p124515539466"><a name="zh-cn_topic_0214996140_p124515539466"></a><a name="zh-cn_topic_0214996140_p124515539466"></a>本地用户</p>
</td>
</tr>
<tr id="zh-cn_topic_0214996140_row9761201434620"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0214996140_p117072165112"><a name="zh-cn_topic_0214996140_p117072165112"></a><a name="zh-cn_topic_0214996140_p117072165112"></a>租户用户</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0214996140_p14452053154610"><a name="zh-cn_topic_0214996140_p14452053154610"></a><a name="zh-cn_topic_0214996140_p14452053154610"></a>租户管理员</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0214996140_p15451053204616"><a name="zh-cn_topic_0214996140_p15451053204616"></a><a name="zh-cn_topic_0214996140_p15451053204616"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0214996140_p1745125312460"><a name="zh-cn_topic_0214996140_p1745125312460"></a><a name="zh-cn_topic_0214996140_p1745125312460"></a>本地用户</p>
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
</tbody>
</table>

-   注释1 使用自定义角色，需要给角色配置权限，最小权限请参考[配置自定义权限](/v4.5.0/appendix/configuring-custom-permissions)章节配置。

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>不推荐使用“超级管理员”角色下的用户。

