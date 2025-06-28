---
title: "Helm values.yaml参数说明"
linkTitle: "Helm values.yaml参数说明"
description: 
weight: 3
---

在使用Helm安装CSI时，需要您根据部署时需要使用的特性准备Helm工程的values.yaml文件。华为CSI已经在软件包的helm/esdk目录下提供了values.yaml模板文件。

本章节将详细说明values.yaml中的配置项以及典型场景下的后端配置示例。

## images参数配置说明{#section128441143205716}

values.yaml中的images配置项主要配置华为CSI运行时依赖的组件镜像信息。需要配置的参数如下：

**表 1**  images配置项说明

<a name="table8452547161918"></a>
<table><thead align="left"><tr id="row645218479197"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="p5269141514410"><a name="p5269141514410"></a><a name="p5269141514410"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="29.17%" id="mcps1.2.5.1.2"><p id="p026931524418"><a name="p026931524418"></a><a name="p026931524418"></a>描述</p>
</th>
<th class="cellrowborder" valign="top" width="5.89%" id="mcps1.2.5.1.3"><p id="p826915156447"><a name="p826915156447"></a><a name="p826915156447"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="39.94%" id="mcps1.2.5.1.4"><p id="p1426921517443"><a name="p1426921517443"></a><a name="p1426921517443"></a>默认值</p>
</th>
</tr>
</thead>
<tbody><tr id="row1156694303912"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000001324610777_p15337145719458"><a name="zh-cn_topic_0000001324610777_p15337145719458"></a><a name="zh-cn_topic_0000001324610777_p15337145719458"></a>images.huaweiCSIService</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000001324610777_p173371357144517"><a name="zh-cn_topic_0000001324610777_p173371357144517"></a><a name="zh-cn_topic_0000001324610777_p173371357144517"></a>huawei-csi镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000001324610777_p1633715710454"><a name="zh-cn_topic_0000001324610777_p1633715710454"></a><a name="zh-cn_topic_0000001324610777_p1633715710454"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000001324610777_p16337457154513"><a name="zh-cn_topic_0000001324610777_p16337457154513"></a><a name="zh-cn_topic_0000001324610777_p16337457154513"></a>huawei-csi:<span id="ph09001410174913"><a name="ph09001410174913"></a><a name="ph09001410174913"></a>4.8.0</span></p>
</td>
</tr>
<tr id="row12803747173911"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p1616415034013"><a name="p1616415034013"></a><a name="p1616415034013"></a>images.storageBackendSidecar</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="p1080311470395"><a name="p1080311470395"></a><a name="p1080311470395"></a>华为后端管理sidecar镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="p1380304783914"><a name="p1380304783914"></a><a name="p1380304783914"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="p1380384793918"><a name="p1380384793918"></a><a name="p1380384793918"></a>storage-backend-sidecar:<span id="ph111931741165212"><a name="ph111931741165212"></a><a name="ph111931741165212"></a>4.8.0</span></p>
</td>
</tr>
<tr id="row1089864973918"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p46581916408"><a name="p46581916408"></a><a name="p46581916408"></a>images.storageBackendController</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="p6899124910393"><a name="p6899124910393"></a><a name="p6899124910393"></a>华为后端管理控制器镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="p2089912497394"><a name="p2089912497394"></a><a name="p2089912497394"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="p1489984963919"><a name="p1489984963919"></a><a name="p1489984963919"></a>storage-backend-controller:<span id="ph21391643115214"><a name="ph21391643115214"></a><a name="ph21391643115214"></a>4.8.0</span></p>
</td>
</tr>
<tr id="row12997135033511"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p199785073518"><a name="p199785073518"></a><a name="p199785073518"></a>images.huaweiCSIExtender</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="p1299785010355"><a name="p1299785010355"></a><a name="p1299785010355"></a>huawei-csi-extender镜像</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="p17997350183511"><a name="p17997350183511"></a><a name="p17997350183511"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="p15997155019358"><a name="p15997155019358"></a><a name="p15997155019358"></a>huawei-csi-extender:<span id="ph8385174515525"><a name="ph8385174515525"></a><a name="ph8385174515525"></a>4.8.0</span></p>
</td>
</tr>
<tr id="row185030354414"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000001324610777_p4337185713453"><a name="zh-cn_topic_0000001324610777_p4337185713453"></a><a name="zh-cn_topic_0000001324610777_p4337185713453"></a>images.sidecar.livenessProbe</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000001324610777_p9337195764510"><a name="zh-cn_topic_0000001324610777_p9337195764510"></a><a name="zh-cn_topic_0000001324610777_p9337195764510"></a><a href="https://kubernetes-csi.github.io/docs/livenessprobe.html" target="_blank" rel="noopener noreferrer">livenessprobe</a> sidecar镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000001324610777_p1633725724512"><a name="zh-cn_topic_0000001324610777_p1633725724512"></a><a name="zh-cn_topic_0000001324610777_p1633725724512"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000001324610777_p1733785714453"><a name="zh-cn_topic_0000001324610777_p1733785714453"></a><a name="zh-cn_topic_0000001324610777_p1733785714453"></a><span id="text9419635285"><a name="text9419635285"></a><a name="text9419635285"></a>registry.k8s.io/sig-storage/livenessprobe:v2.12.0</span></p>
</td>
</tr>
<tr id="row345374716195"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000001324610777_p333755715453"><a name="zh-cn_topic_0000001324610777_p333755715453"></a><a name="zh-cn_topic_0000001324610777_p333755715453"></a>images.sidecar.provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000001324610777_p183372575454"><a name="zh-cn_topic_0000001324610777_p183372575454"></a><a name="zh-cn_topic_0000001324610777_p183372575454"></a><a href="https://kubernetes-csi.github.io/docs/external-provisioner.html" target="_blank" rel="noopener noreferrer">csi-provisioner</a> sidecar镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000001324610777_p1033711577456"><a name="zh-cn_topic_0000001324610777_p1033711577456"></a><a name="zh-cn_topic_0000001324610777_p1033711577456"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000001324610777_p15337125716458"><a name="zh-cn_topic_0000001324610777_p15337125716458"></a><a name="zh-cn_topic_0000001324610777_p15337125716458"></a><span id="text01042496818"><a name="text01042496818"></a><a name="text01042496818"></a>registry.k8s.io/sig-storage/csi-provisioner:v3.6.0</span></p>
</td>
</tr>
<tr id="row145324715192"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000001324610777_p19337155744517"><a name="zh-cn_topic_0000001324610777_p19337155744517"></a><a name="zh-cn_topic_0000001324610777_p19337155744517"></a>images.sidecar.attacher</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000001324610777_p18337145744510"><a name="zh-cn_topic_0000001324610777_p18337145744510"></a><a name="zh-cn_topic_0000001324610777_p18337145744510"></a><a href="https://kubernetes-csi.github.io/docs/external-attacher.html" target="_blank" rel="noopener noreferrer">csi-attacher</a> sidecar镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000001324610777_p18337155714518"><a name="zh-cn_topic_0000001324610777_p18337155714518"></a><a name="zh-cn_topic_0000001324610777_p18337155714518"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000001324610777_p7337457134516"><a name="zh-cn_topic_0000001324610777_p7337457134516"></a><a name="zh-cn_topic_0000001324610777_p7337457134516"></a><span id="text1381095717816"><a name="text1381095717816"></a><a name="text1381095717816"></a>registry.k8s.io/sig-storage/csi-attacher:v4.4.0</span></p>
</td>
</tr>
<tr id="row94532047111915"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000001324610777_p13337175711459"><a name="zh-cn_topic_0000001324610777_p13337175711459"></a><a name="zh-cn_topic_0000001324610777_p13337175711459"></a>images.sidecar.resizer</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000001324610777_p53377576452"><a name="zh-cn_topic_0000001324610777_p53377576452"></a><a name="zh-cn_topic_0000001324610777_p53377576452"></a><a href="https://kubernetes-csi.github.io/docs/external-resizer.html" target="_blank" rel="noopener noreferrer">csi-resizer</a> sidecar镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000001324610777_p93375572452"><a name="zh-cn_topic_0000001324610777_p93375572452"></a><a name="zh-cn_topic_0000001324610777_p93375572452"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000001324610777_p153371257184518"><a name="zh-cn_topic_0000001324610777_p153371257184518"></a><a name="zh-cn_topic_0000001324610777_p153371257184518"></a><span id="text11193167917"><a name="text11193167917"></a><a name="text11193167917"></a>registry.k8s.io/sig-storage/csi-resizer:v1.9.0</span></p>
</td>
</tr>
<tr id="row9453124771918"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000001324610777_p833785764516"><a name="zh-cn_topic_0000001324610777_p833785764516"></a><a name="zh-cn_topic_0000001324610777_p833785764516"></a>images.sidecar.snapshotter</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000001324610777_p73371257134514"><a name="zh-cn_topic_0000001324610777_p73371257134514"></a><a name="zh-cn_topic_0000001324610777_p73371257134514"></a><a href="https://kubernetes-csi.github.io/docs/external-snapshotter.html" target="_blank" rel="noopener noreferrer">csi-snapshotter</a> sidecar镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000001324610777_p1833765712454"><a name="zh-cn_topic_0000001324610777_p1833765712454"></a><a name="zh-cn_topic_0000001324610777_p1833765712454"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000001324610777_p1033755713457"><a name="zh-cn_topic_0000001324610777_p1033755713457"></a><a name="zh-cn_topic_0000001324610777_p1033755713457"></a><span id="text101211917799"><a name="text101211917799"></a><a name="text101211917799"></a>registry.k8s.io/sig-storage/csi-snapshotter:v6.3.0</span></p>
</td>
</tr>
<tr id="row196140122014"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000001324610777_p10337557174514"><a name="zh-cn_topic_0000001324610777_p10337557174514"></a><a name="zh-cn_topic_0000001324610777_p10337557174514"></a>images.sidecar.snapshotController</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000001324610777_p163372057164518"><a name="zh-cn_topic_0000001324610777_p163372057164518"></a><a name="zh-cn_topic_0000001324610777_p163372057164518"></a><a href="https://kubernetes-csi.github.io/docs/snapshot-controller.html" target="_blank" rel="noopener noreferrer">snapshot-controller</a> sidecar镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000001324610777_p10337457134511"><a name="zh-cn_topic_0000001324610777_p10337457134511"></a><a name="zh-cn_topic_0000001324610777_p10337457134511"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000001324610777_p0337195724520"><a name="zh-cn_topic_0000001324610777_p0337195724520"></a><a name="zh-cn_topic_0000001324610777_p0337195724520"></a><span id="text28281726693"><a name="text28281726693"></a><a name="text28281726693"></a>registry.k8s.io/sig-storage/snapshot-controller:v6.3.0</span></p>
</td>
</tr>
<tr id="row84580467201"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000001324610777_p10337165714454"><a name="zh-cn_topic_0000001324610777_p10337165714454"></a><a name="zh-cn_topic_0000001324610777_p10337165714454"></a>images.sidecar.registrar</p>
</td>
<td class="cellrowborder" valign="top" width="29.17%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000001324610777_p153371957164512"><a name="zh-cn_topic_0000001324610777_p153371957164512"></a><a name="zh-cn_topic_0000001324610777_p153371957164512"></a><a href="https://kubernetes-csi.github.io/docs/node-driver-registrar.html" target="_blank" rel="noopener noreferrer">csi-node-driver-registrar</a> sidecar镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="5.89%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000001324610777_p83371057164510"><a name="zh-cn_topic_0000001324610777_p83371057164510"></a><a name="zh-cn_topic_0000001324610777_p83371057164510"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="39.94%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000001324610777_p1833711578459"><a name="zh-cn_topic_0000001324610777_p1833711578459"></a><a name="zh-cn_topic_0000001324610777_p1833711578459"></a><span id="text116171043295"><a name="text116171043295"></a><a name="text116171043295"></a>registry.k8s.io/sig-storage/csi-node-driver-registrar:v2.9.0</span></p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   huaweiCSIService、storageBackendSidecar、storageBackendController、huaweiCSIExtender参数的值，请参考[上传华为CSI镜像](/docs/installation-and-deployment/installation-preparations/uploading-a-huawei-csi-image)章节的说明，使用最终生成镜像的名称和版本。
>-   其他sidecar镜像参数，请参考[检查CSI依赖的镜像](/docs/installation-and-deployment/installation-preparations/checking-the-images-on-which-csi-depends)章节的说明，使用最终上传的镜像的名称和版本。

## controller参数配置说明{#section94006111587}

controller配置项用于配置huawei-csi-controller组件的相关配置。

**表 2**  controller配置项说明

<a name="table813124411459"></a>
<table><thead align="left"><tr id="row16131444124517"><th class="cellrowborder" valign="top" width="24.94%" id="mcps1.2.6.1.1"><p id="p413174420459"><a name="p413174420459"></a><a name="p413174420459"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="24.94%" id="mcps1.2.6.1.2"><p id="p1313111444458"><a name="p1313111444458"></a><a name="p1313111444458"></a>描述</p>
</th>
<th class="cellrowborder" valign="top" width="8.88%" id="mcps1.2.6.1.3"><p id="p8131114464512"><a name="p8131114464512"></a><a name="p8131114464512"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="7.430000000000001%" id="mcps1.2.6.1.4"><p id="p8963122912427"><a name="p8963122912427"></a><a name="p8963122912427"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="33.81%" id="mcps1.2.6.1.5"><p id="p1413154464517"><a name="p1413154464517"></a><a name="p1413154464517"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row19652123211576"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p1765213214571"><a name="p1765213214571"></a><a name="p1765213214571"></a>controller.controllerCount</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p16652123285711"><a name="p16652123285711"></a><a name="p16652123285711"></a>huawei-csi-controller组件的副本数</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p665233210576"><a name="p665233210576"></a><a name="p665233210576"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p9963429194216"><a name="p9963429194216"></a><a name="p9963429194216"></a>1</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p0677122985016"><a name="p0677122985016"></a><a name="p0677122985016"></a>Kubernetes版本低于v1.17时，由于Kubernetes社区提供的csi-provisioner sidecar镜像不支持--leader-election参数，只能通过单副本方式部署huawei-csi-controller组件。</p>
<p id="p8606174713335"><a name="p8606174713335"></a><a name="p8606174713335"></a>因此，当Kubernetes版本低于v1.17版本时，该参数仅支持配置为1。</p>
</td>
</tr>
<tr id="row395265716343"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p936624344510"><a name="p936624344510"></a><a name="p936624344510"></a>controller.volumeNamePrefix</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p19782351165214"><a name="p19782351165214"></a><a name="p19782351165214"></a>PV名称的前缀，默认值为pvc，即创建的PV名称为：<strong id="b1581811715282"><a name="b1581811715282"></a><a name="b1581811715282"></a>pvc-</strong><em id="i9942511192812"><a name="i9942511192812"></a><a name="i9942511192812"></a>&lt;uuid&gt;</em>。前缀必须满足<a href="https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/names#dns-subdomain-names" target="_blank" rel="noopener noreferrer">DNS 子域名</a>的命名规则，且PV名称总长度不得超过253个字符。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p236613438456"><a name="p236613438456"></a><a name="p236613438456"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p9963729104213"><a name="p9963729104213"></a><a name="p9963729104213"></a>pvc</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p17366114313450"><a name="p17366114313450"></a><a name="p17366114313450"></a>对应的provisioner参数名称为：--volume-name-prefix。</p>
<p id="p9406581769"><a name="p9406581769"></a><a name="p9406581769"></a>建议前缀不超过20个字符。</p>
<p id="p828611423316"><a name="p828611423316"></a><a name="p828611423316"></a>详细配置请参考<a href="https://github.com/kubernetes-csi/external-provisioner/tree/release-3.0" target="_blank" rel="noopener noreferrer">配置PV名称前缀</a>。</p>
<a name="ul517195262412"></a><a name="ul517195262412"></a><ul id="ul517195262412"><li>对接后端是OceanStor V5 SAN时，建议前缀不超过5个字符。</li><li>对接后端是OceanStor V5 NAS存储时，前缀只能包含小写字母、'-'，以及数字。</li><li>对接后端是OceanStor Dorado和OceanStor存储时，前缀只能包含小写字母、'-'，以及数字。</li><li>对接后端是OceanStor Pacific系列存储时，前缀只能包含字母、数字、“_”、“-”和“.”，且总长度限制为58字符。</li><li>对接后端是FusionStorage Block时，前缀只能包含字母、数字、“_”和“-”，且总长度限制为58字符。</li></ul>
</td>
</tr>
<tr id="row17543658153417"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p11543175819348"><a name="p11543175819348"></a><a name="p11543175819348"></a>controller.webhookPort</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p6544165816346"><a name="p6544165816346"></a><a name="p6544165816346"></a>webhook服务使用的端口。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p5544158143412"><a name="p5544158143412"></a><a name="p5544158143412"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p85441258193419"><a name="p85441258193419"></a><a name="p85441258193419"></a>4433</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p5544458203416"><a name="p5544458203416"></a><a name="p5544458203416"></a>如果存在端口冲突可修改为其他未占用的端口。</p>
</td>
</tr>
<tr id="row12842142319395"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p1184332318398"><a name="p1184332318398"></a><a name="p1184332318398"></a>controller.snapshot.enabled</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p12348183444610"><a name="zh-cn_topic_0000001324610777_p12348183444610"></a><a name="zh-cn_topic_0000001324610777_p12348183444610"></a>是否开启快照特性。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p1434811345468"><a name="zh-cn_topic_0000001324610777_p1434811345468"></a><a name="zh-cn_topic_0000001324610777_p1434811345468"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p139638293427"><a name="p139638293427"></a><a name="p139638293427"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p6556044384"><a name="p6556044384"></a><a name="p6556044384"></a>如果要使用快照相关功能，请开启该特性。</p>
<p id="zh-cn_topic_0000001324610777_p13348113418464"><a name="zh-cn_topic_0000001324610777_p13348113418464"></a><a name="zh-cn_topic_0000001324610777_p13348113418464"></a>要求Kubernetes版本高于v1.17。</p>
</td>
</tr>
<tr id="row0284172210403"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p16956162712407"><a name="p16956162712407"></a><a name="p16956162712407"></a>controller.resizer.enabled</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p126618381404"><a name="p126618381404"></a><a name="p126618381404"></a>是否开启扩容特性。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p17284192214010"><a name="p17284192214010"></a><a name="p17284192214010"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p16963142912429"><a name="p16963142912429"></a><a name="p16963142912429"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p728462210401"><a name="p728462210401"></a><a name="p728462210401"></a>要求Kubernetes版本高于v1.16。</p>
</td>
</tr>
<tr id="row14131154414450"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p913144454511"><a name="p913144454511"></a><a name="p913144454511"></a>controller.nodeSelector</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p613154419453"><a name="p613154419453"></a><a name="p613154419453"></a>huawei-csi-controller的节点选择器。配置后huawei-csi-controller仅会调度到存在该标签的节点上。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p17131644194514"><a name="p17131644194514"></a><a name="p17131644194514"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p396342918424"><a name="p396342918424"></a><a name="p396342918424"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p1184116225568"><a name="p1184116225568"></a><a name="p1184116225568"></a>节点选择器的详细说明请参考：<a href="https://kubernetes.io/zh-cn/docs/tasks/configure-pod-container/assign-pods-nodes/#create-a-pod-scheduled-to-chosen-node" target="_blank" rel="noopener noreferrer">将 Pod 分配给节点</a></p>
</td>
</tr>
<tr id="row1413194413458"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p21311144164510"><a name="p21311144164510"></a><a name="p21311144164510"></a>controller.tolerations</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p313164414456"><a name="p313164414456"></a><a name="p313164414456"></a>huawei-csi-controller的污点容忍。配置后huawei-csi-controller能够容忍节点上存在该污点。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p1513184416453"><a name="p1513184416453"></a><a name="p1513184416453"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p4963142911421"><a name="p4963142911421"></a><a name="p4963142911421"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p313104444510"><a name="p313104444510"></a><a name="p313104444510"></a>污点和容忍度的详细说明请参考：<a href="https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/" target="_blank" rel="noopener noreferrer">污点和容忍度</a></p>
</td>
</tr>
<tr id="row17847615817"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p8848121511116"><a name="p8848121511116"></a><a name="p8848121511116"></a>controller.affinity</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p198481915714"><a name="p198481915714"></a><a name="p198481915714"></a>huawei-csi-controller的节点亲和性。配置后huawei-csi-controller会优先调度到存在该标签的节点上。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p9848111516113"><a name="p9848111516113"></a><a name="p9848111516113"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p2848111511114"><a name="p2848111511114"></a><a name="p2848111511114"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p16849315113"><a name="p16849315113"></a><a name="p16849315113"></a>节点亲和性的详细说明请参考：<a href="https://kubernetes.io/zh-cn/docs/concepts/scheduling-eviction/assign-pod-node/#node-affinity" target="_blank" rel="noopener noreferrer">将Pod指派给节点</a></p>
</td>
</tr>
<tr id="row3514131652617"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p1751521602612"><a name="p1751521602612"></a><a name="p1751521602612"></a>controller.livenessProbePort</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p10515161682619"><a name="p10515161682619"></a><a name="p10515161682619"></a>huawei-csi-controller的存活性探针端口，用于健康检查。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p75156162261"><a name="p75156162261"></a><a name="p75156162261"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p13515121652612"><a name="p13515121652612"></a><a name="p13515121652612"></a>9808</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p651512160261"><a name="p651512160261"></a><a name="p651512160261"></a>如果存在端口冲突可修改为其他未占用的端口</p>
</td>
</tr>
<tr id="row48331747163918"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p15785239105916"><a name="p15785239105916"></a><a name="p15785239105916"></a>controller.csiExtender.volumeModify.enabled</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p1978533911594"><a name="p1978533911594"></a><a name="p1978533911594"></a>是否开启PVC变更特性。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p97851739145912"><a name="p97851739145912"></a><a name="p97851739145912"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p97858393599"><a name="p97858393599"></a><a name="p97858393599"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p5785133913594"><a name="p5785133913594"></a><a name="p5785133913594"></a>如果要PVC变更相关功能，请开启该特性。</p>
</td>
</tr>
<tr id="row188026506397"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p8802950113914"><a name="p8802950113914"></a><a name="p8802950113914"></a>controller.csiExtender.volumeModify.retryBaseDelay</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p6460153193217"><a name="p6460153193217"></a><a name="p6460153193217"></a>PVC变更创建任务失败时的最小重试间隔。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p1480315509397"><a name="p1480315509397"></a><a name="p1480315509397"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p19803750203914"><a name="p19803750203914"></a><a name="p19803750203914"></a>5s</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p9803450103911"><a name="p9803450103911"></a><a name="p9803450103911"></a>建议使用默认值。</p>
</td>
</tr>
<tr id="row126131354143917"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p166131654153915"><a name="p166131654153915"></a><a name="p166131654153915"></a>controller.csiExtender.volumeModify.retryMaxDelay</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p2613254143910"><a name="p2613254143910"></a><a name="p2613254143910"></a>PVC变更创建任务失败时的最大重试间隔。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p76131254133915"><a name="p76131254133915"></a><a name="p76131254133915"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p261312546395"><a name="p261312546395"></a><a name="p261312546395"></a>5m</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p1861319542396"><a name="p1861319542396"></a><a name="p1861319542396"></a>建议使用默认值。</p>
</td>
</tr>
<tr id="row12879850114019"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p168791450184014"><a name="p168791450184014"></a><a name="p168791450184014"></a>controller.csiExtender.volumeModify.reconcileDelay</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p6879185044013"><a name="p6879185044013"></a><a name="p6879185044013"></a>调协VolumeModifyClaim对象的间隔。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p2879350154017"><a name="p2879350154017"></a><a name="p2879350154017"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p4879185015409"><a name="p4879185015409"></a><a name="p4879185015409"></a>1s</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p148791050164015"><a name="p148791050164015"></a><a name="p148791050164015"></a>建议使用默认值。</p>
</td>
</tr>
<tr id="row1683154018317"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p12683194016316"><a name="p12683194016316"></a><a name="p12683194016316"></a>controller.exportCsiService.enabled</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p6683240539"><a name="p6683240539"></a><a name="p6683240539"></a>是否开启将CSI服务运行在Kubernetes集群的Service上。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p2068311401835"><a name="p2068311401835"></a><a name="p2068311401835"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p1168416401330"><a name="p1168416401330"></a><a name="p1168416401330"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p10684104015313"><a name="p10684104015313"></a><a name="p10684104015313"></a>开启后，Kubernetes集群内其他服务可通过gRPC访问CSI服务。</p>
</td>
</tr>
<tr id="row851953511189"><td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.1 "><p id="p16519735141815"><a name="p16519735141815"></a><a name="p16519735141815"></a>controller.exportCsiService.port</p>
</td>
<td class="cellrowborder" valign="top" width="24.94%" headers="mcps1.2.6.1.2 "><p id="p1151953541816"><a name="p1151953541816"></a><a name="p1151953541816"></a>CSI服务运行在Kubernetes集群的Service时使用的端口。</p>
</td>
<td class="cellrowborder" valign="top" width="8.88%" headers="mcps1.2.6.1.3 "><p id="p65201635201816"><a name="p65201635201816"></a><a name="p65201635201816"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="7.430000000000001%" headers="mcps1.2.6.1.4 "><p id="p1052033591813"><a name="p1052033591813"></a><a name="p1052033591813"></a>9090</p>
</td>
<td class="cellrowborder" valign="top" width="33.81%" headers="mcps1.2.6.1.5 "><p id="p175201135121817"><a name="p175201135121817"></a><a name="p175201135121817"></a>如果存在端口冲突可修改为其他未占用的端口。</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>当controller.snapshot.enabled参数配置为true时，需要安装“helm/crd/snapshot-crds”目录下的卷快照CRD资源。

## node参数配置说明{#section374014171581}

node配置项用于配置huawei-csi-node组件的相关配置。

**表 3**  node配置项说明

<a name="table1496310165912"></a>
<table><thead align="left"><tr id="row29633012599"><th class="cellrowborder" valign="top" width="23.119999999999997%" id="mcps1.2.6.1.1"><p id="p79636005914"><a name="p79636005914"></a><a name="p79636005914"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="23.119999999999997%" id="mcps1.2.6.1.2"><p id="p2096319015915"><a name="p2096319015915"></a><a name="p2096319015915"></a>描述</p>
</th>
<th class="cellrowborder" valign="top" width="8.99%" id="mcps1.2.6.1.3"><p id="p89631908591"><a name="p89631908591"></a><a name="p89631908591"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="22.3%" id="mcps1.2.6.1.4"><p id="p988145513479"><a name="p988145513479"></a><a name="p988145513479"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="22.470000000000002%" id="mcps1.2.6.1.5"><p id="p4963110135913"><a name="p4963110135913"></a><a name="p4963110135913"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row20933131914418"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p109331619134413"><a name="p109331619134413"></a><a name="p109331619134413"></a>node.maxVolumesPerNode</p>
</td>
<td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.2 "><p id="p18933181915444"><a name="p18933181915444"></a><a name="p18933181915444"></a>节点可使用的华为CSI发放卷的最大数量。不定义或者配置为0时则认为不限制。</p>
<p id="p11105463112"><a name="p11105463112"></a><a name="p11105463112"></a>如果创建Pod时，指定 nodeName，则会忽略该配置。</p>
</td>
<td class="cellrowborder" valign="top" width="8.99%" headers="mcps1.2.6.1.3 "><p id="p209331197442"><a name="p209331197442"></a><a name="p209331197442"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="22.3%" headers="mcps1.2.6.1.4 "><p id="p19881955164717"><a name="p19881955164717"></a><a name="p19881955164717"></a>100</p>
</td>
<td class="cellrowborder" valign="top" width="22.470000000000002%" headers="mcps1.2.6.1.5 "><p id="p11933219144415"><a name="p11933219144415"></a><a name="p11933219144415"></a>详细说明请参考：<a href="https://kubernetes-csi.github.io/docs/volume-limits.html" target="_blank" rel="noopener noreferrer">Volume Limits</a></p>
</td>
</tr>
<tr id="row3963706590"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p996314085919"><a name="p996314085919"></a><a name="p996314085919"></a>node.nodeSelector</p>
</td>
<td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.2 "><p id="p1796314045917"><a name="p1796314045917"></a><a name="p1796314045917"></a>huawei-csi-node的节点选择器。配置后huawei-csi-node仅会调度到存在该标签的节点上。</p>
</td>
<td class="cellrowborder" valign="top" width="8.99%" headers="mcps1.2.6.1.3 "><p id="p1296314015593"><a name="p1296314015593"></a><a name="p1296314015593"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="22.3%" headers="mcps1.2.6.1.4 "><p id="p1488185514471"><a name="p1488185514471"></a><a name="p1488185514471"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="22.470000000000002%" headers="mcps1.2.6.1.5 "><p id="p1896315018593"><a name="p1896315018593"></a><a name="p1896315018593"></a>节点选择器的详细说明请参考：<a href="https://kubernetes.io/zh-cn/docs/tasks/configure-pod-container/assign-pods-nodes/#create-a-pod-scheduled-to-chosen-node" target="_blank" rel="noopener noreferrer">将 Pod 分配给节点</a></p>
</td>
</tr>
<tr id="row12963106592"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p16964150115915"><a name="p16964150115915"></a><a name="p16964150115915"></a>node.tolerations</p>
</td>
<td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.2 "><p id="p8964205599"><a name="p8964205599"></a><a name="p8964205599"></a>huawei-csi-node的污点容忍。配置后huawei-csi-node能够容忍节点上存在该污点。</p>
</td>
<td class="cellrowborder" valign="top" width="8.99%" headers="mcps1.2.6.1.3 "><p id="p396420185912"><a name="p396420185912"></a><a name="p396420185912"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="22.3%" headers="mcps1.2.6.1.4 "><pre class="screen" id="screen135832458509"><a name="screen135832458509"></a><a name="screen135832458509"></a>- key: "node.kubernetes.io/memory-pressure"
  operator: "Exists"
  effect: "NoExecute"
- key: "node.kubernetes.io/disk-pressure"
  operator: "Exists"
  effect: "NoExecute"
- key: "node.kubernetes.io/network-unavailable"
  operator: "Exists"
  effect: "NoExecute"</pre>
</td>
<td class="cellrowborder" valign="top" width="22.470000000000002%" headers="mcps1.2.6.1.5 "><p id="p596410085910"><a name="p596410085910"></a><a name="p596410085910"></a>污点和容忍度的详细说明请参考：<a href="https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/" target="_blank" rel="noopener noreferrer">污点和容忍度</a></p>
</td>
</tr>
<tr id="row102254208186"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p72561621151816"><a name="p72561621151816"></a><a name="p72561621151816"></a>node.affinity</p>
</td>
<td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.2 "><p id="p725652110183"><a name="p725652110183"></a><a name="p725652110183"></a>huawei-csi-node的节点亲和性。配置后huawei-csi-node会优先调度到存在该标签的节点上。</p>
</td>
<td class="cellrowborder" valign="top" width="8.99%" headers="mcps1.2.6.1.3 "><p id="p1725672141811"><a name="p1725672141811"></a><a name="p1725672141811"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="22.3%" headers="mcps1.2.6.1.4 "><p id="p1625642110181"><a name="p1625642110181"></a><a name="p1625642110181"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="22.470000000000002%" headers="mcps1.2.6.1.5 "><p id="p132561421101814"><a name="p132561421101814"></a><a name="p132561421101814"></a>节点亲和性的详细说明请参考：<a href="https://kubernetes.io/zh-cn/docs/concepts/scheduling-eviction/assign-pod-node/#node-affinity" target="_blank" rel="noopener noreferrer">将Pod指派给节点</a></p>
</td>
</tr>
<tr id="row14307151183115"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p93081173119"><a name="p93081173119"></a><a name="p93081173119"></a>node.livenessProbePort</p>
</td>
<td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.2 "><p id="p17308619318"><a name="p17308619318"></a><a name="p17308619318"></a>huawei-csi-node的存活性探针端口，用于健康检查。</p>
</td>
<td class="cellrowborder" valign="top" width="8.99%" headers="mcps1.2.6.1.3 "><p id="p130881103113"><a name="p130881103113"></a><a name="p130881103113"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="22.3%" headers="mcps1.2.6.1.4 "><p id="p93087163114"><a name="p93087163114"></a><a name="p93087163114"></a>9800</p>
</td>
<td class="cellrowborder" valign="top" width="22.470000000000002%" headers="mcps1.2.6.1.5 "><p id="p83087111317"><a name="p83087111317"></a><a name="p83087111317"></a>如果存在端口冲突可修改为其他未占用的端口</p>
</td>
</tr>
<tr id="row746313162504"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p16463161625019"><a name="p16463161625019"></a><a name="p16463161625019"></a>node.kubeletVolumeDevicesDirName</p>
</td>
<td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.2 "><p id="p6463616145011"><a name="p6463616145011"></a><a name="p6463616145011"></a>kubelet挂载块设备时的目录名称。</p>
</td>
<td class="cellrowborder" valign="top" width="8.99%" headers="mcps1.2.6.1.3 "><p id="p54631016125019"><a name="p54631016125019"></a><a name="p54631016125019"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="22.3%" headers="mcps1.2.6.1.4 "><p id="p104631416105012"><a name="p104631416105012"></a><a name="p104631416105012"></a>volumeDevices</p>
</td>
<td class="cellrowborder" valign="top" width="22.470000000000002%" headers="mcps1.2.6.1.5 "><p id="p19463181655017"><a name="p19463181655017"></a><a name="p19463181655017"></a>当一个块设备被成功挂载之后，挂载路径的目录结构应该如下所示：</p>
<pre class="screen" id="screen64610218547"><a name="screen64610218547"></a><a name="screen64610218547"></a>/var/lib/kubelet/plugins/kubernetes.io/csi/{kubeletVolumeDevicesDirName}/publish/{specName}/{podUID}</pre>
</td>
</tr>
</tbody>
</table>

## csiDriver参数配置说明{#section389443385812}

csiDriver配置项包括了华为CSI运行时的基本配置，如华为驱动名称、多路径类型等配置信息。

**表 4**  csiDriver配置项说明

<a name="table188162213437"></a>
<table><thead align="left"><tr id="row188161721154311"><th class="cellrowborder" valign="top" width="20.22%" id="mcps1.2.6.1.1"><p id="p113341565437"><a name="p113341565437"></a><a name="p113341565437"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="22.259999999999998%" id="mcps1.2.6.1.2"><p id="p53343568434"><a name="p53343568434"></a><a name="p53343568434"></a>描述</p>
</th>
<th class="cellrowborder" valign="top" width="13.84%" id="mcps1.2.6.1.3"><p id="p4334185615436"><a name="p4334185615436"></a><a name="p4334185615436"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="15.790000000000001%" id="mcps1.2.6.1.4"><p id="p203341356204315"><a name="p203341356204315"></a><a name="p203341356204315"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="27.889999999999997%" id="mcps1.2.6.1.5"><p id="p13933793502"><a name="p13933793502"></a><a name="p13933793502"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row15816202134316"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p6337105774514"><a name="zh-cn_topic_0000001324610777_p6337105774514"></a><a name="zh-cn_topic_0000001324610777_p6337105774514"></a>csiDriver.driverName</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p833725774517"><a name="zh-cn_topic_0000001324610777_p833725774517"></a><a name="zh-cn_topic_0000001324610777_p833725774517"></a>注册的驱动名称。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p833755774515"><a name="zh-cn_topic_0000001324610777_p833755774515"></a><a name="zh-cn_topic_0000001324610777_p833755774515"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p1033725711455"><a name="zh-cn_topic_0000001324610777_p1033725711455"></a><a name="zh-cn_topic_0000001324610777_p1033725711455"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><a name="ul107492610815"></a><a name="ul107492610815"></a><ul id="ul107492610815"><li>直接使用默认值。</li><li>对于CCE Agile平台，需要修改该字段，例如：csi.oceanstor.com。</li></ul>
</td>
</tr>
<tr id="row28161921154319"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p183378575452"><a name="zh-cn_topic_0000001324610777_p183378575452"></a><a name="zh-cn_topic_0000001324610777_p183378575452"></a>csiDriver.endpoint</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p17337165718459"><a name="zh-cn_topic_0000001324610777_p17337165718459"></a><a name="zh-cn_topic_0000001324610777_p17337165718459"></a>通信端点。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p17337195712454"><a name="zh-cn_topic_0000001324610777_p17337195712454"></a><a name="zh-cn_topic_0000001324610777_p17337195712454"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p1333735717456"><a name="zh-cn_topic_0000001324610777_p1333735717456"></a><a name="zh-cn_topic_0000001324610777_p1333735717456"></a>/csi/csi.sock</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p179331599508"><a name="p179331599508"></a><a name="p179331599508"></a>直接使用默认值。</p>
</td>
</tr>
<tr id="row1481682113430"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p033795717451"><a name="zh-cn_topic_0000001324610777_p033795717451"></a><a name="zh-cn_topic_0000001324610777_p033795717451"></a>csiDriver.connectorThreads</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p163371857164519"><a name="zh-cn_topic_0000001324610777_p163371857164519"></a><a name="zh-cn_topic_0000001324610777_p163371857164519"></a>最大并发扫盘/卸盘数。参数格式为整型，支持范围为1~10。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p12337757144515"><a name="zh-cn_topic_0000001324610777_p12337757144515"></a><a name="zh-cn_topic_0000001324610777_p12337757144515"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p2033755784512"><a name="zh-cn_topic_0000001324610777_p2033755784512"></a><a name="zh-cn_topic_0000001324610777_p2033755784512"></a>4</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p89333914502"><a name="p89333914502"></a><a name="p89333914502"></a>该值设置越大，同一时间单个节点中的针对多路径的扫盘、卸盘并发操作就越多。在使用DM-Multipath时，并发数过大可能会导致未知问题，影响整体时间。</p>
</td>
</tr>
<tr id="row9816112116433"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p2033795719452"><a name="zh-cn_topic_0000001324610777_p2033795719452"></a><a name="zh-cn_topic_0000001324610777_p2033795719452"></a>csiDriver.volumeUseMultipath</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p17337185774514"><a name="zh-cn_topic_0000001324610777_p17337185774514"></a><a name="zh-cn_topic_0000001324610777_p17337185774514"></a>是否使用多路径软件。参数格式为布尔值。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p5337135710452"><a name="zh-cn_topic_0000001324610777_p5337135710452"></a><a name="zh-cn_topic_0000001324610777_p5337135710452"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p11337205712459"><a name="zh-cn_topic_0000001324610777_p11337205712459"></a><a name="zh-cn_topic_0000001324610777_p11337205712459"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p793310955012"><a name="p793310955012"></a><a name="p793310955012"></a>强烈建议开启多路径软件，以增强存储链路的冗余度和性能。</p>
</td>
</tr>
<tr id="row481610211432"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p5337105710453"><a name="zh-cn_topic_0000001324610777_p5337105710453"></a><a name="zh-cn_topic_0000001324610777_p5337105710453"></a>csiDriver.scsiMultipathType</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p375115112223"><a name="zh-cn_topic_0000001324610777_p375115112223"></a><a name="zh-cn_topic_0000001324610777_p375115112223"></a>存储协议为fc/iscsi时，使用的多路径软件。支持配置如下参数：</p>
<a name="zh-cn_topic_0000001324610777_ul260012531222"></a><a name="zh-cn_topic_0000001324610777_ul260012531222"></a><ul id="zh-cn_topic_0000001324610777_ul260012531222"><li>DM-multipath</li><li>HW-UltraPath</li><li>HW-UltraPath-NVMe</li></ul>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p4337155712454"><a name="zh-cn_topic_0000001324610777_p4337155712454"></a><a name="zh-cn_topic_0000001324610777_p4337155712454"></a>当volumeUseMultipath为true时必填。</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p933775734517"><a name="zh-cn_topic_0000001324610777_p933775734517"></a><a name="zh-cn_topic_0000001324610777_p933775734517"></a>DM-multipath</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p4933189145013"><a name="p4933189145013"></a><a name="p4933189145013"></a>建议使用DM-multipath取值。</p>
</td>
</tr>
<tr id="row98161421144310"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p634703417465"><a name="zh-cn_topic_0000001324610777_p634703417465"></a><a name="zh-cn_topic_0000001324610777_p634703417465"></a>csiDriver.nvmeMultipathType</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p9347113414463"><a name="zh-cn_topic_0000001324610777_p9347113414463"></a><a name="zh-cn_topic_0000001324610777_p9347113414463"></a>存储协议为roce/fc-nvme时，使用的多路径软件。仅支持配置HW-UltraPath-NVMe。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p53471934114612"><a name="zh-cn_topic_0000001324610777_p53471934114612"></a><a name="zh-cn_topic_0000001324610777_p53471934114612"></a>当volumeUseMultipath为true时必填。</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p1434717343465"><a name="zh-cn_topic_0000001324610777_p1434717343465"></a><a name="zh-cn_topic_0000001324610777_p1434717343465"></a>HW-UltraPath-NVMe</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p199331895507"><a name="p199331895507"></a><a name="p199331895507"></a>-</p>
</td>
</tr>
<tr id="row1081711215431"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p53476342464"><a name="zh-cn_topic_0000001324610777_p53476342464"></a><a name="zh-cn_topic_0000001324610777_p53476342464"></a>csiDriver.scanVolumeTimeout</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p182891831165917"><a name="zh-cn_topic_0000001324610777_p182891831165917"></a><a name="zh-cn_topic_0000001324610777_p182891831165917"></a>在主机上使用DM-Multipath多路径时，等待多路径聚合的超时时间，支持范围为1~600，单位秒。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p14347734104616"><a name="zh-cn_topic_0000001324610777_p14347734104616"></a><a name="zh-cn_topic_0000001324610777_p14347734104616"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p173472348469"><a name="zh-cn_topic_0000001324610777_p173472348469"></a><a name="zh-cn_topic_0000001324610777_p173472348469"></a>3</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p6933189185018"><a name="p6933189185018"></a><a name="p6933189185018"></a>-</p>
</td>
</tr>
<tr id="row41249148199"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="p1912491441914"><a name="p1912491441914"></a><a name="p1912491441914"></a>csiDriver.execCommandTimeout</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="p15124161471913"><a name="p15124161471913"></a><a name="p15124161471913"></a>在主机上执行命令的超时时间</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="p712461420194"><a name="p712461420194"></a><a name="p712461420194"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="p412471411917"><a name="p412471411917"></a><a name="p412471411917"></a>30</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p8124314171910"><a name="p8124314171910"></a><a name="p8124314171910"></a>CSI插件在挂载，扩容盘符等场景下，需要运行一些主机命令，例如使用mount命令挂载文件系统。该配置用于控制执行单条命令的超时时间。</p>
</td>
</tr>
<tr id="row119848396573"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="p11985639165716"><a name="p11985639165716"></a><a name="p11985639165716"></a>csiDriver.enableRoCEConnect</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="p1098518397575"><a name="p1098518397575"></a><a name="p1098518397575"></a>使用RoCE协议时，是否开启CSI自动扫盘</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="p49852039145718"><a name="p49852039145718"></a><a name="p49852039145718"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="p89851639165717"><a name="p89851639165717"></a><a name="p89851639165717"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p798563914572"><a name="p798563914572"></a><a name="p798563914572"></a>如果使用外部工具建立RoCE连接，可以设置为false。例如：存储开启SNSD自动建连时，可以配置为false。</p>
</td>
</tr>
<tr id="row73274310332"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="p1460663514512"><a name="p1460663514512"></a><a name="p1460663514512"></a>csiDriver.allPathOnline</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="p46061935154513"><a name="p46061935154513"></a><a name="p46061935154513"></a>是否检查DM-Multipath软件聚合的路径数等于实际在线的路径数，支持配置如下参数：</p>
<a name="ul107341114134816"></a><a name="ul107341114134816"></a><ul id="ul107341114134816"><li>true：DM-Multipath软件聚合的路径数等于实际在线的路径数才满足盘符挂载条件。</li><li>false：默认不检查DM-Multipath软件聚合的路径数量，只要聚合出虚拟盘符，即满足盘符挂载条件。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="p4606133516456"><a name="p4606133516456"></a><a name="p4606133516456"></a>当csiDriver.scsiMultipathType为DM-multipath时必填。</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="p960673554519"><a name="p960673554519"></a><a name="p960673554519"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p126067351454"><a name="p126067351454"></a><a name="p126067351454"></a>-</p>
</td>
</tr>
<tr id="row14448563444"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p93478341469"><a name="zh-cn_topic_0000001324610777_p93478341469"></a><a name="zh-cn_topic_0000001324610777_p93478341469"></a>csiDriver.backendUpdateInterval</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p7347193474618"><a name="zh-cn_topic_0000001324610777_p7347193474618"></a><a name="zh-cn_topic_0000001324610777_p7347193474618"></a>后端能力的更新时间间隔，支持范围60~600，单位秒。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p1347634204613"><a name="zh-cn_topic_0000001324610777_p1347634204613"></a><a name="zh-cn_topic_0000001324610777_p1347634204613"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p9347034114612"><a name="zh-cn_topic_0000001324610777_p9347034114612"></a><a name="zh-cn_topic_0000001324610777_p9347034114612"></a>60</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p1293417910509"><a name="p1293417910509"></a><a name="p1293417910509"></a>-</p>
</td>
</tr>
<tr id="row744456104419"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p1434713454612"><a name="zh-cn_topic_0000001324610777_p1434713454612"></a><a name="zh-cn_topic_0000001324610777_p1434713454612"></a>csiDriver.controllerLogging.module</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p3624521162211"><a name="zh-cn_topic_0000001324610777_p3624521162211"></a><a name="zh-cn_topic_0000001324610777_p3624521162211"></a>controller日志记录类型。支持配置如下参数：</p>
<a name="zh-cn_topic_0000001324610777_ul06981143132310"></a><a name="zh-cn_topic_0000001324610777_ul06981143132310"></a><ul id="zh-cn_topic_0000001324610777_ul06981143132310"><li>file</li><li>console</li></ul>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p6347234114616"><a name="zh-cn_topic_0000001324610777_p6347234114616"></a><a name="zh-cn_topic_0000001324610777_p6347234114616"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p034743494615"><a name="zh-cn_topic_0000001324610777_p034743494615"></a><a name="zh-cn_topic_0000001324610777_p034743494615"></a>file</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p4934799502"><a name="p4934799502"></a><a name="p4934799502"></a>使用file选项时，日志将被保留在节点指定的目录下，当CSI所在的Pod被销毁时，日志仍然被保留。</p>
<p id="p067035825718"><a name="p067035825718"></a><a name="p067035825718"></a>使用console选项时，日志将被保留在CSI所在Pod的临时空间中，当CSI所在的Pod被销毁时，日志也随之被销毁。</p>
</td>
</tr>
<tr id="row19444564449"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p4347183444613"><a name="zh-cn_topic_0000001324610777_p4347183444613"></a><a name="zh-cn_topic_0000001324610777_p4347183444613"></a>csiDriver.controllerLogging.level</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p16417137154310"><a name="zh-cn_topic_0000001324610777_p16417137154310"></a><a name="zh-cn_topic_0000001324610777_p16417137154310"></a>controller日志输出级别。支持配置如下参数：</p>
<a name="zh-cn_topic_0000001324610777_ul1167154320240"></a><a name="zh-cn_topic_0000001324610777_ul1167154320240"></a><ul id="zh-cn_topic_0000001324610777_ul1167154320240"><li>debug</li><li>info</li><li>warning</li><li>error</li><li>fatal</li></ul>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p17347834154617"><a name="zh-cn_topic_0000001324610777_p17347834154617"></a><a name="zh-cn_topic_0000001324610777_p17347834154617"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p1834720346469"><a name="zh-cn_topic_0000001324610777_p1834720346469"></a><a name="zh-cn_topic_0000001324610777_p1834720346469"></a>info</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p139341498509"><a name="p139341498509"></a><a name="p139341498509"></a>-</p>
</td>
</tr>
<tr id="row5443565449"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p13471434164616"><a name="zh-cn_topic_0000001324610777_p13471434164616"></a><a name="zh-cn_topic_0000001324610777_p13471434164616"></a>csiDriver.controllerLogging.fileDir</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p10347153410468"><a name="zh-cn_topic_0000001324610777_p10347153410468"></a><a name="zh-cn_topic_0000001324610777_p10347153410468"></a>controller日志在file输出模式下的日志目录。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p0347534194610"><a name="zh-cn_topic_0000001324610777_p0347534194610"></a><a name="zh-cn_topic_0000001324610777_p0347534194610"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p103471434184614"><a name="zh-cn_topic_0000001324610777_p103471434184614"></a><a name="zh-cn_topic_0000001324610777_p103471434184614"></a>/var/log/huawei</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p1093411975015"><a name="p1093411975015"></a><a name="p1093411975015"></a>请确保该目录下有足够的空间保留日志。空间大小建议不小于200 MB。</p>
</td>
</tr>
<tr id="row1778411129457"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p17348134104614"><a name="zh-cn_topic_0000001324610777_p17348134104614"></a><a name="zh-cn_topic_0000001324610777_p17348134104614"></a>csiDriver.controllerLogging.fileSize</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p203487346467"><a name="zh-cn_topic_0000001324610777_p203487346467"></a><a name="zh-cn_topic_0000001324610777_p203487346467"></a>controller日志在file输出模式下单个日志文件大小。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p334833444618"><a name="zh-cn_topic_0000001324610777_p334833444618"></a><a name="zh-cn_topic_0000001324610777_p334833444618"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p134813417469"><a name="zh-cn_topic_0000001324610777_p134813417469"></a><a name="zh-cn_topic_0000001324610777_p134813417469"></a>20M</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p1093411995013"><a name="p1093411995013"></a><a name="p1093411995013"></a>-</p>
</td>
</tr>
<tr id="row4961918134510"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p1134873412462"><a name="zh-cn_topic_0000001324610777_p1134873412462"></a><a name="zh-cn_topic_0000001324610777_p1134873412462"></a>csiDriver.controllerLogging.maxBackups</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p53481034164619"><a name="zh-cn_topic_0000001324610777_p53481034164619"></a><a name="zh-cn_topic_0000001324610777_p53481034164619"></a>controller日志在file输出模式下日志文件备份上限。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p19348193414465"><a name="zh-cn_topic_0000001324610777_p19348193414465"></a><a name="zh-cn_topic_0000001324610777_p19348193414465"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p15348163419463"><a name="zh-cn_topic_0000001324610777_p15348163419463"></a><a name="zh-cn_topic_0000001324610777_p15348163419463"></a>9</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p12934890500"><a name="p12934890500"></a><a name="p12934890500"></a>-</p>
</td>
</tr>
<tr id="row1978411274511"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p1234812347465"><a name="zh-cn_topic_0000001324610777_p1234812347465"></a><a name="zh-cn_topic_0000001324610777_p1234812347465"></a>csiDriver.nodeLogging.module</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p2508115722612"><a name="zh-cn_topic_0000001324610777_p2508115722612"></a><a name="zh-cn_topic_0000001324610777_p2508115722612"></a>node日志记录类型。支持配置如下参数：</p>
<a name="zh-cn_topic_0000001324610777_ul35081257192610"></a><a name="zh-cn_topic_0000001324610777_ul35081257192610"></a><ul id="zh-cn_topic_0000001324610777_ul35081257192610"><li>file</li><li>console</li></ul>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p20348234114615"><a name="zh-cn_topic_0000001324610777_p20348234114615"></a><a name="zh-cn_topic_0000001324610777_p20348234114615"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p103486342462"><a name="zh-cn_topic_0000001324610777_p103486342462"></a><a name="zh-cn_topic_0000001324610777_p103486342462"></a>file</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p67624161807"><a name="p67624161807"></a><a name="p67624161807"></a>使用file选项时，日志将被保留在节点指定的目录下，当CSI所在的Pod被销毁时，日志仍然被保留。</p>
<p id="p1676211161707"><a name="p1676211161707"></a><a name="p1676211161707"></a>使用console选项时，日志将被保留在CSI所在Pod的临时空间中，当CSI所在的Pod被销毁时，日志也随之被销毁。</p>
</td>
</tr>
<tr id="row47847123452"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p1934818348469"><a name="zh-cn_topic_0000001324610777_p1934818348469"></a><a name="zh-cn_topic_0000001324610777_p1934818348469"></a>csiDriver.nodeLogging.level</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p1612112242711"><a name="zh-cn_topic_0000001324610777_p1612112242711"></a><a name="zh-cn_topic_0000001324610777_p1612112242711"></a>node日志输出级别。支持配置如下参数：</p>
<a name="zh-cn_topic_0000001324610777_ul1561292212717"></a><a name="zh-cn_topic_0000001324610777_ul1561292212717"></a><ul id="zh-cn_topic_0000001324610777_ul1561292212717"><li>debug</li><li>info</li><li>warning</li><li>error</li><li>fatal</li></ul>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p334873415469"><a name="zh-cn_topic_0000001324610777_p334873415469"></a><a name="zh-cn_topic_0000001324610777_p334873415469"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p7348113416469"><a name="zh-cn_topic_0000001324610777_p7348113416469"></a><a name="zh-cn_topic_0000001324610777_p7348113416469"></a>info</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p593459175013"><a name="p593459175013"></a><a name="p593459175013"></a>-</p>
</td>
</tr>
<tr id="row11785121220453"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p7348234104611"><a name="zh-cn_topic_0000001324610777_p7348234104611"></a><a name="zh-cn_topic_0000001324610777_p7348234104611"></a>csiDriver.nodeLogging.fileDir</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p1750544317272"><a name="zh-cn_topic_0000001324610777_p1750544317272"></a><a name="zh-cn_topic_0000001324610777_p1750544317272"></a>node日志在file输出模式下的日志目录。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p10348193494619"><a name="zh-cn_topic_0000001324610777_p10348193494619"></a><a name="zh-cn_topic_0000001324610777_p10348193494619"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p034893417469"><a name="zh-cn_topic_0000001324610777_p034893417469"></a><a name="zh-cn_topic_0000001324610777_p034893417469"></a>/var/log/huawei</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p1993429105012"><a name="p1993429105012"></a><a name="p1993429105012"></a>请确保该目录下有足够的空间保留日志。空间大小建议不小于200 MB。</p>
</td>
</tr>
<tr id="row078551284516"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p73486347467"><a name="zh-cn_topic_0000001324610777_p73486347467"></a><a name="zh-cn_topic_0000001324610777_p73486347467"></a>csiDriver.nodeLogging.fileSize</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p0505114315275"><a name="zh-cn_topic_0000001324610777_p0505114315275"></a><a name="zh-cn_topic_0000001324610777_p0505114315275"></a>node日志在file输出模式下单个日志文件大小。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p634819343466"><a name="zh-cn_topic_0000001324610777_p634819343466"></a><a name="zh-cn_topic_0000001324610777_p634819343466"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p19348234184616"><a name="zh-cn_topic_0000001324610777_p19348234184616"></a><a name="zh-cn_topic_0000001324610777_p19348234184616"></a>20M</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p1693417913501"><a name="p1693417913501"></a><a name="p1693417913501"></a>-</p>
</td>
</tr>
<tr id="row121518222466"><td class="cellrowborder" valign="top" width="20.22%" headers="mcps1.2.6.1.1 "><p id="p62151622154612"><a name="p62151622154612"></a><a name="p62151622154612"></a>csiDriver.nodeLogging.maxBackups</p>
</td>
<td class="cellrowborder" valign="top" width="22.259999999999998%" headers="mcps1.2.6.1.2 "><p id="p3215142212469"><a name="p3215142212469"></a><a name="p3215142212469"></a>node日志在file输出模式下日志文件备份上限。</p>
</td>
<td class="cellrowborder" valign="top" width="13.84%" headers="mcps1.2.6.1.3 "><p id="p1121582215465"><a name="p1121582215465"></a><a name="p1121582215465"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="15.790000000000001%" headers="mcps1.2.6.1.4 "><p id="p621572294611"><a name="p621572294611"></a><a name="p621572294611"></a>9</p>
</td>
<td class="cellrowborder" valign="top" width="27.889999999999997%" headers="mcps1.2.6.1.5 "><p id="p493411995018"><a name="p493411995018"></a><a name="p493411995018"></a>-</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>如果您的容器环境已经部署了华为CSI，请确保csiDriver.driverName的设置和之前部署时的配置保持一致。否则会导致系统中已存在的有华为CSI发放的卷/快照无法被新部署的华为CSI管理。

## 其他参数配置说明{#section11500468593}

其他配置项包括了CSI插件某些特性的开关或者镜像获取策略。

**表 5**  其他配置项说明

<a name="table258712427285"></a>
<table><thead align="left"><tr id="row1858810426284"><th class="cellrowborder" valign="top" width="23.119999999999997%" id="mcps1.2.6.1.1"><p id="p65678447283"><a name="p65678447283"></a><a name="p65678447283"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="29.709999999999997%" id="mcps1.2.6.1.2"><p id="p9567104432815"><a name="p9567104432815"></a><a name="p9567104432815"></a>描述</p>
</th>
<th class="cellrowborder" valign="top" width="6.329999999999999%" id="mcps1.2.6.1.3"><p id="p656710441284"><a name="p656710441284"></a><a name="p656710441284"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="17.44%" id="mcps1.2.6.1.4"><p id="p056794462811"><a name="p056794462811"></a><a name="p056794462811"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="23.400000000000002%" id="mcps1.2.6.1.5"><p id="p248511121014"><a name="p248511121014"></a><a name="p248511121014"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row10113115012328"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p15337957144510"><a name="zh-cn_topic_0000001324610777_p15337957144510"></a><a name="zh-cn_topic_0000001324610777_p15337957144510"></a>kubernetes.namespace</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p123372572455"><a name="zh-cn_topic_0000001324610777_p123372572455"></a><a name="zh-cn_topic_0000001324610777_p123372572455"></a>华为CSI运行时所在Kubernetes命名空间，支持用户自定义。名称必须由小写字母、数字和“-”组成，例如：my-name、123-abc。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p633705711458"><a name="zh-cn_topic_0000001324610777_p633705711458"></a><a name="zh-cn_topic_0000001324610777_p633705711458"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p1633715784512"><a name="zh-cn_topic_0000001324610777_p1633715784512"></a><a name="zh-cn_topic_0000001324610777_p1633715784512"></a>huawei-csi</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p144858121013"><a name="p144858121013"></a><a name="p144858121013"></a>-</p>
</td>
</tr>
<tr id="row1723613654416"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p1423618610447"><a name="p1423618610447"></a><a name="p1423618610447"></a>kubeletConfigDir</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p1023613610444"><a name="p1023613610444"></a><a name="p1023613610444"></a>kubelet工作目录。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p2236176194414"><a name="p2236176194414"></a><a name="p2236176194414"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p112361667445"><a name="p112361667445"></a><a name="p112361667445"></a>/var/lib/kubelet</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><a name="ul18493162309"></a><a name="ul18493162309"></a><ul id="ul18493162309"><li>直接使用默认值。</li><li>对于Tanzu平台，需要修改该字段为/var/vcap/data/kubelet。</li><li>对于CCE Agile平台，需要修改该字段为/mnt/paas/kubernetes/kubelet。</li></ul>
</td>
</tr>
<tr id="row0588342152819"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p12348334144611"><a name="zh-cn_topic_0000001324610777_p12348334144611"></a><a name="zh-cn_topic_0000001324610777_p12348334144611"></a>sidecarImagePullPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p113481634194616"><a name="zh-cn_topic_0000001324610777_p113481634194616"></a><a name="zh-cn_topic_0000001324610777_p113481634194616"></a>sidecar镜像的拉取策略。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p1134803416462"><a name="zh-cn_topic_0000001324610777_p1134803416462"></a><a name="zh-cn_topic_0000001324610777_p1134803416462"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p33489342465"><a name="zh-cn_topic_0000001324610777_p33489342465"></a><a name="zh-cn_topic_0000001324610777_p33489342465"></a>IfNotPresent</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p18485411109"><a name="p18485411109"></a><a name="p18485411109"></a>-</p>
</td>
</tr>
<tr id="row3588104242816"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p7348034124617"><a name="zh-cn_topic_0000001324610777_p7348034124617"></a><a name="zh-cn_topic_0000001324610777_p7348034124617"></a>huaweiImagePullPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p734818345469"><a name="zh-cn_topic_0000001324610777_p734818345469"></a><a name="zh-cn_topic_0000001324610777_p734818345469"></a>huawei-csi镜像的拉取策略。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p934816348468"><a name="zh-cn_topic_0000001324610777_p934816348468"></a><a name="zh-cn_topic_0000001324610777_p934816348468"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="zh-cn_topic_0000001324610777_p834883414468"><a name="zh-cn_topic_0000001324610777_p834883414468"></a><a name="zh-cn_topic_0000001324610777_p834883414468"></a>IfNotPresent</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p10485101141015"><a name="p10485101141015"></a><a name="p10485101141015"></a>-</p>
</td>
</tr>
<tr id="row136111531580"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p1761115325820"><a name="p1761115325820"></a><a name="p1761115325820"></a>imagePullSecrets</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p1361103155815"><a name="p1361103155815"></a><a name="p1361103155815"></a>用于Kubernetes集群通过镜像仓库的身份验证，进而提取私有镜像。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p1861113325818"><a name="p1861113325818"></a><a name="p1861113325818"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p1861112355810"><a name="p1861112355810"></a><a name="p1861112355810"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p1161112317588"><a name="p1161112317588"></a><a name="p1161112317588"></a>详细说明请参考：<a href="https://kubernetes.io/zh-cn/docs/tasks/configure-pod-container/pull-image-private-registry/" target="_blank" rel="noopener noreferrer">从私有仓库拉取镜像</a></p>
</td>
</tr>
<tr id="row1670374213211"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p177048426324"><a name="p177048426324"></a><a name="p177048426324"></a>CSIDriverObject.isCreate</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p67047427323"><a name="p67047427323"></a><a name="p67047427323"></a>是否创建CSIDriver对象</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p370474273215"><a name="p370474273215"></a><a name="p370474273215"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p117042042153214"><a name="p117042042153214"></a><a name="p117042042153214"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p670464213219"><a name="p670464213219"></a><a name="p670464213219"></a><a href="https://kubernetes-csi.github.io/docs/csi-driver-object.html" target="_blank" rel="noopener noreferrer">CSIDriver</a>特性在Kubernetes v1.18成为GA版本，因此要求Kubernetes版本高于v1.18，当Kubernetes版本低于 v1.18时，请设置该参数为false。</p>
</td>
</tr>
<tr id="row5325193974610"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p11570469462"><a name="p11570469462"></a><a name="p11570469462"></a>CSIDriverObject.attachRequired</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p191571546164615"><a name="p191571546164615"></a><a name="p191571546164615"></a>CSI插件是否跳过attach操作。支持配置如下参数：</p>
<a name="ul4731114312531"></a><a name="ul4731114312531"></a><ul id="ul4731114312531"><li>true：需要attach操作。</li><li>false：跳过attach操作。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p1157114617462"><a name="p1157114617462"></a><a name="p1157114617462"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p515714616460"><a name="p515714616460"></a><a name="p515714616460"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p106733391199"><a name="p106733391199"></a><a name="p106733391199"></a>参数<a href="https://kubernetes-csi.github.io/docs/csi-driver-object.html" target="_blank" rel="noopener noreferrer">attachRequired</a>在Kubernetes v1.18支持配置。</p>
<p id="p87615434538"><a name="p87615434538"></a><a name="p87615434538"></a>如果CSIDriverObject.isCreate为true并且attachRequired参数设置为false时，huawei-csi插件将不会部署csi-attacher这个sidecar。</p>
<a name="ul5512181115174"></a><a name="ul5512181115174"></a><ul id="ul5512181115174"><li>使用NAS存储时支持配置为false。</li><li>使用SAN存储时，请配置为true。</li></ul>
</td>
</tr>
<tr id="row890414451319"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p498831161311"><a name="p498831161311"></a><a name="p498831161311"></a>CSIDriverObject.fsGroupPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p1298810111139"><a name="p1298810111139"></a><a name="p1298810111139"></a>基础卷是否支持在装载之前更改卷的所有权和权限。支持配置如下参数：</p>
<a name="ul1988191110133"></a><a name="ul1988191110133"></a><ul id="ul1988191110133"><li>"ReadWriteOnceWithFSType"：仅当定义了fsType并且卷的accessModes包含ReadWriteOnce时，才支持卷所有权和权限更改。</li><li>"File"：Kubernetes可以使用fsGroup更改卷的权限和所有权，以匹配Pod安全策略中用户请求的fsGroup，而不管fsGroup或accessModes如何。</li><li>"None"：将在不进行修改的情况下装载卷。</li><li>"null"：将不设置fsGroupPolicy参数</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p159881411191317"><a name="p159881411191317"></a><a name="p159881411191317"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p1698811110137"><a name="p1698811110137"></a><a name="p1698811110137"></a>null</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p14641734132114"><a name="p14641734132114"></a><a name="p14641734132114"></a>参数<a href="https://kubernetes-csi.github.io/docs/csi-driver-object.html" target="_blank" rel="noopener noreferrer">fsGroupPolicy</a>在Kubernetes v1.20支持配置，并且当CSIDriverObject.isCreate为true时该参数生效。</p>
<p id="p20988811151315"><a name="p20988811151315"></a><a name="p20988811151315"></a>该特性在Kubernetes v1.20中为Beta版本，在Kubernetes v1.23成为GA版本，因此要求Kubernetes版本高于v1.20。</p>
</td>
</tr>
<tr id="row1921061519422"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p721081512429"><a name="p721081512429"></a><a name="p721081512429"></a>leaderElection.leaseDuration</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p16210151544212"><a name="p16210151544212"></a><a name="p16210151544212"></a>领导者持续时间。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p14210121524211"><a name="p14210121524211"></a><a name="p14210121524211"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p1221071514218"><a name="p1221071514218"></a><a name="p1221071514218"></a>8s</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p7210121554213"><a name="p7210121554213"></a><a name="p7210121554213"></a>仅多controller场景生效。</p>
</td>
</tr>
<tr id="row141688824315"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p3168283431"><a name="p3168283431"></a><a name="p3168283431"></a>leaderElection.renewDeadline</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p141685884315"><a name="p141685884315"></a><a name="p141685884315"></a>领导者重新选举时间。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p11680894311"><a name="p11680894311"></a><a name="p11680894311"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p3168888435"><a name="p3168888435"></a><a name="p3168888435"></a>6s</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p616888134320"><a name="p616888134320"></a><a name="p616888134320"></a>仅多controller场景生效。</p>
</td>
</tr>
<tr id="row13567171024310"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p6568191094318"><a name="p6568191094318"></a><a name="p6568191094318"></a>leaderElection.retryPeriod</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p3568141019435"><a name="p3568141019435"></a><a name="p3568141019435"></a>领导者选举重试时间。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p10568910134310"><a name="p10568910134310"></a><a name="p10568910134310"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p155681010134316"><a name="p155681010134316"></a><a name="p155681010134316"></a>2s</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p165681710114315"><a name="p165681710114315"></a><a name="p165681710114315"></a>仅多controller场景生效。</p>
</td>
</tr>
<tr id="row2630194110428"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p9630104184219"><a name="p9630104184219"></a><a name="p9630104184219"></a>service.ipFamilyPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p2630941144214"><a name="p2630941144214"></a><a name="p2630941144214"></a>service的IP协议栈选择策略。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p763016410424"><a name="p763016410424"></a><a name="p763016410424"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p11630184134220"><a name="p11630184134220"></a><a name="p11630184134220"></a>SingleStack</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p3913114715513"><a name="p3913114715513"></a><a name="p3913114715513"></a>可配置参数：</p>
<a name="ul11642201414568"></a><a name="ul11642201414568"></a><ul id="ul11642201414568"><li><a href="https://kubernetes.io/docs/concepts/services-networking/dual-stack/#services" target="_blank" rel="noopener noreferrer">SingleStack</a>：service只使用一种 IP 地址族（IPv4 或 IPv6）。</li><li><a href="https://kubernetes.io/docs/concepts/services-networking/dual-stack/#services" target="_blank" rel="noopener noreferrer">PreferDualStack</a>：service优先尝试使用双栈；如果集群不支持双栈，则回退单栈。</li><li><a href="https://kubernetes.io/docs/concepts/services-networking/dual-stack/#services" target="_blank" rel="noopener noreferrer">RequireDualStack</a>：service必须使用双栈；如果集群不支持双栈，则service创建会失败。</li></ul>
</td>
</tr>
<tr id="row1104104874417"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p1710414824415"><a name="p1710414824415"></a><a name="p1710414824415"></a>service.ipFamilies</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p9104164834415"><a name="p9104164834415"></a><a name="p9104164834415"></a>service支持的IP协议栈列表。</p>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p12104114864410"><a name="p12104114864410"></a><a name="p12104114864410"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p210411484448"><a name="p210411484448"></a><a name="p210411484448"></a>IPv4</p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p26721743512"><a name="p26721743512"></a><a name="p26721743512"></a>可配置参数：</p>
<a name="ul5941610216"></a><a name="ul5941610216"></a><ul id="ul5941610216"><li>IPv4</li><li>IPv6</li></ul>
</td>
</tr>
<tr id="row2411204292218"><td class="cellrowborder" valign="top" width="23.119999999999997%" headers="mcps1.2.6.1.1 "><p id="p1941154213223"><a name="p1941154213223"></a><a name="p1941154213223"></a>resources</p>
</td>
<td class="cellrowborder" valign="top" width="29.709999999999997%" headers="mcps1.2.6.1.2 "><p id="p113716142716"><a name="p113716142716"></a><a name="p113716142716"></a>可以对huawei-csi-controller和huawei-csi-node相关容器资源进行分配：</p>
<p id="p1513761411718"><a name="p1513761411718"></a><a name="p1513761411718"></a>resources.&lt;component&gt;.&lt;container-name&gt;</p>
<p id="p713711141871"><a name="p713711141871"></a><a name="p713711141871"></a></p>
<p id="p1713731415712"><a name="p1713731415712"></a><a name="p1713731415712"></a>&lt;component&gt;支持的参数：</p>
<a name="ul18915105142419"></a><a name="ul18915105142419"></a><ul id="ul18915105142419"><li>node：配置huawei-csi-node组件中的sidecar时配置；</li><li>controller: 配置huawei-csi-controller组件中的sidecar时配置；</li></ul>
<p id="p913716149716"><a name="p913716149716"></a><a name="p913716149716"></a></p>
<p id="p1813712141714"><a name="p1813712141714"></a><a name="p1813712141714"></a>controller.&lt;container-name&gt;支持的参数:</p>
<a name="ul328959182417"></a><a name="ul328959182417"></a><ul id="ul328959182417"><li>livenessProbe</li><li>csiProvisioner</li><li>csiAttacher</li><li>csiResizer</li><li>csiSnapshotter</li><li>snapshotController</li><li>storageBackendController</li><li>storageBackendSidecar</li><li>huaweiCsiExtender</li><li>huaweiCsiDriver</li></ul>
<p id="p1513717142713"><a name="p1513717142713"></a><a name="p1513717142713"></a></p>
<p id="p8810438121413"><a name="p8810438121413"></a><a name="p8810438121413"></a>node.&lt;container-name&gt;支持的参数:</p>
<a name="ul1778113710255"></a><a name="ul1778113710255"></a><ul id="ul1778113710255"><li>huaweiCsiDriver</li><li>livenessProbe</li><li>csiNodeDriverRegistrar</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.329999999999999%" headers="mcps1.2.6.1.3 "><p id="p2412174213224"><a name="p2412174213224"></a><a name="p2412174213224"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="17.44%" headers="mcps1.2.6.1.4 "><p id="p1593232713328"><a name="p1593232713328"></a><a name="p1593232713328"></a>各容器资源分配默认值，请参考：<a href="/css-docs/docs/appendix/huawei-csi-resource-management">华为CSI资源管理</a></p>
</td>
<td class="cellrowborder" valign="top" width="23.400000000000002%" headers="mcps1.2.6.1.5 "><p id="p13812293161"><a name="p13812293161"></a><a name="p13812293161"></a>以huawei-csi-controller的livenessProbe为例：</p>
<pre class="screen" id="screen1541341184010"><a name="screen1541341184010"></a><a name="screen1541341184010"></a>resources:
  controller:
    limits:
      cpu: 100m
      memory: 128Mi
    requests:
      cpu: 10m
      memory: 128Mi</pre>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>请确保此kubernetes.namespace填入的命名空间在Kubernetes上已经存在，如果不存在请使用如下命令创建对应的命名空间。本例中，华为CSI运行的命名空间为“huawei-csi”。
>```
>kubectl create namespace huawei-csi
>```

