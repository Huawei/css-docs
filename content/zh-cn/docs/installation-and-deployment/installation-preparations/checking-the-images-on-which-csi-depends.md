---
title: "检查CSI依赖的镜像"
linkTitle: "检查CSI依赖的镜像"
description: 
weight: 7
---

华为CSI安装过程中需要依赖下表中的镜像，若集群中的所有worker节点已连接互联网且能够在线拉取镜像，则可跳过本章节。若集群中的节点无法连接互联网，则请根据使用的Kubernetes版本，下载对应的镜像文件并上传到镜像仓库中或者导入Kubernetes集群的所有worker节点中。

huawei-csi-controller服务依赖的sidecar镜像：livenessprobe、csi-provisioner、csi-attacher、csi-resizer、csi-snapshotter、snapshot-controller、storage-backend-controller、storage-backend-sidecar、huawei-csi-driver和huawei-csi-extender。huawei-csi-node服务依赖的sidecar镜像：livenessprobe、csi-node-driver-registrar和huawei-csi-driver。

关于每个镜像的功能和详情，请参考下表。

**表 1**  Huawei CSI依赖的镜像

<a name="table1554616217465"></a>
<table><thead align="left"><tr id="row5547102174612"><th class="cellrowborder" valign="top" width="14.87%" id="mcps1.2.5.1.1"><p id="zh-cn_topic_0214996140_p166064474810"><a name="zh-cn_topic_0214996140_p166064474810"></a><a name="zh-cn_topic_0214996140_p166064474810"></a>容器名称</p>
</th>
<th class="cellrowborder" valign="top" width="30.73%" id="mcps1.2.5.1.2"><p id="zh-cn_topic_0214996140_p26601644124817"><a name="zh-cn_topic_0214996140_p26601644124817"></a><a name="zh-cn_topic_0214996140_p26601644124817"></a>容器镜像</p>
</th>
<th class="cellrowborder" valign="top" width="9.58%" id="mcps1.2.5.1.3"><p id="p19298315112219"><a name="p19298315112219"></a><a name="p19298315112219"></a>K8s版本要求</p>
</th>
<th class="cellrowborder" valign="top" width="44.82%" id="mcps1.2.5.1.4"><p id="zh-cn_topic_0214996140_p26601744104814"><a name="zh-cn_topic_0214996140_p26601744104814"></a><a name="zh-cn_topic_0214996140_p26601744104814"></a>功能描述</p>
</th>
</tr>
</thead>
<tbody><tr id="row9547192114619"><td class="cellrowborder" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p86601044154812"><a name="zh-cn_topic_0214996140_p86601044154812"></a><a name="zh-cn_topic_0214996140_p86601044154812"></a>livenessprobe</p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0214996140_p166034494817"><a name="zh-cn_topic_0214996140_p166034494817"></a><a name="zh-cn_topic_0214996140_p166034494817"></a><span id="text11297103912718"><a name="text11297103912718"></a><a name="text11297103912718"></a>registry.k8s.io/sig-storage/livenessprobe:v2.12.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p16298171552216"><a name="p16298171552216"></a><a name="p16298171552216"></a>v1.16+</p>
</td>
<td class="cellrowborder" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p156604448485"><a name="zh-cn_topic_0214996140_p156604448485"></a><a name="zh-cn_topic_0214996140_p156604448485"></a>Kubernetes社区提供，提供用于监控CSI的健康状态，并上报给Kubernetes，使Kubernetes能够自动检测CSI程序的问题并重启Pod尝试修改该问题。</p>
</td>
</tr>
<tr id="row3136101118366"><td class="cellrowborder" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p11661204454815"><a name="zh-cn_topic_0214996140_p11661204454815"></a><a name="zh-cn_topic_0214996140_p11661204454815"></a>csi-resizer</p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0214996140_p18661134413484"><a name="zh-cn_topic_0214996140_p18661134413484"></a><a name="zh-cn_topic_0214996140_p18661134413484"></a><span id="text851664711713"><a name="text851664711713"></a><a name="text851664711713"></a>registry.k8s.io/sig-storage/csi-resizer:v1.9.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p1829841520229"><a name="p1829841520229"></a><a name="p1829841520229"></a>v1.16+</p>
</td>
<td class="cellrowborder" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p56611544104819"><a name="zh-cn_topic_0214996140_p56611544104819"></a><a name="zh-cn_topic_0214996140_p56611544104819"></a>Kubernetes社区提供，在扩容PVC时，调用CSI给PVC提供更多的存储容量空间。</p>
</td>
</tr>
<tr id="row020073517369"><td class="cellrowborder" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p866114415480"><a name="zh-cn_topic_0214996140_p866114415480"></a><a name="zh-cn_topic_0214996140_p866114415480"></a>csi-node-driver-registrar</p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0214996140_p1866215446487"><a name="zh-cn_topic_0214996140_p1866215446487"></a><a name="zh-cn_topic_0214996140_p1866215446487"></a><span id="text16401105212719"><a name="text16401105212719"></a><a name="text16401105212719"></a>registry.k8s.io/sig-storage/csi-node-driver-registrar:v2.9.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p4298121582211"><a name="p4298121582211"></a><a name="p4298121582211"></a>v1.16+</p>
</td>
<td class="cellrowborder" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p17663104412482"><a name="zh-cn_topic_0214996140_p17663104412482"></a><a name="zh-cn_topic_0214996140_p17663104412482"></a>Kubernetes社区提供，用于获取CSI信息，并通过kubelet的插件注册机制将节点注册到kubelet中，从而Kubernetes能够感知该节点与华为存储的对接。</p>
</td>
</tr>
<tr id="row324775233618"><td class="cellrowborder" rowspan="2" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p766184474818"><a name="zh-cn_topic_0214996140_p766184474818"></a><a name="zh-cn_topic_0214996140_p766184474818"></a>csi-snapshotter</p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="p18449610144812"><a name="p18449610144812"></a><a name="p18449610144812"></a><span id="text98761101187"><a name="text98761101187"></a><a name="text98761101187"></a>registry.k8s.io/sig-storage/csi-snapshotter:v6.3.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p62984158224"><a name="p62984158224"></a><a name="p62984158224"></a>v1.20+</p>
</td>
<td class="cellrowborder" rowspan="2" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p1661644164820"><a name="zh-cn_topic_0214996140_p1661644164820"></a><a name="zh-cn_topic_0214996140_p1661644164820"></a>Kubernetes社区提供，在创建/删除VolumeSnapshot时，调用CSI在存储侧完成快照的创建和删除。</p>
</td>
</tr>
<tr id="row1854381033716"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p202545710478"><a name="p202545710478"></a><a name="p202545710478"></a>registry.k8s.io/sig-storage/csi-snapshotter:v4.2.1</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1625145716473"><a name="p1625145716473"></a><a name="p1625145716473"></a>v1.17-v1.19</p>
</td>
</tr>
<tr id="row7643145710372"><td class="cellrowborder" rowspan="2" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p12661144444812"><a name="zh-cn_topic_0214996140_p12661144444812"></a><a name="zh-cn_topic_0214996140_p12661144444812"></a>snapshot-controller</p>
<p id="p82014388380"><a name="p82014388380"></a><a name="p82014388380"></a></p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="p12512182574812"><a name="p12512182574812"></a><a name="p12512182574812"></a><span id="text476319710811"><a name="text476319710811"></a><a name="text476319710811"></a>registry.k8s.io/sig-storage/snapshot-controller:v6.3.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p102011338113814"><a name="p102011338113814"></a><a name="p102011338113814"></a>v1.20+</p>
</td>
<td class="cellrowborder" rowspan="2" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p1066120440485"><a name="zh-cn_topic_0214996140_p1066120440485"></a><a name="zh-cn_topic_0214996140_p1066120440485"></a>Kubernetes社区提供，在创建/删除VolumeSnapshot时，监听Kubernetes API中关于VolumeSnapshot和VolumeSnapshotContent的对象，并触发csi-snapshotter在存储上完成快照的创建。</p>
</td>
</tr>
<tr id="row192011038193813"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1196613398484"><a name="p1196613398484"></a><a name="p1196613398484"></a>registry.k8s.io/sig-storage/snapshot-controller:v4.2.1</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p109662395488"><a name="p109662395488"></a><a name="p109662395488"></a>v1.17-v1.19</p>
</td>
</tr>
<tr id="row175917813402"><td class="cellrowborder" rowspan="3" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="p97594894014"><a name="p97594894014"></a><a name="p97594894014"></a>csi-provisioner</p>
<p id="p18457125104116"><a name="p18457125104116"></a><a name="p18457125104116"></a></p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="p127598810403"><a name="p127598810403"></a><a name="p127598810403"></a><span id="text0989151113816"><a name="text0989151113816"></a><a name="text0989151113816"></a>registry.k8s.io/sig-storage/csi-provisioner:v3.6.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p1675913824011"><a name="p1675913824011"></a><a name="p1675913824011"></a>v1.20+</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="p1375911811407"><a name="p1375911811407"></a><a name="p1375911811407"></a>Kubernetes社区提供，用于完成PVC创建/删除。</p>
<a name="zh-cn_topic_0214996140_ul966013445485"></a><a name="zh-cn_topic_0214996140_ul966013445485"></a><ul id="zh-cn_topic_0214996140_ul966013445485"><li>在创建PVC时，调用huawei-csi-controller服务在存储上创建LUN/文件系统作为PV。</li><li>在删除PVC时，调用huawei-csi-controller服务在存储上删除该PV对应的LUN/文件系统。</li></ul>
</td>
</tr>
<tr id="row13547021134610"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p866017444487"><a name="zh-cn_topic_0214996140_p866017444487"></a><a name="zh-cn_topic_0214996140_p866017444487"></a>registry.k8s.io/sig-storage/csi-provisioner:v3.0.0</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p3298815142213"><a name="p3298815142213"></a><a name="p3298815142213"></a>v1.17-v1.19</p>
</td>
</tr>
<tr id="row1745712516419"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p845762517411"><a name="p845762517411"></a><a name="p845762517411"></a>quay.io/k8scsi/csi-provisioner:v1.4.0</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p8457112515416"><a name="p8457112515416"></a><a name="p8457112515416"></a>v1.16.x</p>
</td>
</tr>
<tr id="row13547122114466"><td class="cellrowborder" rowspan="2" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p76611044114813"><a name="zh-cn_topic_0214996140_p76611044114813"></a><a name="zh-cn_topic_0214996140_p76611044114813"></a>csi-attacher</p>
<p id="p19287224398"><a name="p19287224398"></a><a name="p19287224398"></a></p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="p10146135017914"><a name="p10146135017914"></a><a name="p10146135017914"></a><span id="text101571318583"><a name="text101571318583"></a><a name="text101571318583"></a>registry.k8s.io/sig-storage/csi-attacher:v4.4.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p829851592214"><a name="p829851592214"></a><a name="p829851592214"></a>v1.17+</p>
</td>
<td class="cellrowborder" rowspan="2" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p20661184444810"><a name="zh-cn_topic_0214996140_p20661184444810"></a><a name="zh-cn_topic_0214996140_p20661184444810"></a>在创建/删除Pod时，调用huawei-csi-controller服务执行Publish/Unpublish Volume操作。</p>
<p id="p1928716214391"><a name="p1928716214391"></a><a name="p1928716214391"></a></p>
</td>
</tr>
<tr id="row32879215395"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1328711216396"><a name="p1328711216396"></a><a name="p1328711216396"></a>quay.io/k8scsi/csi-attacher:v1.2.1</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p528782173916"><a name="p528782173916"></a><a name="p528782173916"></a>v.1.16.x</p>
</td>
</tr>
<tr id="row17451125324615"><td class="cellrowborder" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="p845185320464"><a name="p845185320464"></a><a name="p845185320464"></a>storage-backend-controller</p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="p2045111538468"><a name="p2045111538468"></a><a name="p2045111538468"></a>storage-backend-controller:<span id="ph97067019519"><a name="ph97067019519"></a><a name="ph97067019519"></a>4.8.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p10451353174612"><a name="p10451353174612"></a><a name="p10451353174612"></a>v1.16+</p>
</td>
<td class="cellrowborder" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="p1945112532465"><a name="p1945112532465"></a><a name="p1945112532465"></a>华为CSI软件包提供、用于管理storageBackendClaim资源。</p>
</td>
</tr>
<tr id="row93065617462"><td class="cellrowborder" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="p183045684613"><a name="p183045684613"></a><a name="p183045684613"></a>storage-backend-sidecar</p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="p193075611465"><a name="p193075611465"></a><a name="p193075611465"></a>storage-backend-sidecar:<span id="ph391581875114"><a name="ph391581875114"></a><a name="ph391581875114"></a>4.8.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p133011564464"><a name="p133011564464"></a><a name="p133011564464"></a>v1.16+</p>
</td>
<td class="cellrowborder" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="p103065654616"><a name="p103065654616"></a><a name="p103065654616"></a>华为CSI软件包提供、用于管理storageBackendContent资源。</p>
</td>
</tr>
<tr id="row14278140184816"><td class="cellrowborder" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="p62781704483"><a name="p62781704483"></a><a name="p62781704483"></a>huawei-csi-driver</p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="p152781708484"><a name="p152781708484"></a><a name="p152781708484"></a>huawei-csi:<span id="ph46871220155110"><a name="ph46871220155110"></a><a name="ph46871220155110"></a>4.8.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p2278704483"><a name="p2278704483"></a><a name="p2278704483"></a>v1.16+</p>
</td>
<td class="cellrowborder" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="p42782008484"><a name="p42782008484"></a><a name="p42782008484"></a>华为CSI软件包提供、用于提供华为CSI支持的所有特性。</p>
</td>
</tr>
<tr id="row17271523123216"><td class="cellrowborder" valign="top" width="14.87%" headers="mcps1.2.5.1.1 "><p id="p10728202303212"><a name="p10728202303212"></a><a name="p10728202303212"></a>huawei-csi-extender</p>
</td>
<td class="cellrowborder" valign="top" width="30.73%" headers="mcps1.2.5.1.2 "><p id="p6728112311324"><a name="p6728112311324"></a><a name="p6728112311324"></a>huawei-csi-extender:<span id="ph527132313515"><a name="ph527132313515"></a><a name="ph527132313515"></a>4.8.0</span></p>
</td>
<td class="cellrowborder" valign="top" width="9.58%" headers="mcps1.2.5.1.3 "><p id="p1072862312323"><a name="p1072862312323"></a><a name="p1072862312323"></a>v1.16+</p>
</td>
<td class="cellrowborder" valign="top" width="44.82%" headers="mcps1.2.5.1.4 "><p id="p197281123143210"><a name="p197281123143210"></a><a name="p197281123143210"></a>华为CSI软件包提供、用于提供华为CSI的扩展特性。</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>集群若未连接互联网，需要手动下载容器镜像并上传到集群中，具体操作请参考[下载容器镜像](/docs/common-operations/downloading-a-container-image)。

