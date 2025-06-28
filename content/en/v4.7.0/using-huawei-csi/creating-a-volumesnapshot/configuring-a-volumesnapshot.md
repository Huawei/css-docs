---
title: "Configuring a VolumeSnapshot"
linkTitle: "Configuring a VolumeSnapshot"
description: 
weight: 3
---

VolumeSnapshot can be provisioned in two ways: pre-provisioning and dynamic provisioning. Currently, Huawei CSI supports only dynamic provisioning. This section describes how to dynamically provision a VolumeSnapshot using Huawei CSI.

The following is an example of the VolumeSnapshot configuration file:

-   If api-versions in your environment supports v1, use the following example:

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

-   If api-versions in your environment supports v1beta1, use the following example:

    ```yaml
    apiVersion: snapshot.storage.k8s.io/v1beta1
    kind: VolumeSnapshot
    metadata:
      name: mysnapshot
    spec:
      volumeSnapshotClassName: mysnapclass
      source:
        persistentVolumeClaimName: mypvc
    ```

-   The api-versions information in the VolumeSnapshot must be the same as the version used for creating the VolumeSnapshotClass.

You can modify the parameters according to  [Table 1](#en-us_topic_0254162579_table14111735169).

**Table  1**  VolumeSnapshot parameters

<a name="en-us_topic_0254162579_table14111735169"></a>
<table><thead align="left"><tr id="en-us_topic_0254162579_row74136313166"><th class="cellrowborder" valign="top" width="31.75%" id="mcps1.2.4.1.1"><p id="en-us_topic_0254162579_p741313171613"><a name="en-us_topic_0254162579_p741313171613"></a><a name="en-us_topic_0254162579_p741313171613"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.229999999999997%" id="mcps1.2.4.1.2"><p id="en-us_topic_0254162579_p6416123101617"><a name="en-us_topic_0254162579_p6416123101617"></a><a name="en-us_topic_0254162579_p6416123101617"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="42.02%" id="mcps1.2.4.1.3"><p id="en-us_topic_0254162579_p82453211342"><a name="en-us_topic_0254162579_p82453211342"></a><a name="en-us_topic_0254162579_p82453211342"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0254162579_row1328513213318"><td class="cellrowborder" valign="top" width="31.75%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162579_p1428717212036"><a name="en-us_topic_0254162579_p1428717212036"></a><a name="en-us_topic_0254162579_p1428717212036"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.229999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0254162579_p19287172112316"><a name="en-us_topic_0254162579_p19287172112316"></a><a name="en-us_topic_0254162579_p19287172112316"></a>User-defined name of a VolumeSnapshot object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0254162579_p179301591191"><a name="en-us_topic_0254162579_p179301591191"></a><a name="en-us_topic_0254162579_p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0254162579_row94166341618"><td class="cellrowborder" valign="top" width="31.75%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162579_p1241612311619"><a name="en-us_topic_0254162579_p1241612311619"></a><a name="en-us_topic_0254162579_p1241612311619"></a>spec.volumeSnapshotClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26.229999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0254162579_p198887586399"><a name="en-us_topic_0254162579_p198887586399"></a><a name="en-us_topic_0254162579_p198887586399"></a>Name of the VolumeSnapshotClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0254162579_p17304111921116"><a name="en-us_topic_0254162579_p17304111921116"></a><a name="en-us_topic_0254162579_p17304111921116"></a>--</p>
</td>
</tr>
<tr id="en-us_topic_0254162579_row1241623171612"><td class="cellrowborder" valign="top" width="31.75%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0254162579_p11416143151617"><a name="en-us_topic_0254162579_p11416143151617"></a><a name="en-us_topic_0254162579_p11416143151617"></a>spec.source.persistentVolumeClaimName</p>
</td>
<td class="cellrowborder" valign="top" width="26.229999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0254162579_p174161381612"><a name="en-us_topic_0254162579_p174161381612"></a><a name="en-us_topic_0254162579_p174161381612"></a>Name of the source PVC object.</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0254162579_p1324203293410"><a name="en-us_topic_0254162579_p1324203293410"></a><a name="en-us_topic_0254162579_p1324203293410"></a>Name of the source PVC of the snapshot</p>
</td>
</tr>
</tbody>
</table>

## Prerequisites{#section1236201420471}

-   The source PVC exists, and the backend where the PVC resides supports VolumeSnapshot creation. For details about the storage devices that support VolumeSnapshot creation, see  [Table 2](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage#table14995183994515)  and  [Table 2](/docs/compatibility-and-features/compatibility-with-huawei-distributed-storage#table175022559255). For details about the Kubernetes versions that support VolumeSnapshot creation, see  [Table 1](/docs/compatibility-and-features/kubernetes-feature-matrix#table134589135522).
-   The volume snapshot component CRD on which the running of Huawei CSI depends has been installed. For details, see  [Checking Volume Snapshot-Dependent Components](/docs/installation-and-deployment/installation-preparations/checking-volume-snapshot-dependent-components).
-   A VolumeSnapshotClass that uses Huawei CSI exists in the system.

## Procedure{#section1678012285209}

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

