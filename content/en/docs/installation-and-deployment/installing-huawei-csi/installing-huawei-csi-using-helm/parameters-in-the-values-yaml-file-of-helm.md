---
title: "Parameters in the values.yaml File of Helm"
linkTitle: "Parameters in the values.yaml File of Helm"
description: 
weight: 3
---

When using Helm to install CSI, you need to prepare the  **values.yaml**  file of the Helm project based on the features required during deployment. Huawei CSI provides the  **values.yaml**  template file in the  **helm/esdk**  directory of the software package.

This section describes the configuration items in the  **values.yaml**  file and backend configuration examples in typical scenarios.

## images Parameters{#section128441143205716}

The images parameters in the  **values.yaml**  file are used to configure the component image information on which Huawei CSI depends during running. Set the following parameters:

**Table  1**  images parameters

<a name="table8452547161918"></a>
<table><thead align="left"><tr id="row645218479197"><th class="cellrowborder" valign="top" width="22%" id="mcps1.2.5.1.1"><p id="p5269141514410"><a name="p5269141514410"></a><a name="p5269141514410"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="32%" id="mcps1.2.5.1.2"><p id="p026931524418"><a name="p026931524418"></a><a name="p026931524418"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="17%" id="mcps1.2.5.1.3"><p id="p826915156447"><a name="p826915156447"></a><a name="p826915156447"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="28.999999999999996%" id="mcps1.2.5.1.4"><p id="p1426921517443"><a name="p1426921517443"></a><a name="p1426921517443"></a>Default Value</p>
</th>
</tr>
</thead>
<tbody><tr id="row1156694303912"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000001324610777_p15337145719458"><a name="en-us_topic_0000001324610777_p15337145719458"></a><a name="en-us_topic_0000001324610777_p15337145719458"></a>images.huaweiCSIService</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000001324610777_p173371357144517"><a name="en-us_topic_0000001324610777_p173371357144517"></a><a name="en-us_topic_0000001324610777_p173371357144517"></a>huawei-csi image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000001324610777_p1633715710454"><a name="en-us_topic_0000001324610777_p1633715710454"></a><a name="en-us_topic_0000001324610777_p1633715710454"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000001324610777_p16337457154513"><a name="en-us_topic_0000001324610777_p16337457154513"></a><a name="en-us_topic_0000001324610777_p16337457154513"></a>huawei-csi:<span id="ph09001410174913"><a name="ph09001410174913"></a><a name="ph09001410174913"></a>4.5.0</span></p>
</td>
</tr>
<tr id="row12803747173911"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="p1616415034013"><a name="p1616415034013"></a><a name="p1616415034013"></a>images.storageBackendSidecar</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="p1080311470395"><a name="p1080311470395"></a><a name="p1080311470395"></a>Huawei back-end management sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="p1380304783914"><a name="p1380304783914"></a><a name="p1380304783914"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p1380384793918"><a name="p1380384793918"></a><a name="p1380384793918"></a>storage-backend-sidecar:<span id="ph111931741165212"><a name="ph111931741165212"></a><a name="ph111931741165212"></a>4.5.0</span></p>
</td>
</tr>
<tr id="row1089864973918"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="p46581916408"><a name="p46581916408"></a><a name="p46581916408"></a>images.storageBackendController</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="p6899124910393"><a name="p6899124910393"></a><a name="p6899124910393"></a>Huawei back-end management controller image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="p2089912497394"><a name="p2089912497394"></a><a name="p2089912497394"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p1489984963919"><a name="p1489984963919"></a><a name="p1489984963919"></a>storage-backend-controller:<span id="ph21391643115214"><a name="ph21391643115214"></a><a name="ph21391643115214"></a>4.5.0</span></p>
</td>
</tr>
<tr id="row12997135033511"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="p199785073518"><a name="p199785073518"></a><a name="p199785073518"></a>images.huaweiCSIExtender</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="p1299785010355"><a name="p1299785010355"></a><a name="p1299785010355"></a>huawei-csi-extender image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="p17997350183511"><a name="p17997350183511"></a><a name="p17997350183511"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="p15997155019358"><a name="p15997155019358"></a><a name="p15997155019358"></a>huawei-csi-extender:<span id="ph8385174515525"><a name="ph8385174515525"></a><a name="ph8385174515525"></a>4.5.0</span></p>
</td>
</tr>
<tr id="row185030354414"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000001324610777_p4337185713453"><a name="en-us_topic_0000001324610777_p4337185713453"></a><a name="en-us_topic_0000001324610777_p4337185713453"></a>images.sidecar.livenessProbe</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000001324610777_p9337195764510"><a name="en-us_topic_0000001324610777_p9337195764510"></a><a name="en-us_topic_0000001324610777_p9337195764510"></a><a href="https://kubernetes-csi.github.io/docs/livenessprobe.html" target="_blank" rel="noopener noreferrer">livenessprobe</a> sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000001324610777_p1633725724512"><a name="en-us_topic_0000001324610777_p1633725724512"></a><a name="en-us_topic_0000001324610777_p1633725724512"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000001324610777_p1733785714453"><a name="en-us_topic_0000001324610777_p1733785714453"></a><a name="en-us_topic_0000001324610777_p1733785714453"></a>k8s.gcr.io/sig-storage/livenessprobe:v2.5.0</p>
</td>
</tr>
<tr id="row345374716195"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000001324610777_p333755715453"><a name="en-us_topic_0000001324610777_p333755715453"></a><a name="en-us_topic_0000001324610777_p333755715453"></a>images.sidecar.provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000001324610777_p183372575454"><a name="en-us_topic_0000001324610777_p183372575454"></a><a name="en-us_topic_0000001324610777_p183372575454"></a><a href="https://kubernetes-csi.github.io/docs/external-provisioner.html" target="_blank" rel="noopener noreferrer">csi-provisioner</a> sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000001324610777_p1033711577456"><a name="en-us_topic_0000001324610777_p1033711577456"></a><a name="en-us_topic_0000001324610777_p1033711577456"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000001324610777_p15337125716458"><a name="en-us_topic_0000001324610777_p15337125716458"></a><a name="en-us_topic_0000001324610777_p15337125716458"></a>k8s.gcr.io/sig-storage/csi-provisioner:v3.0.0</p>
</td>
</tr>
<tr id="row145324715192"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000001324610777_p19337155744517"><a name="en-us_topic_0000001324610777_p19337155744517"></a><a name="en-us_topic_0000001324610777_p19337155744517"></a>images.sidecar.attacher</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000001324610777_p18337145744510"><a name="en-us_topic_0000001324610777_p18337145744510"></a><a name="en-us_topic_0000001324610777_p18337145744510"></a><a href="https://kubernetes-csi.github.io/docs/external-attacher.html" target="_blank" rel="noopener noreferrer">csi-attacher</a> sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000001324610777_p18337155714518"><a name="en-us_topic_0000001324610777_p18337155714518"></a><a name="en-us_topic_0000001324610777_p18337155714518"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000001324610777_p7337457134516"><a name="en-us_topic_0000001324610777_p7337457134516"></a><a name="en-us_topic_0000001324610777_p7337457134516"></a>k8s.gcr.io/sig-storage/csi-attacher:v3.4.0</p>
</td>
</tr>
<tr id="row94532047111915"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000001324610777_p13337175711459"><a name="en-us_topic_0000001324610777_p13337175711459"></a><a name="en-us_topic_0000001324610777_p13337175711459"></a>images.sidecar.resizer</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000001324610777_p53377576452"><a name="en-us_topic_0000001324610777_p53377576452"></a><a name="en-us_topic_0000001324610777_p53377576452"></a><a href="https://kubernetes-csi.github.io/docs/external-resizer.html" target="_blank" rel="noopener noreferrer">csi-resizer</a> sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000001324610777_p93375572452"><a name="en-us_topic_0000001324610777_p93375572452"></a><a name="en-us_topic_0000001324610777_p93375572452"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000001324610777_p153371257184518"><a name="en-us_topic_0000001324610777_p153371257184518"></a><a name="en-us_topic_0000001324610777_p153371257184518"></a>k8s.gcr.io/sig-storage/csi-resizer:v1.4.0</p>
</td>
</tr>
<tr id="row9453124771918"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000001324610777_p833785764516"><a name="en-us_topic_0000001324610777_p833785764516"></a><a name="en-us_topic_0000001324610777_p833785764516"></a>images.sidecar.snapshotter</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000001324610777_p73371257134514"><a name="en-us_topic_0000001324610777_p73371257134514"></a><a name="en-us_topic_0000001324610777_p73371257134514"></a><a href="https://kubernetes-csi.github.io/docs/external-snapshotter.html" target="_blank" rel="noopener noreferrer">csi-snapshotter</a> sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000001324610777_p1833765712454"><a name="en-us_topic_0000001324610777_p1833765712454"></a><a name="en-us_topic_0000001324610777_p1833765712454"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000001324610777_p1033755713457"><a name="en-us_topic_0000001324610777_p1033755713457"></a><a name="en-us_topic_0000001324610777_p1033755713457"></a>k8s.gcr.io/sig-storage/csi-snapshotter:v4.2.1</p>
</td>
</tr>
<tr id="row196140122014"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000001324610777_p10337557174514"><a name="en-us_topic_0000001324610777_p10337557174514"></a><a name="en-us_topic_0000001324610777_p10337557174514"></a>images.sidecar.snapshotController</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000001324610777_p163372057164518"><a name="en-us_topic_0000001324610777_p163372057164518"></a><a name="en-us_topic_0000001324610777_p163372057164518"></a><a href="https://kubernetes-csi.github.io/docs/snapshot-controller.html" target="_blank" rel="noopener noreferrer">snapshot-controller</a> sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000001324610777_p10337457134511"><a name="en-us_topic_0000001324610777_p10337457134511"></a><a name="en-us_topic_0000001324610777_p10337457134511"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000001324610777_p0337195724520"><a name="en-us_topic_0000001324610777_p0337195724520"></a><a name="en-us_topic_0000001324610777_p0337195724520"></a>k8s.gcr.io/sig-storage/snapshot-controller:v4.2.1</p>
</td>
</tr>
<tr id="row84580467201"><td class="cellrowborder" valign="top" width="22%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000001324610777_p10337165714454"><a name="en-us_topic_0000001324610777_p10337165714454"></a><a name="en-us_topic_0000001324610777_p10337165714454"></a>images.sidecar.registrar</p>
</td>
<td class="cellrowborder" valign="top" width="32%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000001324610777_p153371957164512"><a name="en-us_topic_0000001324610777_p153371957164512"></a><a name="en-us_topic_0000001324610777_p153371957164512"></a><a href="https://kubernetes-csi.github.io/docs/node-driver-registrar.html" target="_blank" rel="noopener noreferrer">csi-node-driver-registrar</a> sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000001324610777_p83371057164510"><a name="en-us_topic_0000001324610777_p83371057164510"></a><a name="en-us_topic_0000001324610777_p83371057164510"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="28.999999999999996%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000001324610777_p1833711578459"><a name="en-us_topic_0000001324610777_p1833711578459"></a><a name="en-us_topic_0000001324610777_p1833711578459"></a>k8s.gcr.io/sig-storage/csi-node-driver-registrar:v2.3.0</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/en/icon-notice.gif) 
>-   For details about the values of  **huaweiCSIService**,  **storageBackendSidecar**,  **storageBackendController**, and  **huaweiCSIExtender**, see  [Uploading a Huawei CSI Image](/docs/installation-and-deployment/installation-preparations/uploading-a-huawei-csi-image). Use the name and version of the finally generated image.
>-   For details about other sidecar image parameters, see  [Checking the Images on Which CSI Depends](/docs/installation-and-deployment/installation-preparations/checking-the-images-on-which-csi-depends). Use the name and version of the finally uploaded image.

## controller Parameters{#section94006111587}

The controller parameters are used to configure the huawei-csi-controller component.

**Table  2**  controller parameters

<a name="table813124411459"></a>
<table><thead align="left"><tr id="row16131444124517"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.1"><p id="p413174420459"><a name="p413174420459"></a><a name="p413174420459"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="25%" id="mcps1.2.6.1.2"><p id="p1313111444458"><a name="p1313111444458"></a><a name="p1313111444458"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.3"><p id="p8131114464512"><a name="p8131114464512"></a><a name="p8131114464512"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.4"><p id="p8963122912427"><a name="p8963122912427"></a><a name="p8963122912427"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="27%" id="mcps1.2.6.1.5"><p id="p1413154464517"><a name="p1413154464517"></a><a name="p1413154464517"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row19652123211576"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1765213214571"><a name="p1765213214571"></a><a name="p1765213214571"></a>controller.controllerCount</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p16652123285711"><a name="p16652123285711"></a><a name="p16652123285711"></a>Number of huawei-csi-controller component copies.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p665233210576"><a name="p665233210576"></a><a name="p665233210576"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p9963429194216"><a name="p9963429194216"></a><a name="p9963429194216"></a>1</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p0677122985016"><a name="p0677122985016"></a><a name="p0677122985016"></a>If the Kubernetes version is earlier than v1.17, the huawei-csi-controller component can be deployed only in single-copy mode because the csi-provisioner sidecar image provided by the Kubernetes community does not support the <strong id="b7401182418110"><a name="b7401182418110"></a><a name="b7401182418110"></a>--leader-election</strong> parameter.</p>
<p id="p8606174713335"><a name="p8606174713335"></a><a name="p8606174713335"></a>Therefore, if the Kubernetes version is earlier than v1.17, this parameter can only be set to <strong id="b1857643917116"><a name="b1857643917116"></a><a name="b1857643917116"></a>1</strong>.</p>
</td>
</tr>
<tr id="row395265716343"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p936624344510"><a name="p936624344510"></a><a name="p936624344510"></a>controller.volumeNamePrefix</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p19782351165214"><a name="p19782351165214"></a><a name="p19782351165214"></a>PV name prefix. The default value is <strong id="b1845342716130"><a name="b1845342716130"></a><a name="b1845342716130"></a>pvc</strong>, that is, the name of a created PV is <strong id="b245422701310"><a name="b245422701310"></a><a name="b245422701310"></a>pvc-</strong><em id="i134541927121312"><a name="i134541927121312"></a><a name="i134541927121312"></a>&lt;uuid&gt;</em>. The prefix must comply with the naming rules of a <a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#dns-subdomain-names" target="_blank" rel="noopener noreferrer">DNS subdomain name</a>, and the total length of the PV name cannot exceed 253 characters.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p236613438456"><a name="p236613438456"></a><a name="p236613438456"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p9963729104213"><a name="p9963729104213"></a><a name="p9963729104213"></a>pvc</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p17366114313450"><a name="p17366114313450"></a><a name="p17366114313450"></a>The corresponding provisioner parameter name is <strong id="b561312220596"><a name="b561312220596"></a><a name="b561312220596"></a>--volume-name-prefix</strong>.</p>
<p id="p9406581769"><a name="p9406581769"></a><a name="p9406581769"></a>It is recommended that the prefix contain no more than 20 characters.</p>
<p id="p828611423316"><a name="p828611423316"></a><a name="p828611423316"></a>For details, see <a href="https://github.com/kubernetes-csi/external-provisioner/tree/release-3.0" target="_blank" rel="noopener noreferrer">Configuring the PV Name Prefix</a>.</p>
<a name="ul517195262412"></a><a name="ul517195262412"></a><ul id="ul517195262412"><li>If the connected backend is OceanStor V5 SAN storage, it is recommended that the prefix contain a maximum of 5 characters.</li><li>If the connected backend is OceanStor V5 NAS storage, the prefix can contain only lowercase letters, hyphens (-), and digits.</li><li>If the connected backend is OceanStor Dorado or OceanStor storage, the prefix can contain only lowercase letters, hyphens (-), and digits.</li><li>If the connected backend is OceanStor Pacific series storage, the prefix can contain a maximum of 58 characters, including only letters, digits, underscores (_), hyphens (-), and periods (.).</li><li>If the connected backend is FusionStorage Block, the prefix can contain a maximum of 58 characters, including only letters, digits, underscores (_), and hyphens (-).</li></ul>
</td>
</tr>
<tr id="row17543658153417"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p11543175819348"><a name="p11543175819348"></a><a name="p11543175819348"></a>controller.webhookPort</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p6544165816346"><a name="p6544165816346"></a><a name="p6544165816346"></a>Port used by the webhook service.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p5544158143412"><a name="p5544158143412"></a><a name="p5544158143412"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p85441258193419"><a name="p85441258193419"></a><a name="p85441258193419"></a>4433</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p5544458203416"><a name="p5544458203416"></a><a name="p5544458203416"></a>If a port conflict occurs, change the port number to an idle one.</p>
</td>
</tr>
<tr id="row12842142319395"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1184332318398"><a name="p1184332318398"></a><a name="p1184332318398"></a>controller.snapshot.enabled</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p12348183444610"><a name="en-us_topic_0000001324610777_p12348183444610"></a><a name="en-us_topic_0000001324610777_p12348183444610"></a>Whether to enable the snapshot feature.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1434811345468"><a name="en-us_topic_0000001324610777_p1434811345468"></a><a name="en-us_topic_0000001324610777_p1434811345468"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p139638293427"><a name="p139638293427"></a><a name="p139638293427"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p6556044384"><a name="p6556044384"></a><a name="p6556044384"></a>If you want to use snapshot-related functions, enable this feature.</p>
<p id="en-us_topic_0000001324610777_p13348113418464"><a name="en-us_topic_0000001324610777_p13348113418464"></a><a name="en-us_topic_0000001324610777_p13348113418464"></a>The Kubernetes version must be later than v1.17.</p>
</td>
</tr>
<tr id="row0284172210403"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p16956162712407"><a name="p16956162712407"></a><a name="p16956162712407"></a>controller.resizer.enabled</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p126618381404"><a name="p126618381404"></a><a name="p126618381404"></a>Whether to enable the capacity expansion feature.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p17284192214010"><a name="p17284192214010"></a><a name="p17284192214010"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p16963142912429"><a name="p16963142912429"></a><a name="p16963142912429"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p728462210401"><a name="p728462210401"></a><a name="p728462210401"></a>The Kubernetes version must be later than v1.16.</p>
</td>
</tr>
<tr id="row14131154414450"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p913144454511"><a name="p913144454511"></a><a name="p913144454511"></a>controller.nodeSelector</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p613154419453"><a name="p613154419453"></a><a name="p613154419453"></a>Node selector of huawei-csi-controller. After this parameter is set, huawei-csi-controller will be scheduled only to a node with the label.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p17131644194514"><a name="p17131644194514"></a><a name="p17131644194514"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p396342918424"><a name="p396342918424"></a><a name="p396342918424"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p1184116225568"><a name="p1184116225568"></a><a name="p1184116225568"></a>For details about the node selector, see <a href="https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes/#create-a-pod-that-gets-scheduled-to-your-chosen-node" target="_blank" rel="noopener noreferrer">Assign Pods to Nodes</a>.</p>
</td>
</tr>
<tr id="row1413194413458"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p21311144164510"><a name="p21311144164510"></a><a name="p21311144164510"></a>controller.tolerations</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p313164414456"><a name="p313164414456"></a><a name="p313164414456"></a>Taint toleration of huawei-csi-controller. After this parameter is set, huawei-csi-controller can tolerate taints on a node.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p1513184416453"><a name="p1513184416453"></a><a name="p1513184416453"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p4963142911421"><a name="p4963142911421"></a><a name="p4963142911421"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p313104444510"><a name="p313104444510"></a><a name="p313104444510"></a>For details about taints and tolerations, see <a href="https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/" target="_blank" rel="noopener noreferrer">Taints and Tolerations</a>.</p>
</td>
</tr>
<tr id="row3514131652617"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1751521602612"><a name="p1751521602612"></a><a name="p1751521602612"></a>controller.livenessProbePort</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p10515161682619"><a name="p10515161682619"></a><a name="p10515161682619"></a>Liveness probe port of huawei-csi-controller, used for health check.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p75156162261"><a name="p75156162261"></a><a name="p75156162261"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p13515121652612"><a name="p13515121652612"></a><a name="p13515121652612"></a>9808</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p651512160261"><a name="p651512160261"></a><a name="p651512160261"></a>If a port conflict occurs, change the port number to an idle one.</p>
</td>
</tr>
<tr id="row48331747163918"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p15785239105916"><a name="p15785239105916"></a><a name="p15785239105916"></a>controller.csiExtender.volumeModify.enabled</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p1978533911594"><a name="p1978533911594"></a><a name="p1978533911594"></a>Whether to enable the PVC change feature.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p97851739145912"><a name="p97851739145912"></a><a name="p97851739145912"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p97858393599"><a name="p97858393599"></a><a name="p97858393599"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p5785133913594"><a name="p5785133913594"></a><a name="p5785133913594"></a>If you want to use PVC change-related functions, enable this feature.</p>
</td>
</tr>
<tr id="row188026506397"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p8802950113914"><a name="p8802950113914"></a><a name="p8802950113914"></a>controller.csiExtender.volumeModify.retryBaseDelay</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p6460153193217"><a name="p6460153193217"></a><a name="p6460153193217"></a>Minimum retry interval when a PVC change fails to be created.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p1480315509397"><a name="p1480315509397"></a><a name="p1480315509397"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p19803750203914"><a name="p19803750203914"></a><a name="p19803750203914"></a>5s</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p9803450103911"><a name="p9803450103911"></a><a name="p9803450103911"></a>The default value is recommended.</p>
</td>
</tr>
<tr id="row126131354143917"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p166131654153915"><a name="p166131654153915"></a><a name="p166131654153915"></a>controller.csiExtender.volumeModify.retryMaxDelay</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p2613254143910"><a name="p2613254143910"></a><a name="p2613254143910"></a>Maximum retry interval when a PVC change fails to be created.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p76131254133915"><a name="p76131254133915"></a><a name="p76131254133915"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p261312546395"><a name="p261312546395"></a><a name="p261312546395"></a>5m</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p1861319542396"><a name="p1861319542396"></a><a name="p1861319542396"></a>The default value is recommended.</p>
</td>
</tr>
<tr id="row12879850114019"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p168791450184014"><a name="p168791450184014"></a><a name="p168791450184014"></a>controller.csiExtender.volumeModify.reconcileDelay</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.6.1.2 "><p id="p6879185044013"><a name="p6879185044013"></a><a name="p6879185044013"></a>Interval for reconciling VolumeModifyClaim objects.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p2879350154017"><a name="p2879350154017"></a><a name="p2879350154017"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p4879185015409"><a name="p4879185015409"></a><a name="p4879185015409"></a>1s</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.5 "><p id="p148791050164015"><a name="p148791050164015"></a><a name="p148791050164015"></a>The default value is recommended.</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/en/icon-note.gif)
>If  **controller.snapshot.enabled**  is set to  **true**, you need to install the volume snapshot CRD resource in the  **helm/crd/snapshot-crds**  directory.

## node Parameters{#section374014171581}

The node parameters are used to configure the huawei-csi-node component.

**Table  3**  node parameters

<a name="table1496310165912"></a>
<table><thead align="left"><tr id="row29633012599"><th class="cellrowborder" valign="top" width="20.2020202020202%" id="mcps1.2.6.1.1"><p id="p79636005914"><a name="p79636005914"></a><a name="p79636005914"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.26262626262626%" id="mcps1.2.6.1.2"><p id="p2096319015915"><a name="p2096319015915"></a><a name="p2096319015915"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="13.13131313131313%" id="mcps1.2.6.1.3"><p id="p89631908591"><a name="p89631908591"></a><a name="p89631908591"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="14.14141414141414%" id="mcps1.2.6.1.4"><p id="p988145513479"><a name="p988145513479"></a><a name="p988145513479"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="26.26262626262626%" id="mcps1.2.6.1.5"><p id="p4963110135913"><a name="p4963110135913"></a><a name="p4963110135913"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row20933131914418"><td class="cellrowborder" valign="top" width="20.2020202020202%" headers="mcps1.2.6.1.1 "><p id="p109331619134413"><a name="p109331619134413"></a><a name="p109331619134413"></a>node.maxVolumesPerNode</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.2 "><p id="p18933181915444"><a name="p18933181915444"></a><a name="p18933181915444"></a>Maximum number of volumes provisioned by Huawei CSI that can be used by a node. If this parameter is not specified or is set to <strong id="b5302155653010"><a name="b5302155653010"></a><a name="b5302155653010"></a>0</strong>, the number is unlimited.</p>
<p id="p11105463112"><a name="p11105463112"></a><a name="p11105463112"></a>If <strong id="b197481283510"><a name="b197481283510"></a><a name="b197481283510"></a>nodeName</strong> is specified during Pod creation, this configuration will be ignored.</p>
</td>
<td class="cellrowborder" valign="top" width="13.13131313131313%" headers="mcps1.2.6.1.3 "><p id="p209331197442"><a name="p209331197442"></a><a name="p209331197442"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.14141414141414%" headers="mcps1.2.6.1.4 "><p id="p19881955164717"><a name="p19881955164717"></a><a name="p19881955164717"></a>100</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.5 "><p id="p11933219144415"><a name="p11933219144415"></a><a name="p11933219144415"></a>For details, see <a href="https://kubernetes-csi.github.io/docs/volume-limits.html" target="_blank" rel="noopener noreferrer">Volume Limits</a>.</p>
</td>
</tr>
<tr id="row3963706590"><td class="cellrowborder" valign="top" width="20.2020202020202%" headers="mcps1.2.6.1.1 "><p id="p996314085919"><a name="p996314085919"></a><a name="p996314085919"></a>node.nodeSelector</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.2 "><p id="p1796314045917"><a name="p1796314045917"></a><a name="p1796314045917"></a>Node selector of huawei-csi-node. After this parameter is set, huawei-csi-node will be scheduled only to a node with the label.</p>
</td>
<td class="cellrowborder" valign="top" width="13.13131313131313%" headers="mcps1.2.6.1.3 "><p id="p1296314015593"><a name="p1296314015593"></a><a name="p1296314015593"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.14141414141414%" headers="mcps1.2.6.1.4 "><p id="p1488185514471"><a name="p1488185514471"></a><a name="p1488185514471"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.5 "><p id="p1896315018593"><a name="p1896315018593"></a><a name="p1896315018593"></a>For details about the node selector, see <a href="https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes/#create-a-pod-that-gets-scheduled-to-your-chosen-node" target="_blank" rel="noopener noreferrer">Assign Pods to Nodes</a>.</p>
</td>
</tr>
<tr id="row12963106592"><td class="cellrowborder" valign="top" width="20.2020202020202%" headers="mcps1.2.6.1.1 "><p id="p16964150115915"><a name="p16964150115915"></a><a name="p16964150115915"></a>node.tolerations</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.2 "><p id="p8964205599"><a name="p8964205599"></a><a name="p8964205599"></a>Taint toleration of huawei-csi-node. After this parameter is set, huawei-csi-node can tolerate taints on a node.</p>
</td>
<td class="cellrowborder" valign="top" width="13.13131313131313%" headers="mcps1.2.6.1.3 "><p id="p396420185912"><a name="p396420185912"></a><a name="p396420185912"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.14141414141414%" headers="mcps1.2.6.1.4 ">- key: "node.kubernetes.io/memory-pressure"
  operator: "Exists"
  effect: "NoExecute"
- key: "node.kubernetes.io/disk-pressure"
  operator: "Exists"
  effect: "NoExecute"
- key: "node.kubernetes.io/network-unavailable"
  operator: "Exists"
  effect: "NoExecute"
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.5 "><p id="p596410085910"><a name="p596410085910"></a><a name="p596410085910"></a>For details about taints and tolerations, see <a href="https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/" target="_blank" rel="noopener noreferrer">Taints and Tolerations</a>.</p>
</td>
</tr>
<tr id="row14307151183115"><td class="cellrowborder" valign="top" width="20.2020202020202%" headers="mcps1.2.6.1.1 "><p id="p93081173119"><a name="p93081173119"></a><a name="p93081173119"></a>node.livenessProbePort</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.2 "><p id="p17308619318"><a name="p17308619318"></a><a name="p17308619318"></a>Liveness probe port of huawei-csi-node, used for health check.</p>
</td>
<td class="cellrowborder" valign="top" width="13.13131313131313%" headers="mcps1.2.6.1.3 "><p id="p130881103113"><a name="p130881103113"></a><a name="p130881103113"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.14141414141414%" headers="mcps1.2.6.1.4 "><p id="p93087163114"><a name="p93087163114"></a><a name="p93087163114"></a>9800</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.5 "><p id="p83087111317"><a name="p83087111317"></a><a name="p83087111317"></a>If a port conflict occurs, change the port number to an idle one.</p>
</td>
</tr>
<tr id="row746313162504"><td class="cellrowborder" valign="top" width="20.2020202020202%" headers="mcps1.2.6.1.1 "><p id="p16463161625019"><a name="p16463161625019"></a><a name="p16463161625019"></a>node.kubeletVolumeDevicesDirName</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.2 "><p id="p6463616145011"><a name="p6463616145011"></a><a name="p6463616145011"></a>Name of the directory where a block device is mounted to kubelet.</p>
</td>
<td class="cellrowborder" valign="top" width="13.13131313131313%" headers="mcps1.2.6.1.3 "><p id="p54631016125019"><a name="p54631016125019"></a><a name="p54631016125019"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.14141414141414%" headers="mcps1.2.6.1.4 "><p id="p104631416105012"><a name="p104631416105012"></a><a name="p104631416105012"></a>volumeDevices</p>
</td>
<td class="cellrowborder" valign="top" width="26.26262626262626%" headers="mcps1.2.6.1.5 "><p id="p19463181655017"><a name="p19463181655017"></a><a name="p19463181655017"></a>After a block device is successfully mounted, the directory structure of the mount path is as follows:</p>
/var/lib/kubelet/plugins/kubernetes.io/csi/{kubeletVolumeDevicesDirName}/publish/{specName}/{podUID}
</td>
</tr>
</tbody>
</table>

## csiDriver Parameters{#section389443385812}

The csiDriver parameters include the basic configurations for running Huawei CSI, such as Huawei driver name and multipathing type.

**Table  4**  csiDriver parameters

<a name="table188162213437"></a>
<table><thead align="left"><tr id="row188161721154311"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.1"><p id="p113341565437"><a name="p113341565437"></a><a name="p113341565437"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26%" id="mcps1.2.6.1.2"><p id="p53343568434"><a name="p53343568434"></a><a name="p53343568434"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.3"><p id="p4334185615436"><a name="p4334185615436"></a><a name="p4334185615436"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.4"><p id="p203341356204315"><a name="p203341356204315"></a><a name="p203341356204315"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="26%" id="mcps1.2.6.1.5"><p id="p13933793502"><a name="p13933793502"></a><a name="p13933793502"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row15816202134316"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p6337105774514"><a name="en-us_topic_0000001324610777_p6337105774514"></a><a name="en-us_topic_0000001324610777_p6337105774514"></a>csiDriver.driverName</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p833725774517"><a name="en-us_topic_0000001324610777_p833725774517"></a><a name="en-us_topic_0000001324610777_p833725774517"></a>Registered driver name.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p833755774515"><a name="en-us_topic_0000001324610777_p833755774515"></a><a name="en-us_topic_0000001324610777_p833755774515"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p1033725711455"><a name="en-us_topic_0000001324610777_p1033725711455"></a><a name="en-us_topic_0000001324610777_p1033725711455"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><a name="ul107492610815"></a><a name="ul107492610815"></a><ul id="ul107492610815"><li>Use the default value.</li><li>For the CCE Agile platform, modify this field. For example, <strong id="b131781326101419"><a name="b131781326101419"></a><a name="b131781326101419"></a>csi.oceanstor.com</strong>.</li></ul>
</td>
</tr>
<tr id="row28161921154319"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p183378575452"><a name="en-us_topic_0000001324610777_p183378575452"></a><a name="en-us_topic_0000001324610777_p183378575452"></a>csiDriver.endpoint</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p17337165718459"><a name="en-us_topic_0000001324610777_p17337165718459"></a><a name="en-us_topic_0000001324610777_p17337165718459"></a>Communication endpoint.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p17337195712454"><a name="en-us_topic_0000001324610777_p17337195712454"></a><a name="en-us_topic_0000001324610777_p17337195712454"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p1333735717456"><a name="en-us_topic_0000001324610777_p1333735717456"></a><a name="en-us_topic_0000001324610777_p1333735717456"></a>/csi/csi.sock</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p179331599508"><a name="p179331599508"></a><a name="p179331599508"></a>Use the default value.</p>
</td>
</tr>
<tr id="row1481682113430"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p033795717451"><a name="en-us_topic_0000001324610777_p033795717451"></a><a name="en-us_topic_0000001324610777_p033795717451"></a>csiDriver.connectorThreads</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p163371857164519"><a name="en-us_topic_0000001324610777_p163371857164519"></a><a name="en-us_topic_0000001324610777_p163371857164519"></a>Maximum number of disks that can be concurrently scanned/detached. The value is an integer ranging from 1 to 10.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p12337757144515"><a name="en-us_topic_0000001324610777_p12337757144515"></a><a name="en-us_topic_0000001324610777_p12337757144515"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p2033755784512"><a name="en-us_topic_0000001324610777_p2033755784512"></a><a name="en-us_topic_0000001324610777_p2033755784512"></a>4</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p89333914502"><a name="p89333914502"></a><a name="p89333914502"></a>A larger value indicates that more concurrent disk scanning and detaching operations are performed on a single node at the same time. When DM-Multipath is used, a large number of concurrent requests may cause unknown problems and affect the overall time.</p>
</td>
</tr>
<tr id="row9816112116433"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p2033795719452"><a name="en-us_topic_0000001324610777_p2033795719452"></a><a name="en-us_topic_0000001324610777_p2033795719452"></a>csiDriver.volumeUseMultipath</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p17337185774514"><a name="en-us_topic_0000001324610777_p17337185774514"></a><a name="en-us_topic_0000001324610777_p17337185774514"></a>Whether to use multipathing software. The value is a Boolean value.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p5337135710452"><a name="en-us_topic_0000001324610777_p5337135710452"></a><a name="en-us_topic_0000001324610777_p5337135710452"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p11337205712459"><a name="en-us_topic_0000001324610777_p11337205712459"></a><a name="en-us_topic_0000001324610777_p11337205712459"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p793310955012"><a name="p793310955012"></a><a name="p793310955012"></a>It is strongly recommended that multipathing software be enabled to enhance the redundancy and performance of storage links.</p>
</td>
</tr>
<tr id="row481610211432"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p5337105710453"><a name="en-us_topic_0000001324610777_p5337105710453"></a><a name="en-us_topic_0000001324610777_p5337105710453"></a>csiDriver.scsiMultipathType</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p375115112223"><a name="en-us_topic_0000001324610777_p375115112223"></a><a name="en-us_topic_0000001324610777_p375115112223"></a>Multipathing software used when the storage protocol is <strong id="b189936549396"><a name="b189936549396"></a><a name="b189936549396"></a>fc</strong> or <strong id="b69930545398"><a name="b69930545398"></a><a name="b69930545398"></a>iscsi</strong>. The following parameter values can be configured:</p>
<a name="en-us_topic_0000001324610777_ul260012531222"></a><a name="en-us_topic_0000001324610777_ul260012531222"></a><ul id="en-us_topic_0000001324610777_ul260012531222"><li>DM-multipath</li><li>HW-UltraPath</li><li>HW-UltraPath-NVMe</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p4337155712454"><a name="en-us_topic_0000001324610777_p4337155712454"></a><a name="en-us_topic_0000001324610777_p4337155712454"></a>Mandatory when <strong id="b1590511104016"><a name="b1590511104016"></a><a name="b1590511104016"></a>volumeUseMultipath</strong> is set to <strong id="b1190619118404"><a name="b1190619118404"></a><a name="b1190619118404"></a>true</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p933775734517"><a name="en-us_topic_0000001324610777_p933775734517"></a><a name="en-us_topic_0000001324610777_p933775734517"></a>DM-multipath</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p4933189145013"><a name="p4933189145013"></a><a name="p4933189145013"></a>The <strong id="b326115213403"><a name="b326115213403"></a><a name="b326115213403"></a>DM-multipath</strong> value is recommended.</p>
</td>
</tr>
<tr id="row98161421144310"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p634703417465"><a name="en-us_topic_0000001324610777_p634703417465"></a><a name="en-us_topic_0000001324610777_p634703417465"></a>csiDriver.nvmeMultipathType</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p9347113414463"><a name="en-us_topic_0000001324610777_p9347113414463"></a><a name="en-us_topic_0000001324610777_p9347113414463"></a>Multipathing software used when the storage protocol is <strong id="b1613614119419"><a name="b1613614119419"></a><a name="b1613614119419"></a>roce</strong> or <strong id="b113616194118"><a name="b113616194118"></a><a name="b113616194118"></a>fc-nvme</strong>. Only <strong id="b37779916416"><a name="b37779916416"></a><a name="b37779916416"></a>HW-UltraPath-NVMe</strong> is supported.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p53471934114612"><a name="en-us_topic_0000001324610777_p53471934114612"></a><a name="en-us_topic_0000001324610777_p53471934114612"></a>Mandatory when <strong id="b10123217151614"><a name="b10123217151614"></a><a name="b10123217151614"></a>volumeUseMultipath</strong> is set to <strong id="b10124161751618"><a name="b10124161751618"></a><a name="b10124161751618"></a>true</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p1434717343465"><a name="en-us_topic_0000001324610777_p1434717343465"></a><a name="en-us_topic_0000001324610777_p1434717343465"></a>HW-UltraPath-NVMe</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p199331895507"><a name="p199331895507"></a><a name="p199331895507"></a>-</p>
</td>
</tr>
<tr id="row1081711215431"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p53476342464"><a name="en-us_topic_0000001324610777_p53476342464"></a><a name="en-us_topic_0000001324610777_p53476342464"></a>csiDriver.scanVolumeTimeout</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p182891831165917"><a name="en-us_topic_0000001324610777_p182891831165917"></a><a name="en-us_topic_0000001324610777_p182891831165917"></a>Timeout interval for waiting for multipathing aggregation when DM-Multipath is used on the host. The value ranges from 1 to 600 seconds.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p14347734104616"><a name="en-us_topic_0000001324610777_p14347734104616"></a><a name="en-us_topic_0000001324610777_p14347734104616"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p173472348469"><a name="en-us_topic_0000001324610777_p173472348469"></a><a name="en-us_topic_0000001324610777_p173472348469"></a>3</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p6933189185018"><a name="p6933189185018"></a><a name="p6933189185018"></a>-</p>
</td>
</tr>
<tr id="row41249148199"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1912491441914"><a name="p1912491441914"></a><a name="p1912491441914"></a>csiDriver.execCommandTimeout</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p15124161471913"><a name="p15124161471913"></a><a name="p15124161471913"></a>Timeout interval for running commands on the host.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p712461420194"><a name="p712461420194"></a><a name="p712461420194"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p412471411917"><a name="p412471411917"></a><a name="p412471411917"></a>30</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p8124314171910"><a name="p8124314171910"></a><a name="p8124314171910"></a>In scenarios such as mounting and capacity expansion, the CSI plug-in needs to run some host commands, for example, running the <strong id="b14252141604714"><a name="b14252141604714"></a><a name="b14252141604714"></a>mount</strong> command to mount a file system. This parameter is used to control the timeout interval for running a single command.</p>
</td>
</tr>
<tr id="row73274310332"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1460663514512"><a name="p1460663514512"></a><a name="p1460663514512"></a>csiDriver.allPathOnline</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p46061935154513"><a name="p46061935154513"></a><a name="p46061935154513"></a>Whether to check whether the number of paths aggregated by DM-Multipath is equal to the actual number of online paths. The following parameter values can be configured:</p>
<a name="ul107341114134816"></a><a name="ul107341114134816"></a><ul id="ul107341114134816"><li><strong id="b219535212295"><a name="b219535212295"></a><a name="b219535212295"></a>true</strong>: The drive letter mounting condition is met only when the number of paths aggregated by DM-Multipath is equal to the actual number of online paths.</li><li><strong id="b163220514303"><a name="b163220514303"></a><a name="b163220514303"></a>false</strong>: By default, the number of paths aggregated by DM-Multipath is not checked. As long as virtual drive letters are generated upon aggregation, the drive letter mounting condition is met.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p4606133516456"><a name="p4606133516456"></a><a name="p4606133516456"></a>This parameter is mandatory when <strong id="b11700644123220"><a name="b11700644123220"></a><a name="b11700644123220"></a>csiDriver.scsiMultipathType</strong> is set to <strong id="b370118444322"><a name="b370118444322"></a><a name="b370118444322"></a>DM-multipath</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p960673554519"><a name="p960673554519"></a><a name="p960673554519"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p126067351454"><a name="p126067351454"></a><a name="p126067351454"></a>-</p>
</td>
</tr>
<tr id="row14448563444"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p93478341469"><a name="en-us_topic_0000001324610777_p93478341469"></a><a name="en-us_topic_0000001324610777_p93478341469"></a>csiDriver.backendUpdateInterval</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p7347193474618"><a name="en-us_topic_0000001324610777_p7347193474618"></a><a name="en-us_topic_0000001324610777_p7347193474618"></a>Interval for updating backend capabilities. The value ranges from 60 to 600 seconds.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1347634204613"><a name="en-us_topic_0000001324610777_p1347634204613"></a><a name="en-us_topic_0000001324610777_p1347634204613"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p9347034114612"><a name="en-us_topic_0000001324610777_p9347034114612"></a><a name="en-us_topic_0000001324610777_p9347034114612"></a>60</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p1293417910509"><a name="p1293417910509"></a><a name="p1293417910509"></a>-</p>
</td>
</tr>
<tr id="row744456104419"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p1434713454612"><a name="en-us_topic_0000001324610777_p1434713454612"></a><a name="en-us_topic_0000001324610777_p1434713454612"></a>csiDriver.controllerLogging.module</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p3624521162211"><a name="en-us_topic_0000001324610777_p3624521162211"></a><a name="en-us_topic_0000001324610777_p3624521162211"></a>Record type of the controller log. The following parameter values can be configured:</p>
<a name="en-us_topic_0000001324610777_ul06981143132310"></a><a name="en-us_topic_0000001324610777_ul06981143132310"></a><ul id="en-us_topic_0000001324610777_ul06981143132310"><li>file</li><li>console</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p6347234114616"><a name="en-us_topic_0000001324610777_p6347234114616"></a><a name="en-us_topic_0000001324610777_p6347234114616"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p034743494615"><a name="en-us_topic_0000001324610777_p034743494615"></a><a name="en-us_topic_0000001324610777_p034743494615"></a>file</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p4934799502"><a name="p4934799502"></a><a name="p4934799502"></a>When the value is <strong id="b1888825594112"><a name="b1888825594112"></a><a name="b1888825594112"></a>file</strong>, logs are retained in the specified directory of the node. When the Pod where CSI is located is destroyed, logs are still retained.</p>
<p id="p067035825718"><a name="p067035825718"></a><a name="p067035825718"></a>When the value is <strong id="b1537911034217"><a name="b1537911034217"></a><a name="b1537911034217"></a>console</strong>, logs are retained in the temporary space of the Pod where CSI is located. When the Pod where CSI is located is destroyed, the logs are also destroyed.</p>
</td>
</tr>
<tr id="row19444564449"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p4347183444613"><a name="en-us_topic_0000001324610777_p4347183444613"></a><a name="en-us_topic_0000001324610777_p4347183444613"></a>csiDriver.controllerLogging.level</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p16417137154310"><a name="en-us_topic_0000001324610777_p16417137154310"></a><a name="en-us_topic_0000001324610777_p16417137154310"></a>Output level of the controller log. The following parameter values can be configured:</p>
<a name="en-us_topic_0000001324610777_ul1167154320240"></a><a name="en-us_topic_0000001324610777_ul1167154320240"></a><ul id="en-us_topic_0000001324610777_ul1167154320240"><li>debug</li><li>info</li><li>warning</li><li>error</li><li>fatal</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p17347834154617"><a name="en-us_topic_0000001324610777_p17347834154617"></a><a name="en-us_topic_0000001324610777_p17347834154617"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p1834720346469"><a name="en-us_topic_0000001324610777_p1834720346469"></a><a name="en-us_topic_0000001324610777_p1834720346469"></a>info</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p139341498509"><a name="p139341498509"></a><a name="p139341498509"></a>-</p>
</td>
</tr>
<tr id="row5443565449"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p13471434164616"><a name="en-us_topic_0000001324610777_p13471434164616"></a><a name="en-us_topic_0000001324610777_p13471434164616"></a>csiDriver.controllerLogging.fileDir</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p10347153410468"><a name="en-us_topic_0000001324610777_p10347153410468"></a><a name="en-us_topic_0000001324610777_p10347153410468"></a>Directory of the controller log in <strong id="b10369222124216"><a name="b10369222124216"></a><a name="b10369222124216"></a>file</strong> output mode.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p0347534194610"><a name="en-us_topic_0000001324610777_p0347534194610"></a><a name="en-us_topic_0000001324610777_p0347534194610"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p103471434184614"><a name="en-us_topic_0000001324610777_p103471434184614"></a><a name="en-us_topic_0000001324610777_p103471434184614"></a>/var/log/huawei</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p1093411975015"><a name="p1093411975015"></a><a name="p1093411975015"></a>Ensure that the directory has sufficient space for storing logs. It is recommended that the space be greater than or equal to 200 MB.</p>
</td>
</tr>
<tr id="row1778411129457"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p17348134104614"><a name="en-us_topic_0000001324610777_p17348134104614"></a><a name="en-us_topic_0000001324610777_p17348134104614"></a>csiDriver.controllerLogging.fileSize</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p203487346467"><a name="en-us_topic_0000001324610777_p203487346467"></a><a name="en-us_topic_0000001324610777_p203487346467"></a>Size of a single controller log file in <strong id="b20169204084220"><a name="b20169204084220"></a><a name="b20169204084220"></a>file</strong> output mode.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p334833444618"><a name="en-us_topic_0000001324610777_p334833444618"></a><a name="en-us_topic_0000001324610777_p334833444618"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p134813417469"><a name="en-us_topic_0000001324610777_p134813417469"></a><a name="en-us_topic_0000001324610777_p134813417469"></a>20M</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p1093411995013"><a name="p1093411995013"></a><a name="p1093411995013"></a>-</p>
</td>
</tr>
<tr id="row4961918134510"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p1134873412462"><a name="en-us_topic_0000001324610777_p1134873412462"></a><a name="en-us_topic_0000001324610777_p1134873412462"></a>csiDriver.controllerLogging.maxBackups</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p53481034164619"><a name="en-us_topic_0000001324610777_p53481034164619"></a><a name="en-us_topic_0000001324610777_p53481034164619"></a>Maximum number of controller log file backups in <strong id="b42803459427"><a name="b42803459427"></a><a name="b42803459427"></a>file</strong> output mode.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p19348193414465"><a name="en-us_topic_0000001324610777_p19348193414465"></a><a name="en-us_topic_0000001324610777_p19348193414465"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p15348163419463"><a name="en-us_topic_0000001324610777_p15348163419463"></a><a name="en-us_topic_0000001324610777_p15348163419463"></a>9</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p12934890500"><a name="p12934890500"></a><a name="p12934890500"></a>-</p>
</td>
</tr>
<tr id="row1978411274511"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p1234812347465"><a name="en-us_topic_0000001324610777_p1234812347465"></a><a name="en-us_topic_0000001324610777_p1234812347465"></a>csiDriver.nodeLogging.module</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p2508115722612"><a name="en-us_topic_0000001324610777_p2508115722612"></a><a name="en-us_topic_0000001324610777_p2508115722612"></a>Record type of the node log. The following parameter values can be configured:</p>
<a name="en-us_topic_0000001324610777_ul35081257192610"></a><a name="en-us_topic_0000001324610777_ul35081257192610"></a><ul id="en-us_topic_0000001324610777_ul35081257192610"><li>file</li><li>console</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p20348234114615"><a name="en-us_topic_0000001324610777_p20348234114615"></a><a name="en-us_topic_0000001324610777_p20348234114615"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p103486342462"><a name="en-us_topic_0000001324610777_p103486342462"></a><a name="en-us_topic_0000001324610777_p103486342462"></a>file</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p67624161807"><a name="p67624161807"></a><a name="p67624161807"></a>When the value is <strong id="b1429803195"><a name="b1429803195"></a><a name="b1429803195"></a>file</strong>, logs are retained in the specified directory of the node. When the Pod where CSI is located is destroyed, logs are still retained.</p>
<p id="p1676211161707"><a name="p1676211161707"></a><a name="p1676211161707"></a>When the value is <strong id="b134821913194316"><a name="b134821913194316"></a><a name="b134821913194316"></a>console</strong>, logs are retained in the temporary space of the Pod where CSI is located. When the Pod where CSI is located is destroyed, the logs are also destroyed.</p>
</td>
</tr>
<tr id="row47847123452"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p1934818348469"><a name="en-us_topic_0000001324610777_p1934818348469"></a><a name="en-us_topic_0000001324610777_p1934818348469"></a>csiDriver.nodeLogging.level</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p1612112242711"><a name="en-us_topic_0000001324610777_p1612112242711"></a><a name="en-us_topic_0000001324610777_p1612112242711"></a>Output level of the node log. The following parameter values can be configured:</p>
<a name="en-us_topic_0000001324610777_ul1561292212717"></a><a name="en-us_topic_0000001324610777_ul1561292212717"></a><ul id="en-us_topic_0000001324610777_ul1561292212717"><li>debug</li><li>info</li><li>warning</li><li>error</li><li>fatal</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p334873415469"><a name="en-us_topic_0000001324610777_p334873415469"></a><a name="en-us_topic_0000001324610777_p334873415469"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p7348113416469"><a name="en-us_topic_0000001324610777_p7348113416469"></a><a name="en-us_topic_0000001324610777_p7348113416469"></a>info</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p593459175013"><a name="p593459175013"></a><a name="p593459175013"></a>-</p>
</td>
</tr>
<tr id="row11785121220453"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p7348234104611"><a name="en-us_topic_0000001324610777_p7348234104611"></a><a name="en-us_topic_0000001324610777_p7348234104611"></a>csiDriver.nodeLogging.fileDir</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p1750544317272"><a name="en-us_topic_0000001324610777_p1750544317272"></a><a name="en-us_topic_0000001324610777_p1750544317272"></a>Directory of the node log in <strong id="b399243218436"><a name="b399243218436"></a><a name="b399243218436"></a>file</strong> output mode.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p10348193494619"><a name="en-us_topic_0000001324610777_p10348193494619"></a><a name="en-us_topic_0000001324610777_p10348193494619"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p034893417469"><a name="en-us_topic_0000001324610777_p034893417469"></a><a name="en-us_topic_0000001324610777_p034893417469"></a>/var/log/huawei</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p1993429105012"><a name="p1993429105012"></a><a name="p1993429105012"></a>Ensure that the directory has sufficient space for storing logs. It is recommended that the space be greater than or equal to 200 MB.</p>
</td>
</tr>
<tr id="row078551284516"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p73486347467"><a name="en-us_topic_0000001324610777_p73486347467"></a><a name="en-us_topic_0000001324610777_p73486347467"></a>csiDriver.nodeLogging.fileSize</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p0505114315275"><a name="en-us_topic_0000001324610777_p0505114315275"></a><a name="en-us_topic_0000001324610777_p0505114315275"></a>Size of a single node log file in <strong id="b17827503433"><a name="b17827503433"></a><a name="b17827503433"></a>file</strong> output mode.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p634819343466"><a name="en-us_topic_0000001324610777_p634819343466"></a><a name="en-us_topic_0000001324610777_p634819343466"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p19348234184616"><a name="en-us_topic_0000001324610777_p19348234184616"></a><a name="en-us_topic_0000001324610777_p19348234184616"></a>20M</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p1693417913501"><a name="p1693417913501"></a><a name="p1693417913501"></a>-</p>
</td>
</tr>
<tr id="row121518222466"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p62151622154612"><a name="p62151622154612"></a><a name="p62151622154612"></a>csiDriver.nodeLogging.maxBackups</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p3215142212469"><a name="p3215142212469"></a><a name="p3215142212469"></a>Maximum number of node log file backups in <strong id="b18568908441"><a name="b18568908441"></a><a name="b18568908441"></a>file</strong> output mode.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p1121582215465"><a name="p1121582215465"></a><a name="p1121582215465"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p621572294611"><a name="p621572294611"></a><a name="p621572294611"></a>9</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p493411995018"><a name="p493411995018"></a><a name="p493411995018"></a>-</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/en/icon-notice.gif) 
>If Huawei CSI has been deployed in your container environment, ensure that the value of  **csiDriver.driverName**  is the same as that configured during previous deployment. Otherwise, existing volumes or snapshots provisioned by Huawei CSI in the system cannot be managed by the newly deployed Huawei CSI.

## Other Parameters{#section11500468593}

Other parameters include some features of the CSI plug-in or the policies for obtaining images.

**Table  5**  Other parameters

<a name="table258712427285"></a>
<table><thead align="left"><tr id="row1858810426284"><th class="cellrowborder" valign="top" width="19%" id="mcps1.2.6.1.1"><p id="p65678447283"><a name="p65678447283"></a><a name="p65678447283"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26%" id="mcps1.2.6.1.2"><p id="p9567104432815"><a name="p9567104432815"></a><a name="p9567104432815"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.6.1.3"><p id="p656710441284"><a name="p656710441284"></a><a name="p656710441284"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.4"><p id="p056794462811"><a name="p056794462811"></a><a name="p056794462811"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="26%" id="mcps1.2.6.1.5"><p id="p248511121014"><a name="p248511121014"></a><a name="p248511121014"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row10113115012328"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p15337957144510"><a name="en-us_topic_0000001324610777_p15337957144510"></a><a name="en-us_topic_0000001324610777_p15337957144510"></a>kubernetes.namespace</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p123372572455"><a name="en-us_topic_0000001324610777_p123372572455"></a><a name="en-us_topic_0000001324610777_p123372572455"></a>Kubernetes namespace where Huawei CSI is running, which can be customized. The name must consist of lowercase letters, digits, and hyphens (-), for example, <strong id="b7960249174512"><a name="b7960249174512"></a><a name="b7960249174512"></a>my-name</strong> and <strong id="b4960154974518"><a name="b4960154974518"></a><a name="b4960154974518"></a>123-abc</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p633705711458"><a name="en-us_topic_0000001324610777_p633705711458"></a><a name="en-us_topic_0000001324610777_p633705711458"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p1633715784512"><a name="en-us_topic_0000001324610777_p1633715784512"></a><a name="en-us_topic_0000001324610777_p1633715784512"></a>huawei-csi</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p144858121013"><a name="p144858121013"></a><a name="p144858121013"></a>-</p>
</td>
</tr>
<tr id="row1723613654416"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="p1423618610447"><a name="p1423618610447"></a><a name="p1423618610447"></a>kubeletConfigDir</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p1023613610444"><a name="p1023613610444"></a><a name="p1023613610444"></a>Working directory of kubelet.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p2236176194414"><a name="p2236176194414"></a><a name="p2236176194414"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p112361667445"><a name="p112361667445"></a><a name="p112361667445"></a>/var/lib/kubelet</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><a name="ul18493162309"></a><a name="ul18493162309"></a><ul id="ul18493162309"><li>Use the default value.</li><li>For the Tanzu platform, change the value of this field to <strong id="b10313124152"><a name="b10313124152"></a><a name="b10313124152"></a>/var/vcap/data/kubelet</strong>.</li><li>For the CCE Agile platform, change the value of this field to <strong id="b191151616121519"><a name="b191151616121519"></a><a name="b191151616121519"></a>/mnt/paas/kubernetes/kubelet</strong>.</li></ul>
</td>
</tr>
<tr id="row0588342152819"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p12348334144611"><a name="en-us_topic_0000001324610777_p12348334144611"></a><a name="en-us_topic_0000001324610777_p12348334144611"></a>sidecarImagePullPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p113481634194616"><a name="en-us_topic_0000001324610777_p113481634194616"></a><a name="en-us_topic_0000001324610777_p113481634194616"></a>Pull policy of the sidecar image.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1134803416462"><a name="en-us_topic_0000001324610777_p1134803416462"></a><a name="en-us_topic_0000001324610777_p1134803416462"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p33489342465"><a name="en-us_topic_0000001324610777_p33489342465"></a><a name="en-us_topic_0000001324610777_p33489342465"></a>IfNotPresent</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p18485411109"><a name="p18485411109"></a><a name="p18485411109"></a>-</p>
</td>
</tr>
<tr id="row3588104242816"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p7348034124617"><a name="en-us_topic_0000001324610777_p7348034124617"></a><a name="en-us_topic_0000001324610777_p7348034124617"></a>huaweiImagePullPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p734818345469"><a name="en-us_topic_0000001324610777_p734818345469"></a><a name="en-us_topic_0000001324610777_p734818345469"></a>Pull policy of the huawei-csi image.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p934816348468"><a name="en-us_topic_0000001324610777_p934816348468"></a><a name="en-us_topic_0000001324610777_p934816348468"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0000001324610777_p834883414468"><a name="en-us_topic_0000001324610777_p834883414468"></a><a name="en-us_topic_0000001324610777_p834883414468"></a>IfNotPresent</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p10485101141015"><a name="p10485101141015"></a><a name="p10485101141015"></a>-</p>
</td>
</tr>
<tr id="row1670374213211"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="p177048426324"><a name="p177048426324"></a><a name="p177048426324"></a>CSIDriverObject.isCreate</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p67047427323"><a name="p67047427323"></a><a name="p67047427323"></a>Whether to create the CSIDriver object.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p370474273215"><a name="p370474273215"></a><a name="p370474273215"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p117042042153214"><a name="p117042042153214"></a><a name="p117042042153214"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p670464213219"><a name="p670464213219"></a><a name="p670464213219"></a>The <a href="https://kubernetes-csi.github.io/docs/csi-driver-object.html" target="_blank" rel="noopener noreferrer">CSIDriver</a> feature is a GA version in Kubernetes v1.18. Therefore, to use this feature, the Kubernetes version must be later than v1.18. If the Kubernetes version is earlier than v1.18, set this parameter to <strong id="b123811772351"><a name="b123811772351"></a><a name="b123811772351"></a>false</strong>.</p>
</td>
</tr>
<tr id="row5325193974610"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="p11570469462"><a name="p11570469462"></a><a name="p11570469462"></a>CSIDriverObject.attachRequired</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p191571546164615"><a name="p191571546164615"></a><a name="p191571546164615"></a>Whether the CSI plug-in skips the attach operation. The following parameter values can be configured:</p>
<a name="ul4731114312531"></a><a name="ul4731114312531"></a><ul id="ul4731114312531"><li><strong id="b10943152417476"><a name="b10943152417476"></a><a name="b10943152417476"></a>true</strong>: The attach operation is required.</li><li><strong id="b123881729194714"><a name="b123881729194714"></a><a name="b123881729194714"></a>false</strong>: The attach operation is skipped.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1157114617462"><a name="p1157114617462"></a><a name="p1157114617462"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p515714616460"><a name="p515714616460"></a><a name="p515714616460"></a>true</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p106733391199"><a name="p106733391199"></a><a name="p106733391199"></a>The <a href="https://kubernetes-csi.github.io/docs/csi-driver-object.html" target="_blank" rel="noopener noreferrer">attachRequired</a> parameter can be configured in Kubernetes v1.18.</p>
<p id="p87615434538"><a name="p87615434538"></a><a name="p87615434538"></a>If <strong id="b1892112273614"><a name="b1892112273614"></a><a name="b1892112273614"></a>CSIDriverObject.isCreate</strong> is set to <strong id="b15388619362"><a name="b15388619362"></a><a name="b15388619362"></a>true</strong> and <strong id="b188322863618"><a name="b188322863618"></a><a name="b188322863618"></a>attachRequired</strong> is set to <strong id="b8561181114366"><a name="b8561181114366"></a><a name="b8561181114366"></a>false</strong>, the huawei-csi plug-in will not deploy the csi-attacher sidecar.</p>
<a name="ul5512181115174"></a><a name="ul5512181115174"></a><ul id="ul5512181115174"><li>If NAS storage is used, this parameter can be set to <strong id="b1417443617363"><a name="b1417443617363"></a><a name="b1417443617363"></a>false</strong>.</li><li>If SAN storage is used, set this parameter to <strong id="b181703598470"><a name="b181703598470"></a><a name="b181703598470"></a>true</strong>.</li></ul>
</td>
</tr>
<tr id="row890414451319"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="p498831161311"><a name="p498831161311"></a><a name="p498831161311"></a>CSIDriverObject.fsGroupPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p1298810111139"><a name="p1298810111139"></a><a name="p1298810111139"></a>Whether the ownership and permissions of a basic volume can be changed before the volume is mounted. The following parameter values can be configured:</p>
<a name="ul1988191110133"></a><a name="ul1988191110133"></a><ul id="ul1988191110133"><li><strong id="b11757125816481"><a name="b11757125816481"></a><a name="b11757125816481"></a>"ReadWriteOnceWithFSType"</strong>: The volume ownership and permission can be changed only when <strong id="b153739854918"><a name="b153739854918"></a><a name="b153739854918"></a>fsType</strong> is specified and <strong id="b10473619174916"><a name="b10473619174916"></a><a name="b10473619174916"></a>accessModes</strong> of the volume contains <strong id="b18125727114913"><a name="b18125727114913"></a><a name="b18125727114913"></a>ReadWriteOnce</strong>.</li><li><strong id="b921173212492"><a name="b921173212492"></a><a name="b921173212492"></a>"File"</strong>: Kubernetes can use <strong id="b8999113718206"><a name="b8999113718206"></a><a name="b8999113718206"></a>fsGroup</strong> to change the permissions and ownership of a volume to match <strong id="b1929510499201"><a name="b1929510499201"></a><a name="b1929510499201"></a>fsGroup</strong> requested by a user in the Pod security policy, regardless of <strong id="b4272343218"><a name="b4272343218"></a><a name="b4272343218"></a>fsGroup</strong> or <strong id="b1678393019209"><a name="b1678393019209"></a><a name="b1678393019209"></a>accessModes</strong>.</li><li><strong id="b338051305014"><a name="b338051305014"></a><a name="b338051305014"></a>"None"</strong>: A volume is mounted without any change.</li><li><strong id="b146621687387"><a name="b146621687387"></a><a name="b146621687387"></a>"null"</strong>: The <strong id="b1335918135381"><a name="b1335918135381"></a><a name="b1335918135381"></a>fsGroupPolicy</strong> parameter is not set.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p159881411191317"><a name="p159881411191317"></a><a name="p159881411191317"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p1698811110137"><a name="p1698811110137"></a><a name="p1698811110137"></a>null</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p14641734132114"><a name="p14641734132114"></a><a name="p14641734132114"></a>The <a href="https://kubernetes-csi.github.io/docs/csi-driver-object.html" target="_blank" rel="noopener noreferrer">fsGroupPolicy</a> parameter can be configured in Kubernetes v1.20, and takes effect only when <strong id="b181911246123716"><a name="b181911246123716"></a><a name="b181911246123716"></a>CSIDriverObject.isCreate</strong> is set to <strong id="b85412488378"><a name="b85412488378"></a><a name="b85412488378"></a>true</strong>.</p>
<p id="p20988811151315"><a name="p20988811151315"></a><a name="p20988811151315"></a>This feature is a Beta version in Kubernetes v1.20 but a GA version in Kubernetes v1.23. Therefore, the Kubernetes version must be later than v1.20.</p>
</td>
</tr>
<tr id="row1921061519422"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="p721081512429"><a name="p721081512429"></a><a name="p721081512429"></a>leaderElection.leaseDuration</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p16210151544212"><a name="p16210151544212"></a><a name="p16210151544212"></a>Leader duration.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p14210121524211"><a name="p14210121524211"></a><a name="p14210121524211"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p1221071514218"><a name="p1221071514218"></a><a name="p1221071514218"></a>8s</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p7210121554213"><a name="p7210121554213"></a><a name="p7210121554213"></a>This parameter takes effect only in the multi-controller scenario.</p>
</td>
</tr>
<tr id="row141688824315"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="p3168283431"><a name="p3168283431"></a><a name="p3168283431"></a>leaderElection.renewDeadline</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p141685884315"><a name="p141685884315"></a><a name="p141685884315"></a>Time for the leader to be re-elected.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p11680894311"><a name="p11680894311"></a><a name="p11680894311"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p3168888435"><a name="p3168888435"></a><a name="p3168888435"></a>6s</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p616888134320"><a name="p616888134320"></a><a name="p616888134320"></a>This parameter takes effect only in the multi-controller scenario.</p>
</td>
</tr>
<tr id="row13567171024310"><td class="cellrowborder" valign="top" width="19%" headers="mcps1.2.6.1.1 "><p id="p6568191094318"><a name="p6568191094318"></a><a name="p6568191094318"></a>leaderElection.retryPeriod</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p3568141019435"><a name="p3568141019435"></a><a name="p3568141019435"></a>Leader election retry time.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p10568910134310"><a name="p10568910134310"></a><a name="p10568910134310"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.4 "><p id="p155681010134316"><a name="p155681010134316"></a><a name="p155681010134316"></a>2s</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.5 "><p id="p165681710114315"><a name="p165681710114315"></a><a name="p165681710114315"></a>This parameter takes effect only in the multi-controller scenario.</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/en/icon-notice.gif) 
>Ensure that the namespace entered in  **kubernetes.namespace**  exists on Kubernetes. If the namespace does not exist, run the following command to create it. In this example, the namespace for running Huawei CSI is  **huawei-csi**.
>```
>kubectl create namespace huawei-csi
>```

