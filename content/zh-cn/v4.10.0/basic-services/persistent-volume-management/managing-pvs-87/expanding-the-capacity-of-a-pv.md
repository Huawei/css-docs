---
title: "扩容持久卷"
linkTitle: "扩容持久卷"
description: 
weight: 1
---

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>OceanStor V700R001C10和OceanStor Dorado V700R001C10及以后版本，扩容后文件系统的容量存在最小限制，具体限制值参考对应存储的产品手册。

当容器使用的PVC容量不足时，需要对该PVC进行扩容操作。

## 前提条件{#zh-cn_topic_0254162571_section07036257166}

-   PVC已创建，所在的backend存在且支持扩容。
-   支持扩容的存储请参考[兼容性和特性](/docs/compatibility-and-features)章节中的特性表格，支持扩容的Kubernetes版本请参考[Kubernetes特性矩阵](/docs/appendix/kubernetes-feature-matrix)。
-   huawei-csi-controller启用了csi-resizer服务。

    ```
    kubectl describe deploy huawei-csi-controller -n huawei-csi | grep csi-resizer
    ```

    命令回显示例如下则说明已启用csi-resizer服务。

    ```yaml
       csi-resizer:
        Image:      k8s.gcr.io/sig-storage/csi-resizer:v1.9.0
    ```

## 操作步骤{#section06451161277}

1.  执行命令，查询StorageClass是否支持扩容。其中，_mysc_  为需要查看的StorageClass名称。

    ```
    kubectl get sc mysc
    ```

    命令结果示例如下：

    ```
    NAME              PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc              csi.huawei.com   Delete          Immediate           true                  172m
    ```

    如果ALLOWVOLUMEEXPANSION的值为true，表示当前StorageClass已经支持扩容，请跳转至步骤[3](#zh-cn_topic_0254162571_li1143318914115)。

2.  执行以下命令，将“allowVolumeExpansion“的值修改为“true“。其中，_mysc_  为需要修改的StorageClass名称。

    ```
    kubectl patch sc mysc --patch '{"allowVolumeExpansion":true}'
    ```

3.  <a name="zh-cn_topic_0254162571_li1143318914115"></a>执行命令，查询PVC的StorageClass名称。其中，_mypvc_  为需要扩容的PVC名称。

    ```
    kubectl get pvc mypvc
    ```

    命令结果示例如下：

    ```
    NAME               STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS      AGE
    mypvc              Bound    pvc-3383be36-537c-4cb1-8f32-a415fa6ba384   2Gi        RW0            mysc              145m
    ```

4.  执行以下命令进行扩容。

    ```
    kubectl patch pvc mypvc -p '{"spec":{"resources":{"requests":{"storage":"120Gi"}}}}'
    ```

    其中，"_mypvc_"是需要扩容的PVC名称，“_120Gi_”是扩容后的容量大小。请根据实际情况进行替换。

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >-   PVC容量的规格取决于存储规格限制和主机规格限制。以OceanStor Dorado 6.1.2/OceanStor Pacific系列 8.1.0对接CentOS 7为例，当使用的是ext4文件系统时，容量限制见[表2](/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#zh-cn_topic_0150885187_table178824527142)；当使用的是XFS文件系统时，容量限制见[表3](/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#zh-cn_topic_0150885187_table101951367104)。如果使用的是NFS或者裸设备，容量需满足使用的华为存储设备型号和版本所要求的规格约束。
    >-   如果PVC容量不在规格范围内，可能会由于存储规格限制或主机文件系统规格限制导致创建PVC或Pod失败。
    >-   如果扩容的目标容量超过存储池容量导致扩容失败，请参考[PVC扩容的目标容量超过存储池容量导致扩容失败](/docs/troubleshooting/pvc-issues/failed-to-expand-the-pvc-capacity-because-the-target-capacity-exceeds-the-storage-pool-capacity)。

5.  执行命令，检查容量修改是否生效。

    ```
    kubectl get pvc
    ```

    命令结果示例如下，如果CAPACITY字段已变更为指定容量，说明扩容成功。

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-3383be36-537c-4cb1-8f32-a415fa6ba384   120Gi       RWO            mysc           24s
    ```

