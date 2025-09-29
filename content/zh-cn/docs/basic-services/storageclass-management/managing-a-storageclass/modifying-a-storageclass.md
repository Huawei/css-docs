---
title: "修改存储类"
linkTitle: "修改存储类"
description: 
weight: 2
---

Kubernetes限制仅允许修改存储类  **是否允许扩容字段**  （allowVolumeExpansion），修改方式如下：

1.  执行命令，查看存储类是否允许扩容。

    ```
    kubectl get sc mysc
    ```

    命令结果示例如下，存储类mysc不允许扩容：

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           false                  8s
    ```

2.  执行下列命令，将存储类修改为允许扩容：

    ```
    kubectl patch sc mysc --patch '{"allowVolumeExpansion":true}'
    ```

3.  再次查看存储类，修改成功：

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           true                   8s
    ```

