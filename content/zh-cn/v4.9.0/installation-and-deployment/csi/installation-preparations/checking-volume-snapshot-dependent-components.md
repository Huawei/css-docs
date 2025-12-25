---
title: "检查卷快照依赖组件"
linkTitle: "检查卷快照依赖组件"
description: 
weight: 4
---

本章节介绍如何检查集群中卷快照依赖组件情况。

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>Kubernetes v1.20之前版本部署华为CSI，请按照以下步骤检查。

1.  执行以下命令查看Kubernetes版本。以Kubernetes版本v1.16.0为例。

    ```
    kubectl get node
    ```

    命令结果示例如下：

    ```
    NAME          STATUS       ROLES     AGE    VERSION
    test-master   Ready        master    311d   v1.16.0
    test-node     Ready        <none>    311d   v1.16.0
    ```

2.  将Kubernetes CSI组件包中的"helm"目录拷贝到master节点的任意目录下。Helm工具路径请参见[表1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。
3.  进入helm/esdk/crds/snapshot-crds目录，执行以下命令，删除快照CRD安装文件。

    ```
    rm -rf ./huawei-csi-snapshot-crd-v1.yaml
    ```

