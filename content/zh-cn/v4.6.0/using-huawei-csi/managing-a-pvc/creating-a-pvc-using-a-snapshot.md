---
title: "从快照创建PVC"
linkTitle: "从快照创建PVC"
description: 
weight: 4
---

本章节描述如何从快照创建PVC。

在创建这个PVC时，需要指定数据源。如下示例是一个简单的从快照创建PVC示例，在该示例中，使用快照“mysnapshot”作为数据源，新创建了一个名叫“myrestore”的PVC。

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: myrestore
spec:
  storageClassName: mysc
  dataSource:
    name: mysnapshot
    kind: VolumeSnapshot
    apiGroup: snapshot.storage.k8s.io
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 100Gi
```

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   指定的storageClassName必须和dataSource中的快照源卷的StorageClass需一致。
>-   克隆卷的容量必须不小于快照容量，建议和快照容量保持一致。

## 前提条件{#zh-cn_topic_0254212585_section0772716133710}

系统中已经存在快照，且快照所在的backend存在支持克隆。支持快照创建PVC的存储请参考[华为企业存储支持的特性](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage#section0652122673620)和[华为企业存储支持的特性](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage#section0652122673620)，支持快照创建PVC的Kubernetes版本请参考[Kubernetes特性矩阵](/docs/compatibility-and-features/kubernetes-feature-matrix)。

## 操作步骤{#zh-cn_topic_0254212585_section1882544631619}

1.  执行以下命令，基于从快照创建卷的配置文件创建PVC。

    ```
    kubectl create -f myrestore.yaml
    ```

