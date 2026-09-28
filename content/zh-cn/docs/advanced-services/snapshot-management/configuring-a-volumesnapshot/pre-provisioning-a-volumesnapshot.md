---
title: "预制备卷快照"
linkTitle: "预制备卷快照"
description: 
weight: 2
---

本章节将说明如何使用华为CSI预制备卷快照。

## 前提条件{#section12590411394}

-   已在华为存储设备上创建源卷快照，并能够获取到创建的快照名称。

## 创建卷快照实体{#zh-cn_topic_0000002393093844_section1925544124114}

VolumeSnapshotContent的配置文件示例如下：

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshotContent
metadata:
  name: mysnapshotcontent
spec:
  deletionPolicy: Retain
  driver: csi.huawei.com
  volumeSnapshotRef:
    apiVersion: snapshot.storage.k8s.io/v1
    kind: VolumeSnapshot
    name: mysnapshot
    namespace: default
  source:
    snapshotHandle: mybackend.1.snapshot_001
  volumeSnapshotClassName: "mysnapclass"
```

实际参数可以参考[表1](#table8786153415557)中的说明修改。

**表 1**  VolumeSnapshotContent参数说明

<a name="table8786153415557"></a>
<table><thead align="left"><tr id="row1378753416551"><th class="cellrowborder" valign="top" width="19.63%" id="mcps1.2.4.1.1"><p id="p197871344553"><a name="p197871344553"></a><a name="p197871344553"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="25.8%" id="mcps1.2.4.1.2"><p id="p1878773495515"><a name="p1878773495515"></a><a name="p1878773495515"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="54.56999999999999%" id="mcps1.2.4.1.3"><p id="p5787123414551"><a name="p5787123414551"></a><a name="p5787123414551"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row6787163475512"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p20787163415552"><a name="p20787163415552"></a><a name="p20787163415552"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p207877342558"><a name="p207877342558"></a><a name="p207877342558"></a>自定义的<span>VolumeSnapshotContent</span>对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p14787434135514"><a name="p14787434135514"></a><a name="p14787434135514"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字字符开头和结尾。</p>
</td>
</tr>
<tr id="row37871534105518"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p1678719349551"><a name="p1678719349551"></a><a name="p1678719349551"></a>spec.deletionPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p13787163417557"><a name="p13787163417557"></a><a name="p13787163417557"></a>删除策略。支持如下类型：</p>
<a name="ul79405438329"></a><a name="ul79405438329"></a><ul id="ul79405438329"><li>Delete：自动回收资源。</li><li>Retain：手动回收资源。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><a name="ul35990286363"></a><a name="ul35990286363"></a><ul id="ul35990286363"><li>Delete：删除<span>VolumeSnapshotContent</span>时会关联删除存储上的快照资源。</li><li>Retain：删除<span>VolumeSnapshotContent</span>时不会删除存储上的快照资源。</li></ul>
</td>
</tr>
<tr id="row4787103410555"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p678753419556"><a name="p678753419556"></a><a name="p678753419556"></a>spec.driver</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p57879345557"><a name="p57879345557"></a><a name="p57879345557"></a>驱动名称。</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p95861308387"><a name="p95861308387"></a><a name="p95861308387"></a>该字段需要指定为安装华为CSI时设置的驱动名称。</p>
<p id="p1358612083815"><a name="p1358612083815"></a><a name="p1358612083815"></a>取值和values.yaml文件中driverName一致。</p>
</td>
</tr>
<tr id="row19261848113817"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p426148133819"><a name="p426148133819"></a><a name="p426148133819"></a>spec.volumeSnapshotRef</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p62684810382"><a name="p62684810382"></a><a name="p62684810382"></a>需要绑定的目标VolumeSnapshot信息，包含VolumeSnapshot名称以及所属命名空间。</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p1261448163816"><a name="p1261448163816"></a><a name="p1261448163816"></a>--</p>
</td>
</tr>
<tr id="row14266115793916"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p926718577393"><a name="p926718577393"></a><a name="p926718577393"></a>spec.source.snapshotHandle</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p6900439124013"><a name="p6900439124013"></a><a name="p6900439124013"></a>存储快照资源的唯一标志。必选参数。</p>
<p id="p3900139184019"><a name="p3900139184019"></a><a name="p3900139184019"></a>格式为：&lt;backend-name&gt;.&lt;parent-id&gt;.&lt;snapshot-name&gt;</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p186954484407"><a name="p186954484407"></a><a name="p186954484407"></a>该参数值由以下三部分构成：</p>
<a name="ul46951348124017"></a><a name="ul46951348124017"></a><ul id="ul46951348124017"><li>&lt;backend-name&gt;：该快照资源对应的后端名称，可使用如下命令获取配置的后端信息：oceanctl get backend</li><li>&lt;parent-id&gt;：存储上快照资源的父资源对象ID，可通过DeviceManager查看。</li><li>&lt;snapshot-name&gt;：存储上快照资源的名称，可通过DeviceManager查看。</li></ul>
</td>
</tr>
<tr id="row17349349444"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p1535113412442"><a name="p1535113412442"></a><a name="p1535113412442"></a>spec.volumeSnapshotClassName</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p6587115224412"><a name="p6587115224412"></a><a name="p6587115224412"></a>VolumeSnapshotClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p153514345441"><a name="p153514345441"></a><a name="p153514345441"></a>--</p>
</td>
</tr>
</tbody>
</table>

1.  执行以下命令，使用已经创建的VolumeSnapshotContent配置文件创建VolumeSnapshotContent。

    ```
    kubectl create -f mysnapshotcontent.yaml
    ```

2.  执行以下命令，查看已创建的VolumeSnapshot信息。

    ```
    kubectl get volumesnapshotcontent
    ```

    命令结果示例如下：

    ```
    NAME               READYTOUSE   RESTORESIZE   DELETIONPOLICY   DRIVER           VOLUMESNAPSHOTCLASS   VOLUMESNAPSHOT   VOLUMESNAPSHOTNAMESPACE   AGE
    mysnapshotcontent  true         0             Retain           csi.huawei.com   mysnapclass           mysnapshot       default                   4s
    ```

## 创建卷快照{#zh-cn_topic_0000002393093844_section11071242458}

当VolumeSnapshotContent以预制备方式创建完成后，可以基于该VolumeSnapshotContent创建VolumeSnapshot。VolumeSnapshot的配置文件示例如下：

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshot
metadata:
  name: mysnapshot
  namespace: default
spec:
  volumeSnapshotClassName: mysnapclass
  source:
    volumeSnapshotContentName: mysnapshotcontent
```

实际参数可以参考[表2](#zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_table14111735169)中的说明修改。

**表 2**  VolumeSnapshot参数说明

<a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_table14111735169"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_row74136313166"><th class="cellrowborder" valign="top" width="31.5%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p741313171613"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p741313171613"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p741313171613"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="26.479999999999997%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p6416123101617"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p6416123101617"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p6416123101617"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="42.02%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p82453211342"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p82453211342"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p82453211342"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_row1328513213318"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1428717212036"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1428717212036"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1428717212036"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p19287172112316"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p19287172112316"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p19287172112316"></a>自定义的<span>VolumeSnapshot</span>对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p179301591191"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p179301591191"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p179301591191"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字字符开头和结尾。</p>
<p id="p13223147173617"><a name="p13223147173617"></a><a name="p13223147173617"></a>与<span>VolumeSnapshotContent</span>指定的<span>VolumeSnapshot名称保持一致。</span></p>
</td>
</tr>
<tr id="row763382633415"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="p12634142619345"><a name="p12634142619345"></a><a name="p12634142619345"></a>metadata.namespace</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="p11634826133419"><a name="p11634826133419"></a><a name="p11634826133419"></a>VolumeSnapshot所属命名空间。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="p563492633412"><a name="p563492633412"></a><a name="p563492633412"></a>与<span>VolumeSnapshotContent</span>指定的<span>VolumeSnapshot命名空间保持一致。</span></p>
</td>
</tr>
<tr id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_row94166341618"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1241612311619"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1241612311619"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1241612311619"></a>spec.volumeSnapshotClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p198887586399"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p198887586399"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p198887586399"></a>VolumeSnapshotClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p17304111921116"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p17304111921116"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p17304111921116"></a>--</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_row1241623171612"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p11416143151617"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p11416143151617"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p11416143151617"></a>spec.source.volumeSnapshotContentName</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p174161381612"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p174161381612"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p174161381612"></a>源<span>VolumeSnapshotContent</span>对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1324203293410"><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1324203293410"></a><a name="zh-cn_topic_0000002393093844_zh-cn_topic_0254162579_p1324203293410"></a>快照源<span>VolumeSnapshotContent</span>对应的名称</p>
</td>
</tr>
</tbody>
</table>

1.  执行以下命令，使用已经创建的VolumeSnapshot配置文件创建VolumeSnapshot。

    ```
    kubectl create -f mysnapshot.yaml
    ```

2.  执行以下命令，查看已创建的VolumeSnapshot信息。

    ```
    kubectl get volumesnapshot
    ```

    命令结果示例如下：

    ```
    NAME         READYTOUSE  SOURCEPVC  SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS   SNAPSHOTCONTENT     CREATIONTIME   AGE
    mysnapshot   true                   mysnapshotcontent       0             mysnapclass     mysnapshotcontent   2m39s          8s
    ```

