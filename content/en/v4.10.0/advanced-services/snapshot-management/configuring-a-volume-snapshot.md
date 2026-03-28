---
title: "Configuring a Volume Snapshot"
linkTitle: "Configuring a Volume Snapshot"
description: 
weight: 1
---

## Creating a Volume Snapshot Class{#section1925544124114}

[VolumeSnapshotClass](https://kubernetes.io/docs/concepts/storage/volume-snapshot-classes/)  provides a way to describe the "classes" of storage when provisioning a VolumeSnapshot. Each VolumeSnapshotClass contains the  **driver**,  **deletionPolicy**, and  **parameters**  fields, which are used when a VolumeSnapshot belonging to the class needs to be dynamically provisioned.

The name of a VolumeSnapshotClass object is significant, and is how users can request a particular class. Administrators set the name and other parameters of a class when first creating VolumeSnapshotClass objects, and the objects cannot be updated once they are created.

The following is an example of a VolumeSnapshotClass used by Huawei CSI:

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshotClass
metadata:
  name: mysnapclass
driver: csi.huawei.com
deletionPolicy: Delete
```

You can modify the parameters according to  [Table 1](#en-us_topic_0254162578_table189495491346). Currently, Huawei CSI does not support user-defined parameters \(**parameters**\) in a VolumeSnapshotClass. Therefore, you are advised to create a VolumeSnapshotClass for all snapshots.

**Table  1**  VolumeSnapshotClass parameters

<a name="en-us_topic_0254162578_table189495491346"></a>
<table><thead align="left"><tr id="en-us_topic_0254162578_row694915491241"><th class="cellrowborder" valign="top" width="17.91%" id="mcps1.2.4.1.1"><p id="en-us_topic_0254162578_p1094915491049"><a name="en-us_topic_0254162578_p1094915491049"></a><a name="en-us_topic_0254162578_p1094915491049"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.99%" id="mcps1.2.4.1.2"><p id="en-us_topic_0254162578_p14949149841"><a name="en-us_topic_0254162578_p14949149841"></a><a name="en-us_topic_0254162578_p14949149841"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="55.1%" id="mcps1.2.4.1.3"><p id="en-us_topic_0254162578_p1894916491142"><a name="en-us_topic_0254162578_p1894916491142"></a><a name="en-us_topic_0254162578_p1894916491142"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0254162578_row694916498411"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162578_p179494491042"><a name="en-us_topic_0254162578_p179494491042"></a><a name="en-us_topic_0254162578_p179494491042"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0254162578_p594918493417"><a name="en-us_topic_0254162578_p594918493417"></a><a name="en-us_topic_0254162578_p594918493417"></a>User-defined name of a VolumeSnapshotClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0254162578_p179301591191"><a name="en-us_topic_0254162578_p179301591191"></a><a name="en-us_topic_0254162578_p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0254162578_row17949349643"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162578_p294913495410"><a name="en-us_topic_0254162578_p294913495410"></a><a name="en-us_topic_0254162578_p294913495410"></a>driver</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0254162578_p189491549542"><a name="en-us_topic_0254162578_p189491549542"></a><a name="en-us_topic_0254162578_p189491549542"></a>driver identifier. This parameter is mandatory.</p>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0254162578_p119491249043"><a name="en-us_topic_0254162578_p119491249043"></a><a name="en-us_topic_0254162578_p119491249043"></a>Set this parameter to the driver name set during Huawei CSI installation. The default driver name is <strong id="b1877316566470"><a name="b1877316566470"></a><a name="b1877316566470"></a>csi.huawei.com</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0254162578_row19949449547"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162578_p5949749144"><a name="en-us_topic_0254162578_p5949749144"></a><a name="en-us_topic_0254162578_p5949749144"></a>deletionPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="p19594192418394"><a name="p19594192418394"></a><a name="p19594192418394"></a>Snapshot deletion policy. This parameter is mandatory. The value can be:</p>
<a name="ul1034113525514"></a><a name="ul1034113525514"></a><ul id="ul1034113525514"><li>Delete</li><li>Retain</li></ul>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><a name="ul925601066"></a><a name="ul925601066"></a><ul id="ul925601066"><li>If the deletion policy is <strong id="b1091982014164"><a name="b1091982014164"></a><a name="b1091982014164"></a>Delete</strong>, the snapshot on the storage device will be deleted together with the VolumeSnapshotContent object.</li><li>If the deletion policy is <strong id="b1013813510484"><a name="b1013813510484"></a><a name="b1013813510484"></a>Retain</strong>, the snapshot and VolumeSnapshotContent object on the storage device will be retained.</li></ul>
</td>
</tr>
</tbody>
</table>

## Procedure{#section133215312424}

1.  Run the following command to create a VolumeSnapshotClass using the created VolumeSnapshotClass configuration file.

    ```
    kubectl create -f mysnapclass.yaml
    ```

2.  Run the following command to view the information about the created VolumeSnapshotClass.

    ```
    kubectl get volumesnapshotclass
    ```

    The following is an example of the command output.

    ```
    NAME          DRIVER           DELETIONPOLICY   AGE
    mysnapclass   csi.huawei.com   Delete           25s
    ```

## Creating a Snapshot for a Volume{#section11071242458}

VolumeSnapshot can be provisioned in two ways:  [pre-provisioning and dynamic provisioning](https://kubernetes.io/docs/concepts/storage/volume-snapshots/). Currently, Huawei CSI supports only dynamic provisioning. This section describes how to dynamically provision a VolumeSnapshot using Huawei CSI. The following is an example of the VolumeSnapshot configuration file:

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshot
metadata:
  name: mysnapshot
spec:
  volumeSnapshotClassName: mysnapclass
  source:
    persistentVolumeClaimName: mypvc
```

You can modify the parameters according to  [Table 2](#en-us_topic_0254162579_table14111735169).

**Table  2**  VolumeSnapshot parameters

<a name="en-us_topic_0254162579_table14111735169"></a>
<table><thead align="left"><tr id="en-us_topic_0254162579_row74136313166"><th class="cellrowborder" valign="top" width="31.5%" id="mcps1.2.4.1.1"><p id="en-us_topic_0254162579_p741313171613"><a name="en-us_topic_0254162579_p741313171613"></a><a name="en-us_topic_0254162579_p741313171613"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.479999999999997%" id="mcps1.2.4.1.2"><p id="en-us_topic_0254162579_p6416123101617"><a name="en-us_topic_0254162579_p6416123101617"></a><a name="en-us_topic_0254162579_p6416123101617"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="42.02%" id="mcps1.2.4.1.3"><p id="en-us_topic_0254162579_p82453211342"><a name="en-us_topic_0254162579_p82453211342"></a><a name="en-us_topic_0254162579_p82453211342"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0254162579_row1328513213318"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162579_p1428717212036"><a name="en-us_topic_0254162579_p1428717212036"></a><a name="en-us_topic_0254162579_p1428717212036"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0254162579_p19287172112316"><a name="en-us_topic_0254162579_p19287172112316"></a><a name="en-us_topic_0254162579_p19287172112316"></a>User-defined name of a VolumeSnapshot object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0254162579_p179301591191"><a name="en-us_topic_0254162579_p179301591191"></a><a name="en-us_topic_0254162579_p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0254162579_row94166341618"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162579_p1241612311619"><a name="en-us_topic_0254162579_p1241612311619"></a><a name="en-us_topic_0254162579_p1241612311619"></a>spec.volumeSnapshotClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0254162579_p198887586399"><a name="en-us_topic_0254162579_p198887586399"></a><a name="en-us_topic_0254162579_p198887586399"></a>Name of the VolumeSnapshotClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0254162579_p17304111921116"><a name="en-us_topic_0254162579_p17304111921116"></a><a name="en-us_topic_0254162579_p17304111921116"></a>--</p>
</td>
</tr>
<tr id="en-us_topic_0254162579_row1241623171612"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162579_p11416143151617"><a name="en-us_topic_0254162579_p11416143151617"></a><a name="en-us_topic_0254162579_p11416143151617"></a>spec.source.persistentVolumeClaimName</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0254162579_p174161381612"><a name="en-us_topic_0254162579_p174161381612"></a><a name="en-us_topic_0254162579_p174161381612"></a>Name of the source PVC object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0254162579_p1324203293410"><a name="en-us_topic_0254162579_p1324203293410"></a><a name="en-us_topic_0254162579_p1324203293410"></a>Name of the source PVC of the snapshot</p>
</td>
</tr>
</tbody>
</table>

## Procedure{#section17556404720}

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
    NAME         READYTOUSE   SOURCEPVC   SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS   SNAPSHOTCONTENT                                    CREATIONTIME   AGE
    mysnapshot   true         mypvc                               100Gi         mysnapclass     snapcontent-1009af0a-24c2-4435-861c-516224503f2d   <invalid>      78s
    ```

