---
title: "Deleting a VolumeSnapshot"
linkTitle: "Deleting a VolumeSnapshot"
description: 
weight: 3
---

## Deleting a VolumeSnapshot{#section17253353163115}

Perform this operation when the volume snapshot is no longer required.

## Procedure{#section1976104203312}

1.  Run the following command to view the information about the created VolumeSnapshot.

    ```
    kubectl get volumesnapshot
    ```

    The following is an example of the command output.

    ```
    NAME         READYTOUSE   SOURCEPVC   SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS   SNAPSHOTCONTENT                                    CREATIONTIME   AGE
    mysnapshot   true         mypvc                               100Gi         mysnapclass     snapcontent-1009af0a-24c2-4435-861c-516224503f2d   <invalid>      78s
    ```

2.  Run the following command to delete the VolumeSnapshot:

    ```
    kubectl delete volumesnapshot mysnapshot 
    ```

    If the following information is displayed, the deletion is successful:

    ```
    volumesnapshot.snapshot.storage.k8s.io "mysnapshot" deleted
    ```

## Deleting a VolumeSnapshotClass{#section12459185133213}

Perform this operation when the VolumeSnapshotClass is not bound to any VolumeSnapshot and the VolumeSnapshotClass is no longer required.

## Procedure{#section4278153218329}

1.  Run the following command to view the VolumeSnapshotClass:

    ```
    kubectl get vsclass
    ```

    The following is an example of the command output.

    ```
    NAME          DRIVER           DELETIONPOLICY   AGE
    mysnapclass   csi.huawei.com   Delete           25s
    ```

2.  Run the following command to delete the StorageClass:

    ```
    kubectl delete vsclass mysnapclass
    ```

    If the following information is displayed, the deletion is successful:

    ```
    volumesnapshotclass.snapshot.storage.k8s.io "mysnapclass" deleted
    ```

