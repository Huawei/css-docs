---
title: "检查卷快照依赖组件"
linkTitle: "检查卷快照依赖组件"
description: 
weight: 4
---

本章节介绍如何检查集群中卷快照依赖组件情况。

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>由于Kubernetes v1.17.0之前不支持快照功能，如果部署快照CRD可能导致集群出现问题，因此在低于Kubernetes v1.17.0版本上部署华为CSI，请务必按照[Kubernetes低于v1.17.0](#section6894165917369)章节检查。

## Kubernetes低于v1.17.0{#section6894165917369}

Kubernetes低于v1.17.0时，部署快照时将会导致集群出现问题，请按照以下步骤删除快照CRD安装文件。

1.  执行以下命令查看Kubernetes版本。如下示例中，Kubernetes版本为v1.16.0。

    ```
    kubectl get node
    ```

    命令结果示例如下：

    ```
    NAME          STATUS       ROLES     AGE    VERSION
    test-master   Ready        master    311d   v1.16.0
    test-node     Ready        <none>    311d   v1.16.0
    ```

2.  进入/helm/esdk/crds/snapshot-crds目录，执行以下命令，删除快照CRD安装文件。组件包路径请参考[表1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。

    ```
    rm -rf ./huawei-csi-snapshot-crd-v1.yaml
    ```

