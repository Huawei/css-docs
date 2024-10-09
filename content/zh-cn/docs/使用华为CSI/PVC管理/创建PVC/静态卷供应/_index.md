---
title: "静态卷供应"
linkTitle: "静态卷供应"
description: 
weight: 3
---

静态卷供应（Static Volume Provisioning）允许管理员使用已经在存储侧创建的资源做为PV，供集群中的容器使用。

为了完成静态卷供应，需要完成如下两步：

-   配置PV
-   配置PVC

## 前提条件{#section4107171112475}

存储侧已经存在待创建PV所需要的存储资源，如LUN或者文件系统。如果存储资源是文件系统，还需要创建文件系统的共享和客户端信息。

## 配置PV{#section1994861643814}

1.  准备PV配置文件mypv.yaml，示例如下，其他配置参数请参考[静态卷供应PV参数说明](/docs/使用华为CSI/PVC管理/创建PVC/静态卷供应/静态卷供应PV参数说明)。

    ```yaml
    kind: PersistentVolume
    apiVersion: v1
    metadata:
      name: mypv
    spec:
      volumeMode: Filesystem
      storageClassName: "" # 必须配置为""
      accessModes:
        - ReadWriteOnce
      csi:
        driver: csi.huawei.com # csi驱动名称
        volumeHandle: iscsi-dorado-181.lun0001 # 卷名称
        fsType: xfs # 文件系统类型
      capacity:
        storage: 100Gi
    ```

    >![](/public_sys-resources/zh/icon-note.gif) 
    >静态卷供应的配置文件中，storageClassName参数必须配置为‘“”’，如果不配置，Kubernetes会使用系统默认的StorageClass。

2.  执行以下命令，基于准备好的yaml文件创建PV。

    ```
    kubectl create -f mypv.yaml
    ```

3.  等待一段时间后，执行以下命令，查看已经创建的PV信息。

    ```
    kubectl get pv
    ```

    命令结果示例如下，当PV状态为“Available”时，表明PV创建成功。

    ```
    NAME       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM               STORAGECLASS   REASON   AGE
    mypv       100Gi      RWO            Retain           Available                                               4s
    ```

## 配置PVC{#section166021742104214}

当PV以静态卷供应的方式创建完成后，可以基于该PV创建PVC，从而供容器使用。

1.  首先准备PVC配置文件。如下示例是一个使用静态卷供应的PVC配置文件。

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
      volumeName: mypv # 对应PV名称
    ```

2.  执行以下命令，基于已配置的yaml文件创建PVC。

    ```
    kubectl create -f mypvc.yaml
    ```

3.  等待一段时间后，执行以下命令，查看已经创建的PVC信息。

    ```
    kubectl get pvc
    ```

    命令结果示例如下，当PVC状态为“Bound“时，表明PVC创建成功。

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO                           12s
    ```

    >![](/public_sys-resources/zh/icon-note.gif) 
    >-   完成创建PVC操作后，如果长时间后（如一分钟后）PVC的状态是Pending，请参考[创建PVC时， PVC的状态为Pending](/docs/故障处理/PVC相关问题/创建PVC时-PVC的状态为Pending)。
    >-   建议每批次最多批量创建/删除100个PVC。

## 使用PVC{#section2949728204519}

与动态卷供应[使用PVC](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应#section8172141413917)方式相同。



