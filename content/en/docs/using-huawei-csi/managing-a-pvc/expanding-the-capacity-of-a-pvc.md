---
title: "Expanding the Capacity of a PVC"
linkTitle: "Expanding the Capacity of a PVC"
description: 
weight: 2
---

When the capacity of a PVC used by a container is insufficient, you need to expand the capacity of the PVC.

## Prerequisites{#en-us_topic_0254162571_section07036257166}

-   A PVC has been created, the backend to which it resides exists and supports capacity expansion.
-   For details about the storage devices that support capacity expansion, see  [Features Supported by Huawei Enterprise Storage](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage#section0652122673620)  and  [Features Supported by Huawei Distributed Storage](/docs/compatibility-and-features/compatibility-with-huawei-distributed-storage#section14115311203711). For details about the Kubernetes versions that support capacity expansion, see  [Kubernetes Feature Matrix](/docs/compatibility-and-features/kubernetes-feature-matrix).
-   The csi-resizer service is enabled for huawei-csi-controller.

    ```
    kubectl describe deploy huawei-csi-controller -n huawei-csi | grep csi-resizer
    ```

    If the following information is displayed, the csi-resizer service is enabled.

    ```yaml
       csi-resizer:
        Image:      k8s.gcr.io/sig-storage/csi-resizer:v1.4.0
    ```

## Procedure{#en-us_topic_0254162571_section152212156464}

1.  Run the following command to check whether the StorageClass supports capacity expansion. In the preceding command,  _mysc_  indicates the name of the StorageClass to be queried.

    ```
    kubectl get sc mysc
    ```

    The following is an example of the command output.

    ```
    NAME              PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc              csi.huawei.com   Delete          Immediate           true                  172m
    ```

    If the value of  **ALLOWVOLUMEEXPANSION**  is  **true**, the current StorageClass supports capacity expansion. In this case, go to  [3](#en-us_topic_0254162571_li1143318914115).

2.  Run the following command to change the value of  **allowVolumeExpansion**  to  **true**. In the preceding command,  _mysc_  indicates the name of the StorageClass to be modified.

    ```
    kubectl patch sc mysc --patch '{"allowVolumeExpansion":true}'
    ```

3.  <a name="en-us_topic_0254162571_li1143318914115"></a>Run the following command to query the StorageClass name of the PVC. In the preceding command,  _mypvc_  indicates the name of the PVC to be expanded.

    ```
    kubectl get pvc mypvc
    ```

    The following is an example of the command output.

    ```
    NAME               STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS      AGE
    mypvc              Bound    pvc-3383be36-537c-4cb1-8f32-a415fa6ba384   2Gi        RW0            mysc              145m
    ```

4.  Run the following command to expand the capacity.

    ```
    kubectl patch pvc mypvc -p '{"spec":{"resources":{"requests":{"storage":"120Gi"}}}}'
    ```

    In the preceding command,  _mypvc_  indicates the name of the PVC to be expanded, and  _120Gi_  indicates the capacity after expansion. Change the values based on the site requirements.

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >-   The PVC capacity depends on storage specifications and host specifications. For example, OceanStor Dorado 6.1.2 or OceanStor Pacific series 8.1.0 is connected to CentOS 7. If ext4 file systems are used, see  [Table 2](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning#en-us_topic_0150885187_table178824527142). If XFS file systems are used, see  [Table 3](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning#en-us_topic_0150885187_table101951367104). If NFS or raw devices are used, the capacity must meet the specifications of the used Huawei storage device model and version.
    >-   If the PVC capacity does not meet the specifications, a PVC or Pod may fail to be created due to the limitations of storage specifications or host file system specifications.
    >-   If the capacity expansion fails because the target capacity exceeds the storage pool capacity, see  [Failed to Expand the PVC Capacity Because the Target Capacity Exceeds the Storage Pool Capacity](/docs/troubleshooting/pvc-issues/failed-to-expand-the-pvc-capacity-because-the-target-capacity-exceeds-the-storage-pool-capacity).

5.  Run the following command to check whether the capacity modification takes effect.

    ```
    kubectl get pvc
    ```

    The following is an example of the command output. If the value of  **CAPACITY**  is changed to the specified capacity, the capacity expansion is successful.

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-3383be36-537c-4cb1-8f32-a415fa6ba384   120Gi       RWO            mysc           24s
    ```

