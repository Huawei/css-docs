---
title: "Querying a VolumeSnapshot"
linkTitle: "Querying a VolumeSnapshot"
description: 
weight: 1
---

## Viewing a VolumeSnapshotClass{#section1116853914280}

1.  Run the following command to view the information about the created VolumeSnapshotClass.

    ```
    kubectl get volumesnapshotclass
    ```

    The following is an example of the command output.

    ```
    NAME          DRIVER           DELETIONPOLICY   AGE
    mysnapclass   csi.huawei.com   Delete           25s
    ```

## Querying a Volume Snapshot{#section5247123019291}

1.  Run the following command to view the information about the created VolumeSnapshot.

    ```
    kubectl get volumesnapshot
    ```

    The following is an example of the command output.

    ```
    NAME         READYTOUSE   SOURCEPVC   SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS   SNAPSHOTCONTENT                                    CREATIONTIME   AGE
    mysnapshot   true         mypvc                               100Gi         mysnapclass     snapcontent-1009af0a-24c2-4435-861c-516224503f2d   <invalid>      78s
    ```

