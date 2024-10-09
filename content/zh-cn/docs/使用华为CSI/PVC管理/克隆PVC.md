---
title: "克隆PVC"
linkTitle: "克隆PVC"
description: 
weight: 3
---

本章节描述如何克隆PVC。

在克隆PVC时，需要指定数据源。如下示例是一个简单的克隆PVC示例，在该示例中，使用“mypvc”作为数据源，新创建了一个名叫“myclone”的PVC。

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

>![](/public_sys-resources/zh/icon-notice.gif)  
>-   指定的storageClassName必须和dataSource中的源卷的StorageClass需一致。
>-   克隆卷的容量必须不小于源卷容量，建议和源卷容量保持一致。

## 前提条件{#section349216304616}

系统中已经存在源PVC，且源PVC所在的backend存在支持克隆。支持克隆的存储请参考[表 华为企业存储支持的特性及约束](/docs/兼容性和特性/华为企业存储兼容性#table14995183994515)和[表 华为分布式存储支持的特性及约束](/docs/兼容性和特性/华为分布式存储兼容性#table175022559255)，支持克隆的Kubernetes版本请参考[Kubernetes特性矩阵](/docs/兼容性和特性/Kubernetes特性矩阵)。

## 操作步骤{#zh-cn_topic_0254212544_section319012981414}

1.  执行以下命令，基于克隆卷的配置文件创建PVC。

    ```
    kubectl create -f myclone.yaml
    ```

