---
title: "查询存储类"
linkTitle: "查询存储类"
description: 
weight: 1
---

1.  执行命令，查看已创建的StorageClass信息。

    ```
    kubectl get sc mysc
    ```

    命令结果示例如下：

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           true                   8s
    ```

