---
title: "Configuring a VolumeSnapshotClass"
linkTitle: "Configuring a VolumeSnapshotClass"
description: 
weight: 2
---

[VolumeSnapshotClass](https://kubernetes.io/docs/concepts/storage/volume-snapshot-classes/)  provides a way to describe the "classes" of storage when provisioning a VolumeSnapshot. Each VolumeSnapshotClass contains the  **driver**,  **deletionPolicy**, and  **parameters**  fields, which are used when a VolumeSnapshot belonging to the class needs to be dynamically provisioned.

The name of a VolumeSnapshotClass object is significant, and is how users can request a particular class. Administrators set the name and other parameters of a class when first creating VolumeSnapshotClass objects, and the objects cannot be updated once they are created.

The following is an example of a VolumeSnapshotClass used by Huawei CSI:

-   If api-versions in your environment supports v1, use the following example:

    ```yaml
    apiVersion: snapshot.storage.k8s.io/v1
    kind: VolumeSnapshotClass
    metadata:
      name: mysnapclass
    driver: csi.huawei.com
    deletionPolicy: Delete
    ```

-   If api-versions in your environment supports v1beta1, use the following example:

    ```yaml
    apiVersion: snapshot.storage.k8s.io/v1beta1
    kind: VolumeSnapshotClass
    metadata:
      name: mysnapclass
    driver: csi.huawei.com
    deletionPolicy: Delete
    ```

-   If api-versions in your environment supports both v1 and v1beta1, v1 is recommended.

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
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><a name="ul925601066"></a><a name="ul925601066"></a><ul id="ul925601066"><li>If the deletion policy is <strong id="b35361518194816"><a name="b35361518194816"></a><a name="b35361518194816"></a>Delete</strong>, the snapshot on the storage device will be deleted together with the VolumeSnapshotContent object.</li><li>If the deletion policy is <strong id="b1013813510484"><a name="b1013813510484"></a><a name="b1013813510484"></a>Retain</strong>, the snapshot and VolumeSnapshotContent object on the storage device will be retained.</li></ul>
</td>
</tr>
</tbody>
</table>

## Prerequisites{#section549623219322}

Huawei CSI supports snapshots, and the volume snapshot component CRD on which its running depends has been installed. For details about the CRD, see  [Checking Volume Snapshot-Dependent Components](/docs/installation-and-deployment/installation-preparations/checking-volume-snapshot-dependent-components). For details about the Kubernetes versions that support VolumeSnapshot creation, see  [Table 1](/docs/compatibility-and-features/kubernetes-feature-matrix#table134589135522).

## Procedure{#section187667882011}

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

