---
title: "华为CSI资源管理"
linkTitle: "华为CSI资源管理"
description: 
weight: 6
---

本章节列举了华为CSI插件中每个容器所使用的资源请求和限制。其中单位说明请参考[Kubernetes 中的资源单位](https://kubernetes.io/zh-cn/docs/concepts/configuration/manage-resources-containers/#resource-units-in-kubernetes)。

**表 1**  容器资源请求和限制

<a name="table4106151116363"></a>
<table><thead align="left"><tr id="row131061011123614"><th class="cellrowborder" valign="top" width="20.022002200220022%" id="mcps1.2.7.1.1"><p id="p210671110368"><a name="p210671110368"></a><a name="p210671110368"></a>Pod 名称</p>
</th>
<th class="cellrowborder" valign="top" width="20.132013201320138%" id="mcps1.2.7.1.2"><p id="p1110641123613"><a name="p1110641123613"></a><a name="p1110641123613"></a>容器名称</p>
</th>
<th class="cellrowborder" valign="top" width="14.951495149514955%" id="mcps1.2.7.1.3"><p id="p13106111123616"><a name="p13106111123616"></a><a name="p13106111123616"></a>CPU 请求</p>
</th>
<th class="cellrowborder" valign="top" width="14.971497149714974%" id="mcps1.2.7.1.4"><p id="p16106141193612"><a name="p16106141193612"></a><a name="p16106141193612"></a>CPU 限制</p>
</th>
<th class="cellrowborder" valign="top" width="14.961496149614966%" id="mcps1.2.7.1.5"><p id="p1859019004018"><a name="p1859019004018"></a><a name="p1859019004018"></a>Memory 请求</p>
</th>
<th class="cellrowborder" valign="top" width="14.961496149614966%" id="mcps1.2.7.1.6"><p id="p759011074012"><a name="p759011074012"></a><a name="p759011074012"></a>Memory 限制</p>
</th>
</tr>
</thead>
<tbody><tr id="row1410617113360"><td class="cellrowborder" rowspan="10" align="left" valign="top" width="20.022002200220022%" headers="mcps1.2.7.1.1 "><p id="p12106711173612"><a name="p12106711173612"></a><a name="p12106711173612"></a>huawei-csi-controller</p>
</td>
<td class="cellrowborder" valign="top" width="20.132013201320138%" headers="mcps1.2.7.1.2 "><p id="p203561471148"><a name="p203561471148"></a><a name="p203561471148"></a>huawei-csi-driver</p>
</td>
<td class="cellrowborder" valign="top" width="14.951495149514955%" headers="mcps1.2.7.1.3 "><p id="p1410691114363"><a name="p1410691114363"></a><a name="p1410691114363"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" width="14.971497149714974%" headers="mcps1.2.7.1.4 "><p id="p101068119366"><a name="p101068119366"></a><a name="p101068119366"></a>500m</p>
</td>
<td class="cellrowborder" valign="top" width="14.961496149614966%" headers="mcps1.2.7.1.5 "><p id="p5106151123614"><a name="p5106151123614"></a><a name="p5106151123614"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" width="14.961496149614966%" headers="mcps1.2.7.1.6 "><p id="p1810641153618"><a name="p1810641153618"></a><a name="p1810641153618"></a>1Gi</p>
</td>
</tr>
<tr id="row110621117367"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p163578472412"><a name="p163578472412"></a><a name="p163578472412"></a>storage-backend-sidecar</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p1610671183614"><a name="p1610671183614"></a><a name="p1610671183614"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p61581135114813"><a name="p61581135114813"></a><a name="p61581135114813"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p4757124517489"><a name="p4757124517489"></a><a name="p4757124517489"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p83571147748"><a name="p83571147748"></a><a name="p83571147748"></a>512Mi</p>
</td>
</tr>
<tr id="row210615118362"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p153574471746"><a name="p153574471746"></a><a name="p153574471746"></a>storage-backend-controller</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p141061711183613"><a name="p141061711183613"></a><a name="p141061711183613"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p1163203634812"><a name="p1163203634812"></a><a name="p1163203634812"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p1130414612485"><a name="p1130414612485"></a><a name="p1130414612485"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p33573471747"><a name="p33573471747"></a><a name="p33573471747"></a>512Mi</p>
</td>
</tr>
<tr id="row247533714401"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p174756378403"><a name="p174756378403"></a><a name="p174756378403"></a>huawei-csi-extender</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p164756370401"><a name="p164756370401"></a><a name="p164756370401"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p11475123794016"><a name="p11475123794016"></a><a name="p11475123794016"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p1547573710407"><a name="p1547573710407"></a><a name="p1547573710407"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p1347520377408"><a name="p1347520377408"></a><a name="p1347520377408"></a>512Mi</p>
</td>
</tr>
<tr id="row4107611173614"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p173573478411"><a name="p173573478411"></a><a name="p173573478411"></a>csi-attacher</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p74288152500"><a name="p74288152500"></a><a name="p74288152500"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p13107511123616"><a name="p13107511123616"></a><a name="p13107511123616"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p975194719487"><a name="p975194719487"></a><a name="p975194719487"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p935716471142"><a name="p935716471142"></a><a name="p935716471142"></a>512Mi</p>
</td>
</tr>
<tr id="row131071311153611"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p135774719410"><a name="p135774719410"></a><a name="p135774719410"></a>csi-provisioner</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p18428111585012"><a name="p18428111585012"></a><a name="p18428111585012"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p4534744175020"><a name="p4534744175020"></a><a name="p4534744175020"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p6761947104814"><a name="p6761947104814"></a><a name="p6761947104814"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p1135764717411"><a name="p1135764717411"></a><a name="p1135764717411"></a>512Mi</p>
</td>
</tr>
<tr id="row1110861113617"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p103571547841"><a name="p103571547841"></a><a name="p103571547841"></a>csi-resize</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p194284150502"><a name="p194284150502"></a><a name="p194284150502"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p3144194595015"><a name="p3144194595015"></a><a name="p3144194595015"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p1641825274814"><a name="p1641825274814"></a><a name="p1641825274814"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p335710477411"><a name="p335710477411"></a><a name="p335710477411"></a>512Mi</p>
</td>
</tr>
<tr id="row3919175014413"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p1635711471247"><a name="p1635711471247"></a><a name="p1635711471247"></a>csi-snapshotter</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p18275151810505"><a name="p18275151810505"></a><a name="p18275151810505"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p9641122585116"><a name="p9641122585116"></a><a name="p9641122585116"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p141915211487"><a name="p141915211487"></a><a name="p141915211487"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p9107847205119"><a name="p9107847205119"></a><a name="p9107847205119"></a>512Mi</p>
</td>
</tr>
<tr id="row11704145044115"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p43581947845"><a name="p43581947845"></a><a name="p43581947845"></a>snapshot-controller</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p142751918185015"><a name="p142751918185015"></a><a name="p142751918185015"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p7641125165114"><a name="p7641125165114"></a><a name="p7641125165114"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p12419155218484"><a name="p12419155218484"></a><a name="p12419155218484"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p2107134716518"><a name="p2107134716518"></a><a name="p2107134716518"></a>512Mi</p>
</td>
</tr>
<tr id="row8401617164917"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p1541817204910"><a name="p1541817204910"></a><a name="p1541817204910"></a>liveness-probe</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p027511186507"><a name="p027511186507"></a><a name="p027511186507"></a>10m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p4641162516512"><a name="p4641162516512"></a><a name="p4641162516512"></a>100m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p5416174491"><a name="p5416174491"></a><a name="p5416174491"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p610711476511"><a name="p610711476511"></a><a name="p610711476511"></a>128Mi</p>
</td>
</tr>
<tr id="row115187505412"><td class="cellrowborder" rowspan="3" align="left" valign="top" width="20.022002200220022%" headers="mcps1.2.7.1.1 "><p id="p1751885019415"><a name="p1751885019415"></a><a name="p1751885019415"></a>huawei-csi-node</p>
</td>
<td class="cellrowborder" valign="top" width="20.132013201320138%" headers="mcps1.2.7.1.2 "><p id="p251875084118"><a name="p251875084118"></a><a name="p251875084118"></a>huawei-csi-driver</p>
</td>
<td class="cellrowborder" valign="top" width="14.951495149514955%" headers="mcps1.2.7.1.3 "><p id="p627581812504"><a name="p627581812504"></a><a name="p627581812504"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" width="14.971497149714974%" headers="mcps1.2.7.1.4 "><p id="p1038372718517"><a name="p1038372718517"></a><a name="p1038372718517"></a>500m</p>
</td>
<td class="cellrowborder" valign="top" width="14.961496149614966%" headers="mcps1.2.7.1.5 "><p id="p3419105244811"><a name="p3419105244811"></a><a name="p3419105244811"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" width="14.961496149614966%" headers="mcps1.2.7.1.6 "><p id="p910714473510"><a name="p910714473510"></a><a name="p910714473510"></a>1Gi</p>
</td>
</tr>
<tr id="row935545014415"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p8355750114116"><a name="p8355750114116"></a><a name="p8355750114116"></a>csi-node-driver-registrar</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p11275131811509"><a name="p11275131811509"></a><a name="p11275131811509"></a>50m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p3383122720510"><a name="p3383122720510"></a><a name="p3383122720510"></a>300m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p62875419489"><a name="p62875419489"></a><a name="p62875419489"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p21071647115118"><a name="p21071647115118"></a><a name="p21071647115118"></a>128Mi</p>
</td>
</tr>
<tr id="row618465014414"><td class="cellrowborder" valign="top" headers="mcps1.2.7.1.1 "><p id="p1518416506417"><a name="p1518416506417"></a><a name="p1518416506417"></a>liveness-probe</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.2 "><p id="p182750181507"><a name="p182750181507"></a><a name="p182750181507"></a>10m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.3 "><p id="p18383227195110"><a name="p18383227195110"></a><a name="p18383227195110"></a>100m</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.4 "><p id="p132812542485"><a name="p132812542485"></a><a name="p132812542485"></a>128Mi</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.7.1.5 "><p id="p1418412507416"><a name="p1418412507416"></a><a name="p1418412507416"></a>128Mi</p>
</td>
</tr>
</tbody>
</table>

## 修改资源请求和限制{#section61471438195712}

如果需要修改容器的资源请求和限制，以Helm安装华为CSI为例，可参考以下步骤

1.  使用Helm安装时进入/helm/esdk/templates 目录。手动部署时需要修改的文件在/manual/esdk/deploy目录，其中组件包路径请参考[表1](/v4.5.0/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。
2.  修改部署模板文件。

    -   Pod名称为huawei-csi-controller时，修改huawei-csi-controller.yaml文件。
    -   Pod名称为huawei-csi-node时，修改huawei-csi-node.yaml文件。

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >Pod名称的分类，请参考[表1](#table4106151116363)。

    以修改Pod名称为huawei-csi-node中huawei-csi-driver容器的资源请求为例，执行命令编辑配置文件，找到spec.template.spec.containes.name为huawei-csi-driver的容器。按需修改资源请求和限制。

    ```
    vi huawei-csi-node.yaml
    ```

    编辑如下内容。

    ```
    containers
     - name: huawei-csi-driver
       ...
       resources:
         limits:
           cpu: 500m
           memory: 1Gi
         requests:
           cpu: 50m
           memory: 128Mi
    ```

3.  若华为CSI未安装，则参考[Kubernetes、OpenShift、Tanzu安装华为CSI](/v4.5.0/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu)章节安装华为CSI后，资源请求和限制的修改生效。
4.  若已安装华为CSI，则参考[升级华为CSI](/v4.5.0/installation-and-deployment/upgrading-or-rolling-back-huawei-csi/upgrading-or-rolling-back-huawei-csi-using-helm/upgrading-huawei-csi/upgrading-huawei-csi-on-kubernetes-openshift-and-tanzu#section6841317173013)章节更新华为CSI后，资源请求和限制的修改生效。

