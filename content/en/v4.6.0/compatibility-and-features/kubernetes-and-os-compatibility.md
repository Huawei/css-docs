---
title: "Kubernetes and OS Compatibility"
linkTitle: "Kubernetes and OS Compatibility"
description: 
weight: 1
---

Huawei CSI plug-in supports the following container management platforms.

**Table  1**  Supported container management platforms

<a name="table1074710451516"></a>
<table><thead align="left"><tr id="row474794517118"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p107476451618"><a name="p107476451618"></a><a name="p107476451618"></a>Container Management Platform</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p1574820451312"><a name="p1574820451312"></a><a name="p1574820451312"></a>Version</p>
</th>
</tr>
</thead>
<tbody><tr id="row774818457119"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p774815451619"><a name="p774815451619"></a><a name="p774815451619"></a>Kubernetes</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p1074815457112"><a name="p1074815457112"></a><a name="p1074815457112"></a>1.16 to 1.31</p>
</td>
</tr>
<tr id="row1374812458110"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p15748194519116"><a name="p15748194519116"></a><a name="p15748194519116"></a>Red Hat OpenShift Container Platform</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p1774819451114"><a name="p1774819451114"></a><a name="p1774819451114"></a>4.6 EUS, 4.7, 4.8, 4.9, 4.10, 4.11, 4.12, 4.13, 4.14, 4.15, 4.16, 4.17</p>
</td>
</tr>
<tr id="row1526064545317"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p1426094595313"><a name="p1426094595313"></a><a name="p1426094595313"></a>Tanzu Kubernetes Grid Integrated</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p626054555310"><a name="p626054555310"></a><a name="p626054555310"></a>TKGI 1.14.1, TKGI 1.15, TKGI 1.16, TKGI 1.17, TKGI 1.18</p>
</td>
</tr>
<tr id="row117973419355"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p1118023483511"><a name="p1118023483511"></a><a name="p1118023483511"></a>CCE Agile</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p418018342356"><a name="p418018342356"></a><a name="p418018342356"></a>22.3.2</p>
</td>
</tr>
<tr id="row2097213814106"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p6972113831015"><a name="p6972113831015"></a><a name="p6972113831015"></a>CCE</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p79726387102"><a name="p79726387102"></a><a name="p79726387102"></a>22.9.5</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   The connection between Huawei CSI and Tanzu Kubernetes supports only the centralized storage NAS scenario. For the related FAQ, see  [Common Problems and Solutions for Interconnecting with the Tanzu Kubernetes Cluster](/docs/troubleshooting/common-problems-and-solutions-for-interconnecting-with-the-tanzu-kubernetes-cluster).
>-   The connection between Huawei CSI and CCE or CCE Agile supports only centralized storage.

The following table lists the OSs and multipathing software supported by the Huawei CSI plug-in.

**Table  2**  Supported host OSs and multipathing software versions

<a name="table133422378818"></a>
<table><thead align="left"><tr id="row83438371381"><th class="cellrowborder" valign="top" width="21%" id="mcps1.2.5.1.1"><p id="p334317371186"><a name="p334317371186"></a><a name="p334317371186"></a>OS Name</p>
</th>
<th class="cellrowborder" valign="top" width="23%" id="mcps1.2.5.1.2"><p id="p1534317371812"><a name="p1534317371812"></a><a name="p1534317371812"></a>OS Version</p>
</th>
<th class="cellrowborder" valign="top" width="27%" id="mcps1.2.5.1.3"><p id="p20513132412163"><a name="p20513132412163"></a><a name="p20513132412163"></a>Native DM-Multipath Version</p>
</th>
<th class="cellrowborder" valign="top" width="28.999999999999996%" id="mcps1.2.5.1.4"><p id="p5519020131610"><a name="p5519020131610"></a><a name="p5519020131610"></a>Huawei UltraPath Version</p>
</th>
</tr>
</thead>
<tbody><tr id="row10343137688"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p174422515917"><a name="p174422515917"></a><a name="p174422515917"></a>CentOS x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p714515424912"><a name="p714515424912"></a><a name="p714515424912"></a>7.6, 7.7, 7.9</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p9513142418162"><a name="p9513142418162"></a><a name="p9513142418162"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p951912207160"><a name="p951912207160"></a><a name="p951912207160"></a>UltraPath 31.1.0, supporting FC/iSCSI</p>
</td>
</tr>
<tr id="row126961850188"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p66968571811"><a name="p66968571811"></a><a name="p66968571811"></a>CentOS x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p146964518186"><a name="p146964518186"></a><a name="p146964518186"></a>8.2, 8.4</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p7696154184"><a name="p7696154184"></a><a name="p7696154184"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p3696175101811"><a name="p3696175101811"></a><a name="p3696175101811"></a>UltraPath 31.1.0, supporting FC/iSCSI</p>
<p id="p13433122917188"><a name="p13433122917188"></a><a name="p13433122917188"></a>UltraPath-NVMe 31.1.RC8, supporting NVMe over RoCE/NVMe over FC</p>
</td>
</tr>
<tr id="row462220559496"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p8622205534918"><a name="p8622205534918"></a><a name="p8622205534918"></a>CentOS ARM</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p162295519499"><a name="p162295519499"></a><a name="p162295519499"></a>7.6</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1571627205016"><a name="p1571627205016"></a><a name="p1571627205016"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p92831342165018"><a name="p92831342165018"></a><a name="p92831342165018"></a>Not supported</p>
</td>
</tr>
<tr id="row338018570509"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p65591473511"><a name="p65591473511"></a><a name="p65591473511"></a>Rocky Linux x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p175591079513"><a name="p175591079513"></a><a name="p175591079513"></a>8.6</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1355913785117"><a name="p1355913785117"></a><a name="p1355913785117"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p05591714513"><a name="p05591714513"></a><a name="p05591714513"></a>UltraPath 31.2.1, supporting NVMe over RoCE</p>
</td>
</tr>
<tr id="row33431037682"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p184420254915"><a name="p184420254915"></a><a name="p184420254915"></a>SUSE 15 x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p2014514429912"><a name="p2014514429912"></a><a name="p2014514429912"></a>SP2, SP3</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p351302411165"><a name="p351302411165"></a><a name="p351302411165"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p43207517196"><a name="p43207517196"></a><a name="p43207517196"></a>UltraPath 31.1.0, supporting FC/iSCSI</p>
<p id="p1232018541915"><a name="p1232018541915"></a><a name="p1232018541915"></a>UltraPath-NVMe 31.1.RC8, supporting NVMe over RoCE/NVMe over FC</p>
</td>
</tr>
<tr id="row10343113716818"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p7442251798"><a name="p7442251798"></a><a name="p7442251798"></a>Red Hat CoreOS x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p1214517426916"><a name="p1214517426916"></a><a name="p1214517426916"></a>4.6, 4.7, 4.8, 4.9, 4.10, 4.11, 4.12, 4.13, 4.14, 4.15, 4.16, 4.17</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p115134245168"><a name="p115134245168"></a><a name="p115134245168"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p19519220141616"><a name="p19519220141616"></a><a name="p19519220141616"></a>Not supported</p>
</td>
</tr>
<tr id="row234312371784"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p24411253910"><a name="p24411253910"></a><a name="p24411253910"></a>Ubuntu x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p141451428911"><a name="p141451428911"></a><a name="p141451428911"></a>18.04, 20.04, 22.04</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p751392431616"><a name="p751392431616"></a><a name="p751392431616"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p351992071616"><a name="p351992071616"></a><a name="p351992071616"></a>Not supported</p>
</td>
</tr>
<tr id="row1279582641416"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p7795172661419"><a name="p7795172661419"></a><a name="p7795172661419"></a>Ubuntu ARM</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p14796182613148"><a name="p14796182613148"></a><a name="p14796182613148"></a>22.04</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p173292051151419"><a name="p173292051151419"></a><a name="p173292051151419"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p83292514146"><a name="p83292514146"></a><a name="p83292514146"></a>Not supported</p>
</td>
</tr>
<tr id="row10343173719816"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p11441251399"><a name="p11441251399"></a><a name="p11441251399"></a>Kylin x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p114517420917"><a name="p114517420917"></a><a name="p114517420917"></a>7.6, V10 SP1, V10 SP2, V10 SP3</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p851302401613"><a name="p851302401613"></a><a name="p851302401613"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p6519820151615"><a name="p6519820151615"></a><a name="p6519820151615"></a>UltraPath 31.2.0, supporting FC/iSCSI<sup id="sup1712945141917"><a name="sup1712945141917"></a><a name="sup1712945141917"></a>1</sup></p>
</td>
</tr>
<tr id="row514418498117"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p0144174981113"><a name="p0144174981113"></a><a name="p0144174981113"></a>Kylin ARM</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p121441149121117"><a name="p121441149121117"></a><a name="p121441149121117"></a>V10 SP1, V10 SP2, V10 SP3</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1351318249164"><a name="p1351318249164"></a><a name="p1351318249164"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p35196203166"><a name="p35196203166"></a><a name="p35196203166"></a>UltraPath 31.3.0, supporting iSCSI<sup id="sup185591937155114"><a name="sup185591937155114"></a><a name="sup185591937155114"></a>2</sup></p>
</td>
</tr>
<tr id="row110899123112"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p16108109203112"><a name="p16108109203112"></a><a name="p16108109203112"></a>Debian x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p1310859163119"><a name="p1310859163119"></a><a name="p1310859163119"></a>9, 11, 12</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p91081299314"><a name="p91081299314"></a><a name="p91081299314"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p410816943110"><a name="p410816943110"></a><a name="p410816943110"></a>Not supported</p>
</td>
</tr>
<tr id="row257753715216"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p15577537165212"><a name="p15577537165212"></a><a name="p15577537165212"></a>EulerOS x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p15771637195210"><a name="p15771637195210"></a><a name="p15771637195210"></a>V2R9, V2R10, V2R11, V2R12</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p14470145615315"><a name="p14470145615315"></a><a name="p14470145615315"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p14701656125313"><a name="p14701656125313"></a><a name="p14701656125313"></a>Not supported</p>
</td>
</tr>
<tr id="row292017416534"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p7920841155312"><a name="p7920841155312"></a><a name="p7920841155312"></a>EulerOS ARM</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p1792014110534"><a name="p1792014110534"></a><a name="p1792014110534"></a>V2R10, V2R12</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p10150157115312"><a name="p10150157115312"></a><a name="p10150157115312"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p415055725312"><a name="p415055725312"></a><a name="p415055725312"></a>Not supported</p>
</td>
</tr>
<tr id="row10474145114011"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p174741753402"><a name="p174741753402"></a><a name="p174741753402"></a>UOS x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p134758574010"><a name="p134758574010"></a><a name="p134758574010"></a>V20</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p34753524019"><a name="p34753524019"></a><a name="p34753524019"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p947516574016"><a name="p947516574016"></a><a name="p947516574016"></a>Not supported</p>
</td>
</tr>
<tr id="row867984183816"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p1967912417382"><a name="p1967912417382"></a><a name="p1967912417382"></a>BC-Linux ARM</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p1967915493815"><a name="p1967915493815"></a><a name="p1967915493815"></a>21.10</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1467974163820"><a name="p1467974163820"></a><a name="p1467974163820"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p26792411387"><a name="p26792411387"></a><a name="p26792411387"></a>Not supported</p>
</td>
</tr>
<tr id="row4144193719134"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p914473714135"><a name="p914473714135"></a><a name="p914473714135"></a>Anolis OS<sup id="sup19737153002119"><a name="sup19737153002119"></a><a name="sup19737153002119"></a>3</sup></p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p1214473771310"><a name="p1214473771310"></a><a name="p1214473771310"></a>8.8</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p14144837121313"><a name="p14144837121313"></a><a name="p14144837121313"></a>Delivered with the OS, supporting iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p16145113761319"><a name="p16145113761319"></a><a name="p16145113761319"></a>Not supported</p>
</td>
</tr>
<tr id="row1941116615225"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p17411196152216"><a name="p17411196152216"></a><a name="p17411196152216"></a>OpenEuler x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p241115619228"><a name="p241115619228"></a><a name="p241115619228"></a>22.03 LTS SP1</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1541176132218"><a name="p1541176132218"></a><a name="p1541176132218"></a>Delivered with the OS, supporting iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p9412146192210"><a name="p9412146192210"></a><a name="p9412146192210"></a>Not supported</p>
</td>
</tr>
<tr id="row8426659627"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.5.1.1 "><p id="p411217583481"><a name="p411217583481"></a><a name="p411217583481"></a>Red Hat Enterprise Linux x86_64</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.5.1.2 "><p id="p91129587480"><a name="p91129587480"></a><a name="p91129587480"></a>8.6, 8.7, 8.8, 8.9, 8.10, 9.4</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p141128581485"><a name="p141128581485"></a><a name="p141128581485"></a>Delivered with the OS, supporting FC/iSCSI</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p511205884815"><a name="p511205884815"></a><a name="p511205884815"></a>Not supported</p>
</td>
</tr>
</tbody>
</table>

Note 1: Only Kylin x86\_64 V10 SP2 supports UltraPath 31.2.0.

Note 2: Only Kylin ARM V10 SP3 supports UltraPath 31.3.0.

Note 3: Anolis OS supports only OceanStor Pacific storage.

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>For DM-Multipath 0.7, some virtual devices may not be displayed in the command output after the  **multipathd show maps**  command is executed. Therefore, you are advised to use version 0.8 or later.
>You can query the DM-Multipath version in either of the following ways:
>-   If the rpm package is used, run the  **rpm -qa | grep multipath**  or  **rpm -qa | grep device-mapper**  command.
>-   If the deb package is used, run the  **dpkg -l | grep multipath**  command.

