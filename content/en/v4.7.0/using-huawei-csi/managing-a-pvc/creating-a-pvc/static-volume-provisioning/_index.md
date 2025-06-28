---
title: "Static Volume Provisioning"
linkTitle: "Static Volume Provisioning"
description: 
weight: 3
---

Static volume provisioning allows administrators to use a resource created on the storage side as a PV for containers in the cluster.

To implement static volume provisioning, perform the following steps:

-   Configuring a PV
-   Configuring a PVC

## Prerequisites{#section4107171112475}

A storage resource, such as a LUN or file system, required by the PV to be created exists on the storage device. If the storage resource is a file system, you also need to create the share and client information of the file system.

## Configuring a PV{#section1994861643814}

1.  Prepare the PV configuration file  **mypv.yaml**. The following is an example. For details about other parameters, see  [PV Parameters for Static Volume Provisioning](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/static-volume-provisioning/pv-parameters-for-static-volume-provisioning).

    ```yaml
    kind: PersistentVolume
    apiVersion: v1
    metadata:
      name: mypv
    spec:
      volumeMode: Filesystem
      storageClassName: "" # The value must be to "".
      accessModes:
        - ReadWriteOnce
      csi:
        driver: csi.huawei.com # Enter the CSI driver name.
        volumeHandle: iscsi-dorado-181.lun0001 # Enter the volume name.
        fsType: xfs # Set the file system type.
      capacity:
        storage: 100Gi
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >In the configuration file for static volume provisioning,  **storageClassName**  must be set to  **""**. Otherwise, Kubernetes will use the default StorageClass.

2.  Run the following command to create a PV based on the prepared .yaml file.

    ```
    kubectl create -f mypv.yaml
    ```

3.  After a period of time, run the following command to view the information about the created PV.

    ```
    kubectl get pv
    ```

    The following is an example of the command output. If the PV status is  **Available**, the PV is successfully created.

    ```
    NAME       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM               STORAGECLASS   REASON   AGE
    mypv       100Gi      RWO            Retain           Available                                               4s
    ```

## Configuring a PVC{#section166021742104214}

After a PV is created in static volume provisioning mode, you can create a PVC based on the PV for containers.

1.  Prepare the PVC configuration file. The following example is a PVC configuration file for static volume provisioning.

    ```yaml
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: mypvc
    spec:
      storageClassName: ""
      accessModes:
        - ReadWriteOnce
      volumeMode: Filesystem
      resources:
        requests:
          storage: 100Gi
      volumeName: mypv # Enter the name of the corresponding PV.
    ```

2.  Run the following command to create a PVC based on the configured .yaml file.

    ```
    kubectl create -f mypvc.yaml
    ```

3.  After a period of time, run the following command to view the information about the created PVC.

    ```
    kubectl get pvc
    ```

    The following is an example of the command output. If the PVC status is  **Bound**, the PVC is successfully created.

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO                           12s
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >-   After the PVC is created, if the PVC is in the  **Pending**  state after a long time \(for example, one minute\), refer to  [When a PVC Is Created, the PVC Is in the Pending State](/docs/troubleshooting/pvc-issues/when-a-pvc-is-created-the-pvc-is-in-the-pending-state).
    >-   You are advised to create or delete a maximum of 100 PVCs in a batch.

## Using a PVC{#section2949728204519}

The use method is the same as that for dynamic volume provisioning in  [Using a PVC](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning#section8172141413917).



