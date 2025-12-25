---
title: "查询卷快照"
linkTitle: "查询卷快照"
description: 
weight: 1
---

## 查看卷快照类{#section1116853914280}

1.  执行以下命令，查看已创建的VolumeSnapshotClass信息。

    ```
    kubectl get volumesnapshotclass
    ```

    命令结果示例如下：

    ```
    NAME          DRIVER           DELETIONPOLICY   AGE
    mysnapclass   csi.huawei.com   Delete           25s
    ```

## 查询卷快照{#section5247123019291}

1.  执行以下命令，查看已创建的VolumeSnapshot信息。

    ```
    kubectl get volumesnapshot
    ```

    命令结果示例如下：

    ```
    NAME         READYTOUSE   SOURCEPVC   SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS   SNAPSHOTCONTENT                                    CREATIONTIME   AGE
    mysnapshot   true         mypvc                               100Gi         mysnapclass     snapcontent-1009af0a-24c2-4435-861c-516224503f2d   <invalid>      78s
    ```

