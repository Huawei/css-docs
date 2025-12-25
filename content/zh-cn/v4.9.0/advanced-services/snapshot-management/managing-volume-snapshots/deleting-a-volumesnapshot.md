---
title: "删除卷快照"
linkTitle: "删除卷快照"
description: 
weight: 3
---

## 删除卷快照{#section17253353163115}

当后续不需要使用该卷快照时，执行该操作。

## 操作步骤{#section1976104203312}

1.  执行以下命令，查看已创建的VolumeSnapshot信息。

    ```
    kubectl get volumesnapshot
    ```

    命令结果示例如下：

    ```
    NAME         READYTOUSE   SOURCEPVC   SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS   SNAPSHOTCONTENT                                    CREATIONTIME   AGE
    mysnapshot   true         mypvc                               100Gi         mysnapclass     snapcontent-1009af0a-24c2-4435-861c-516224503f2d   <invalid>      78s
    ```

2.  执行下列命令，删除VolumeSnapshot：

    ```
    kubectl delete volumesnapshot mysnapshot 
    ```

    回显如下所示，表示删除成功：

    ```
    volumesnapshot.snapshot.storage.k8s.io "mysnapshot" deleted
    ```

## 删除卷快照类{#section12459185133213}

当该卷快照类没有绑定任何卷快照，且后续不需要使用该卷快照类时，执行该操作。

## 操作步骤{#section4278153218329}

1.  执行以下命令，查看卷快照类。

    ```
    kubectl get vsclass
    ```

    命令结果示例如下：

    ```
    NAME          DRIVER           DELETIONPOLICY   AGE
    mysnapclass   csi.huawei.com   Delete           25s
    ```

2.  执行下列命令，删除存储类：

    ```
    kubectl delete vsclass mysnapclass
    ```

    回显如下所示，表示删除成功：

    ```
    volumesnapshotclass.snapshot.storage.k8s.io "mysnapclass" deleted
    ```

