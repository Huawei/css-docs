---
title: "纳管卷供应"
linkTitle: "纳管卷供应"
description: 
weight: 2
---

纳管卷供应（Manage Volume Provisioning）允许管理员使用已经在存储侧创建的资源做为PV，并能够支持动态卷的特性，例如：扩容，快照，克隆等，属于华为CSI自定义能力。使用该特性可满足如下场景：

-   容器化应用的改造场景，需要使用已有的存储卷。
-   重建Kubernetes集群。
-   容灾场景下，对存储数据进行迁移。

>![](/public_sys-resources/zh/icon-note.gif) 
>在多Kubernetes集群场景下，使用纳管卷特性对同一存储资源进行管理时，在任一集群中对该资源对应的PVC进行管理操作后，不会同步到其他集群中。
>例如：在某一集群中对PVC进行扩容时，其他集群对应的PVC不会自动扩容，需要在其他集群中手动根据[扩容PVC](/docs/使用华为CSI/PVC管理/扩容PVC)中的扩容命令进行扩容。

## 前提条件{#section65071656132313}

-   已在CSI中注册需要纳管卷所在存储。
-   已登录存储设备获取需要纳管卷的名称和容量。

## 配置StorageClass{#section19289935145}

1.  根据业务需要，参考[动态卷供应典型场景StorageClass配置示例](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应典型场景StorageClass配置示例)和[动态卷供应StorageClass参数说明](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应StorageClass参数说明)，创建StorageClass配置文件，如本例从的mysc.yaml文件。
2.  执行命令，使用配置文件创建StorageClass。

    ```
    kubectl apply -f mysc.yaml
    ```

3.  执行命令，查看已创建的StorageClass信息。

    ```
    kubectl get sc mysc
    ```

    命令结果示例如下：

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           true                   8s
    ```

## 配置PVC{#section1836215261144}

1.  根据业务需要，参考本节描述和PVC配置文件示例，修改具体参数，生成本次需要创建的PVC配置文件，如本例中mypvc.yaml文件。

    ```yaml
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: mypvc
      annotations:
        csi.huawei.com/manageVolumeName: "*"  # 存储资源名称
        csi.huawei.com/manageBackendName: "*" # 存储后端名称
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

2.  执行命令，使用配置文件创建PVC。

    ```
    kubectl create -f mypvc.yaml
    ```

3.  等待一段时间后，执行以下命令，查看已经创建的PVC信息。

    ```
    kubectl get pvc mypvc
    ```

    命令结果示例如下。如果PVC的状态是“Bound”时，则说明该PVC已经创建成功，后续可以被Pod使用。

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO            mysc           12s
    ```

    >![](/public_sys-resources/zh/icon-notice.gif)  
    >-   完成创建PVC操作后，如果长时间后（如一分钟后）PVC的状态是Pending，请参考[创建PVC时， PVC的状态为Pending](/docs/故障处理/PVC相关问题/创建PVC时-PVC的状态为Pending)。
    >-   建议每批次最多批量创建/删除100个PVC。

## 使用PVC{#section847932614377}

与动态卷供应[使用PVC](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应#section8172141413917)方式相同。




