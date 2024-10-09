---
title: "Manage Volume Provisioning"
linkTitle: "Manage Volume Provisioning"
description: 
weight: 2
---

Manage Volume Provisioning allows administrators to use resources created on storage as PVs and supports features of dynamic volumes, such as capacity expansion, snapshot, and clone. This is a custom capability of Huawei CSI. This feature applies to the following scenarios:

-   In the reconstruction containerized applications, existing storage volumes need to be used.
-   The Kubernetes cluster is rebuilt.
-   Storage data is migrated in disaster recovery \(DR\) scenarios.

>![](/css-docs/public_sys-resources/en/icon-note.gif)
>In scenarios where multiple Kubernetes clusters are deployed, when Manage Volume Provisioning is used to manage the same storage resource, management operations performed on the PVC corresponding to the resource in any cluster will not be synchronized to other clusters.
>For example, when you expand the capacity of a PVC in a cluster, the capacity of the corresponding PVC in other clusters will not be automatically expanded. In this case, you need to manually expand the capacity in other clusters by running the expansion commands in  [Expanding the Capacity of a PVC](/docs/using-huawei-csi/managing-a-pvc/expanding-the-capacity-of-a-pvc).

## Prerequisites{#section65071656132313}

-   You have registered the storage where the volume to be managed resides with CSI.
-   You have logged in to the storage device to obtain the name and capacity of the volume to be managed.

## Configuring a StorageClass{#section19289935145}

1.  Create a StorageClass configuration file, for example,  **mysc.yaml**, based on service requirements by referring to  [StorageClass Configuration Examples in Typical Manage Volume Provisioning Scenarios](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/manage-volume-provisioning/storageclass-configuration-examples-in-typical-manage-volume-provisioning-scenarios)  and  [StorageClass Parameters for Manage Volume Provisioning](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/manage-volume-provisioning/storageclass-parameters-for-manage-volume-provisioning).
2.  Run the following command to create a StorageClass using the configuration file.

    ```
    kubectl apply -f mysc.yaml
    ```

3.  Run the following command to view the information about the created StorageClass.

    ```
    kubectl get sc mysc
    ```

    The following is an example of the command output.

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           true                   8s
    ```

## Configuring a PVC{#section1836215261144}

1.  Based on service requirements, modify specific parameters by referring to the description in this section and the PVC configuration file example to generate the PVC configuration file to be created, for example, the  **mypvc.yaml**  file in this example.

    ```yaml
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: mypvc
      annotations:
        csi.huawei.com/manageVolumeName: "*"  # Enter the storage resource name.
        csi.huawei.com/manageBackendName: "*" # Enter the storage backend name.
      labels:
        provisioner: csi.huawei.com
    spec:
      accessModes:
        - ReadWriteOnce
      volumeMode: Filesystem
      storageClassName: mysc
      resources:
        requests:
          storage: 100Gi
    ```

2.  Run the following command to create a PVC using the configuration file.

    ```
    kubectl create -f mypvc.yaml
    ```

3.  After a period of time, run the following command to view the information about the created PVC.

    ```
    kubectl get pvc mypvc
    ```

    The following is an example of the command output. If the PVC status is  **Bound**, the PVC has been created and can be used by a Pod.

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO            mysc           12s
    ```

    >![](/css-docs/public_sys-resources/en/icon-notice.gif) 
    >-   After the PVC is created, if the PVC is in the  **Pending**  state after a long time \(for example, one minute\), refer to  [When a PVC Is Created, the PVC Is in the Pending State](/docs/troubleshooting/pvc-issues/when-a-pvc-is-created-the-pvc-is-in-the-pending-state).
    >-   You are advised to create or delete a maximum of 100 PVCs in a batch.

## Using a PVC{#section847932614377}

The use method is the same as that for dynamic volume provisioning in  [Using a PVC](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning#section8172141413917).




