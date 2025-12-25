---
title: "克隆持久卷"
linkTitle: "克隆持久卷"
description: 
weight: 2
---

本章节描述如何克隆PVC。

在克隆PVC时，需要指定数据源。如下是一个克隆PVC示例，在该示例中，使用“mypvc”作为数据源，新创建了一个名叫“myclone”的PVC。

```yaml
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: myclone
spec:
  storageClassName: mysc
  dataSource:
    name: mypvc
    kind: PersistentVolumeClaim
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 2Gi
```

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   指定的storageClassName必须和dataSource中的源卷的StorageClass需一致。
>-   克隆卷的容量必须不小于源卷容量，建议和源卷容量保持一致。

## 前提条件{#section349216304616}

系统中已经存在源PVC，且源PVC所在的backend支持克隆。支持克隆的存储请参考[兼容性和特性](/docs/compatibility-and-features)章节中的特性表格，支持克隆的Kubernetes版本请参考[Kubernetes特性矩阵](/docs/appendix/kubernetes-feature-matrix)。

## 操作步骤{#section153154508193}

1.  执行以下命令，基于克隆卷的配置文件创建PVC。

    ```
    kubectl create -f myclone.yaml
    ```

