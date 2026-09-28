---
title: "Pre-provisioning a VolumeSnapshot"
linkTitle: "Pre-provisioning a VolumeSnapshot"
description: 
weight: 2
---

This section describes how to pre-provision a VolumeSnapshot using Huawei CSI.

## Prerequisites{#section12590411394}

-   A source VolumeSnapshot has been created on the Huawei storage device, and the created snapshot name can be obtained.

## Creating a VolumeSnapshot Entity{#en-us_topic_0000002393093844_section1925544124114}

The following is an example of the VolumeSnapshotContent file:

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

You can modify the parameters according to  [Table 1](#table8786153415557).

**Table  1**  VolumeSnapshotContent parameters

<a name="table8786153415557"></a>
<table><thead align="left"><tr id="row1378753416551"><th class="cellrowborder" valign="top" width="19.63%" id="mcps1.2.4.1.1"><p id="p197871344553"><a name="p197871344553"></a><a name="p197871344553"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="25.8%" id="mcps1.2.4.1.2"><p id="p1878773495515"><a name="p1878773495515"></a><a name="p1878773495515"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="54.56999999999999%" id="mcps1.2.4.1.3"><p id="p5787123414551"><a name="p5787123414551"></a><a name="p5787123414551"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row6787163475512"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p20787163415552"><a name="p20787163415552"></a><a name="p20787163415552"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p207877342558"><a name="p207877342558"></a><a name="p207877342558"></a>User-defined name of a VolumeSnapshotContent object.</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p14787434135514"><a name="p14787434135514"></a><a name="p14787434135514"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="row37871534105518"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p1678719349551"><a name="p1678719349551"></a><a name="p1678719349551"></a>spec.deletionPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p13787163417557"><a name="p13787163417557"></a><a name="p13787163417557"></a>Deletion policy. The following types are supported:</p>
<a name="ul79405438329"></a><a name="ul79405438329"></a><ul id="ul79405438329"><li><strong id="b151462645845435"><a name="b151462645845435"></a><a name="b151462645845435"></a>Delete</strong>: Resources are automatically reclaimed.</li><li><strong id="b31991833145435"><a name="b31991833145435"></a><a name="b31991833145435"></a>Retain</strong>: Resources are manually reclaimed.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><a name="ul35990286363"></a><a name="ul35990286363"></a><ul id="ul35990286363"><li><strong id="b87601118193316"><a name="b87601118193316"></a><a name="b87601118193316"></a>Delete</strong>: When a VolumeSnapshotContent is deleted, the snapshot resources on the storage are also deleted.</li><li><strong id="b356912012334"><a name="b356912012334"></a><a name="b356912012334"></a>Retain</strong>: When a VolumeSnapshotContent is deleted, the snapshot resources on the storage are not deleted.</li></ul>
</td>
</tr>
<tr id="row4787103410555"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p678753419556"><a name="p678753419556"></a><a name="p678753419556"></a>spec.driver</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p57879345557"><a name="p57879345557"></a><a name="p57879345557"></a>Driver name.</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p95861308387"><a name="p95861308387"></a><a name="p95861308387"></a>Set this parameter to the driver name set during Huawei CSI installation.</p>
<p id="p1358612083815"><a name="p1358612083815"></a><a name="p1358612083815"></a>The value is the same as that of <strong id="b85542044645435"><a name="b85542044645435"></a><a name="b85542044645435"></a>driverName</strong> in the <strong id="b74152627745435"><a name="b74152627745435"></a><a name="b74152627745435"></a>values.yaml</strong> file.</p>
</td>
</tr>
<tr id="row19261848113817"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p426148133819"><a name="p426148133819"></a><a name="p426148133819"></a>spec.volumeSnapshotRef</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p62684810382"><a name="p62684810382"></a><a name="p62684810382"></a>Information about the target VolumeSnapshot to be bound, including the VolumeSnapshot name and namespace.</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p1261448163816"><a name="p1261448163816"></a><a name="p1261448163816"></a>--</p>
</td>
</tr>
<tr id="row14266115793916"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p926718577393"><a name="p926718577393"></a><a name="p926718577393"></a>spec.source.snapshotHandle</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p6900439124013"><a name="p6900439124013"></a><a name="p6900439124013"></a>Unique identifier of a storage snapshot resource. This parameter is mandatory.</p>
<p id="p3900139184019"><a name="p3900139184019"></a><a name="p3900139184019"></a>The format is <em id="i72035013344"><a name="i72035013344"></a><a name="i72035013344"></a>&lt;backend-name&gt;</em><strong id="b232414243516"><a name="b232414243516"></a><a name="b232414243516"></a>.</strong><em id="i16883105312344"><a name="i16883105312344"></a><a name="i16883105312344"></a>&lt;parent-id&gt;</em><strong id="b37691709352"><a name="b37691709352"></a><a name="b37691709352"></a>.</strong><em id="i17119155763411"><a name="i17119155763411"></a><a name="i17119155763411"></a>&lt;snapshot-name&gt;</em>.</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p186954484407"><a name="p186954484407"></a><a name="p186954484407"></a>The value of this parameter consists of the following parts:</p>
<a name="ul46951348124017"></a><a name="ul46951348124017"></a><ul id="ul46951348124017"><li><strong id="b1818913914354"><a name="b1818913914354"></a><a name="b1818913914354"></a>&lt;backend-name&gt;</strong>: indicates the backend name corresponding to the snapshot resource. You can run the <strong id="b13211325193519"><a name="b13211325193519"></a><a name="b13211325193519"></a>oceanctl get backend</strong> command to obtain the configured backend information.</li><li><strong id="b1178331073515"><a name="b1178331073515"></a><a name="b1178331073515"></a>&lt;parent-id&gt;</strong>: indicates the ID of the parent resource object of the snapshot resource on the storage device. You can view the ID on DeviceManager.</li><li><strong id="b13270101311356"><a name="b13270101311356"></a><a name="b13270101311356"></a>&lt;snapshot-name&gt;</strong>: indicates the name of the snapshot resource on the storage device. You can view the name on DeviceManager.</li></ul>
</td>
</tr>
<tr id="row17349349444"><td class="cellrowborder" valign="top" width="19.63%" headers="mcps1.2.4.1.1 "><p id="p1535113412442"><a name="p1535113412442"></a><a name="p1535113412442"></a>spec.volumeSnapshotClassName</p>
</td>
<td class="cellrowborder" valign="top" width="25.8%" headers="mcps1.2.4.1.2 "><p id="p6587115224412"><a name="p6587115224412"></a><a name="p6587115224412"></a>Name of the VolumeSnapshotClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="54.56999999999999%" headers="mcps1.2.4.1.3 "><p id="p153514345441"><a name="p153514345441"></a><a name="p153514345441"></a>--</p>
</td>
</tr>
</tbody>
</table>

1.  Run the following command to create a VolumeSnapshotContent using the created VolumeSnapshotContent configuration file.

    ```
    kubectl create -f mysnapshotcontent.yaml
    ```

2.  Run the following command to view the information about the created VolumeSnapshot.

    ```
    kubectl get volumesnapshotcontent
    ```

    The following is an example of the command output.

    ```
    NAME               READYTOUSE   RESTORESIZE   DELETIONPOLICY   DRIVER           VOLUMESNAPSHOTCLASS   VOLUMESNAPSHOT   VOLUMESNAPSHOTNAMESPACE   AGE
    mysnapshotcontent  true         0             Retain           csi.huawei.com   mysnapclass           mysnapshot       default                   4s
    ```

## Creating a Snapshot for a Volume{#en-us_topic_0000002393093844_section11071242458}

After a VolumeSnapshotContent is created in provisioned mode, you can create a VolumeSnapshot based on the VolumeSnapshotContent. The following is an example of the VolumeSnapshot configuration file:

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

You can modify the parameters according to  [Table 2](#en-us_topic_0000002393093844_en-us_topic_0254162579_table14111735169).

**Table  2**  VolumeSnapshot parameters

<a name="en-us_topic_0000002393093844_en-us_topic_0254162579_table14111735169"></a>
<table><thead align="left"><tr id="en-us_topic_0000002393093844_en-us_topic_0254162579_row74136313166"><th class="cellrowborder" valign="top" width="31.5%" id="mcps1.2.4.1.1"><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p741313171613"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p741313171613"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p741313171613"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.479999999999997%" id="mcps1.2.4.1.2"><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p6416123101617"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p6416123101617"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p6416123101617"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="42.02%" id="mcps1.2.4.1.3"><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p82453211342"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p82453211342"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p82453211342"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000002393093844_en-us_topic_0254162579_row1328513213318"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p1428717212036"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p1428717212036"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p1428717212036"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p19287172112316"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p19287172112316"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p19287172112316"></a>User-defined name of a VolumeSnapshot object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p179301591191"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p179301591191"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
<p id="p13223147173617"><a name="p13223147173617"></a><a name="p13223147173617"></a>The value must be the same as the name of the VolumeSnapshot specified by VolumeSnapshotContent.</p>
</td>
</tr>
<tr id="row763382633415"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="p12634142619345"><a name="p12634142619345"></a><a name="p12634142619345"></a>metadata.namespace</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="p11634826133419"><a name="p11634826133419"></a><a name="p11634826133419"></a>Namespace to which the VolumeSnapshot belongs.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="p563492633412"><a name="p563492633412"></a><a name="p563492633412"></a>The value must be the same as the namespace of the VolumeSnapshot specified by VolumeSnapshotContent.</p>
</td>
</tr>
<tr id="en-us_topic_0000002393093844_en-us_topic_0254162579_row94166341618"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p1241612311619"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p1241612311619"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p1241612311619"></a>spec.volumeSnapshotClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p198887586399"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p198887586399"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p198887586399"></a>Name of the VolumeSnapshotClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p17304111921116"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p17304111921116"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p17304111921116"></a>--</p>
</td>
</tr>
<tr id="en-us_topic_0000002393093844_en-us_topic_0254162579_row1241623171612"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p11416143151617"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p11416143151617"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p11416143151617"></a>spec.source.volumeSnapshotContentName</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p174161381612"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p174161381612"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p174161381612"></a>Name of the source VolumeSnapshotContent object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162579_p1324203293410"><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p1324203293410"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162579_p1324203293410"></a>Name of the source VolumeSnapshotContent of the snapshot.</p>
</td>
</tr>
</tbody>
</table>

1.  Run the following command to create a VolumeSnapshot using the created VolumeSnapshot configuration file.

    ```
    kubectl create -f mysnapshot.yaml
    ```

2.  Run the following command to view the information about the created VolumeSnapshot.

    ```
    kubectl get volumesnapshot
    ```

    The following is an example of the command output.

    ```
    NAME         READYTOUSE  SOURCEPVC  SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS   SNAPSHOTCONTENT     CREATIONTIME   AGE
    mysnapshot   true                   mysnapshotcontent       0             mysnapclass     mysnapshotcontent   2m39s          8s
    ```

