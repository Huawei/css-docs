---
title: "删除存储类"
linkTitle: "删除存储类"
description: 
weight: 3
---

1.  执行命令，查看存储类。

    ```
    kubectl get sc mysc
    ```

    命令结果示例如下：

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           false                  8s
    ```

2.  执行下列命令，删除存储类：

    ```
    kubectl delete sc mysc
    ```

    回显如下所示，表示删除成功：

    ```
    storageclass.storage.k8s.io "mysc" deleted
    ```

