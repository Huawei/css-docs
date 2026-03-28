---
title: "从卷快照创建持久卷"
linkTitle: "从卷快照创建持久卷"
description: 
weight: 2
---

## 前提条件{#zh-cn_topic_0254212585_section0772716133710}

-   支持从卷快照创建PVC的存储请参考存储自身的[特性表](/docs/compatibility-and-features)，选择对应存储类型和业务类型进行查询。
-   支持从卷快照创建PVC的Kubernetes版本请参考[Kubernetes特性矩阵](/docs/appendix/kubernetes-feature-matrix)。
-   已经存在卷快照，且卷快照所在的backend支持克隆。

在创建PVC时，需要指定卷快照作为数据源。如下是一个从卷快照创建PVC示例，在该示例中，使用快照“mysnapshot”作为数据源，新创建了一个名叫“myrestore”的PVC。

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

## 操作步骤{#section145015152569}

1.  执行以下命令，基于从快照创建卷的配置文件创建PVC。

    ```
    kubectl create -f myrestore.yaml
    ```

