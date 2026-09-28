---
title: "Configuring a VolumeSnapshotClass"
linkTitle: "Configuring a VolumeSnapshotClass"
description: 
weight: 1
---

## Creating a VolumeSnapshotClass{#en-us_topic_0000002393093844_section1925544124114}

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

You can modify the parameters according to  [Table 1](#en-us_topic_0000002393093844_en-us_topic_0254162578_table189495491346).

**Table  1**  VolumeSnapshotClass parameters

<a name="en-us_topic_0000002393093844_en-us_topic_0254162578_table189495491346"></a>
<table><thead align="left"><tr id="en-us_topic_0000002393093844_en-us_topic_0254162578_row694915491241"><th class="cellrowborder" valign="top" width="17.91%" id="mcps1.2.4.1.1"><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p1094915491049"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p1094915491049"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p1094915491049"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.99%" id="mcps1.2.4.1.2"><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p14949149841"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p14949149841"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p14949149841"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="55.1%" id="mcps1.2.4.1.3"><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p1894916491142"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p1894916491142"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p1894916491142"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000002393093844_en-us_topic_0254162578_row694916498411"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p179494491042"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p179494491042"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p179494491042"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p594918493417"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p594918493417"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p594918493417"></a>User-defined name of a VolumeSnapshotClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p179301591191"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p179301591191"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0000002393093844_en-us_topic_0254162578_row17949349643"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p294913495410"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p294913495410"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p294913495410"></a>driver</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p189491549542"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p189491549542"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p189491549542"></a>driver identifier. This parameter is mandatory.</p>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p119491249043"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p119491249043"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p119491249043"></a>Set this parameter to the driver name set during Huawei CSI installation. The default driver name is <strong id="b160621172945328"><a name="b160621172945328"></a><a name="b160621172945328"></a>csi.huawei.com</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0000002393093844_en-us_topic_0254162578_row19949449547"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000002393093844_en-us_topic_0254162578_p5949749144"><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p5949749144"></a><a name="en-us_topic_0000002393093844_en-us_topic_0254162578_p5949749144"></a>deletionPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000002393093844_p19594192418394"><a name="en-us_topic_0000002393093844_p19594192418394"></a><a name="en-us_topic_0000002393093844_p19594192418394"></a>Snapshot deletion policy. This parameter is mandatory. The value can be:</p>
<a name="en-us_topic_0000002393093844_ul1034113525514"></a><a name="en-us_topic_0000002393093844_ul1034113525514"></a><ul id="en-us_topic_0000002393093844_ul1034113525514"><li>Delete</li><li>Retain</li></ul>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><a name="en-us_topic_0000002393093844_ul925601066"></a><a name="en-us_topic_0000002393093844_ul925601066"></a><ul id="en-us_topic_0000002393093844_ul925601066"><li>If the deletion policy is <strong id="b1167266036"><a name="b1167266036"></a><a name="b1167266036"></a>Delete</strong>, the snapshot on the storage device will be deleted together with the VolumeSnapshotContent object.</li><li>If the deletion policy is <strong id="b67381673145328"><a name="b67381673145328"></a><a name="b67381673145328"></a>Retain</strong>, the snapshot and VolumeSnapshotContent object on the storage device will be retained.</li></ul>
</td>
</tr>
<tr id="en-us_topic_0000002393093844_row123551713017"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000002393093844_p586014583516"><a name="en-us_topic_0000002393093844_p586014583516"></a><a name="en-us_topic_0000002393093844_p586014583516"></a>parameters.enableHyperMetroSnap</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000002393093844_p158602581659"><a name="en-us_topic_0000002393093844_p158602581659"></a><a name="en-us_topic_0000002393093844_p158602581659"></a>Whether to create SAN HyperMetro snapshots on both ends.</p>
<a name="en-us_topic_0000002393093844_ul1952015398716"></a><a name="en-us_topic_0000002393093844_ul1952015398716"></a><ul id="en-us_topic_0000002393093844_ul1952015398716"><li><strong id="b28403499245328"><a name="b28403499245328"></a><a name="b28403499245328"></a>"true"</strong>: Create snapshots on the two storage systems that form the HyperMetro pair.</li><li><strong id="b1451974745328"><a name="b1451974745328"></a><a name="b1451974745328"></a>"false"</strong>: Create a snapshot on the storage system associated with the current storage class.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000002393093844_p486075816514"><a name="en-us_topic_0000002393093844_p486075816514"></a><a name="en-us_topic_0000002393093844_p486075816514"></a>The default value is <strong id="b180216932645328"><a name="b180216932645328"></a><a name="b180216932645328"></a>"false"</strong>.</p>
<p id="en-us_topic_0000002393093844_p1586018581150"><a name="en-us_topic_0000002393093844_p1586018581150"></a><a name="en-us_topic_0000002393093844_p1586018581150"></a>When the backend type is oceanstor-san and the storage version is V700R001C10 or later, this parameter can be set to <strong id="b87225595845328"><a name="b87225595845328"></a><a name="b87225595845328"></a>"true"</strong>.</p>
</td>
</tr>
</tbody>
</table>

## Procedure{#en-us_topic_0000002393093844_section133215312424}

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

