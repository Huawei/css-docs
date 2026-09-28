---
title: "查询存储后端"
linkTitle: "查询存储后端"
description: 
weight: 2
---

## 查询StorageBackendClaim{#section169128734716}

1.  执行以下命令查询默认命名空间下所有存储后端声明。

    ```
    kubectl get sbc -n huawei-csi
    ```

    命令结果示例如下：

    ```
    NAME             STORAGEBACKENDCONTENTNAME      STATUS   AGE
    backend-demo     content-xxxxxxxxxxxx           Bound    53d
    ```

2.  执行以下命令以YAML格式查看存储后端声明。

    ```
    kubectl get sbc backend-demo -n huawei-csi -o yaml
    ```

## 查询StorageBackendContent{#section116041549115320}

1.  执行以下命令查询所有存储后端实例。

    ```
    kubectl get sbct
    ```

    命令结果示例如下：

    ```
    NAME              CLAIM                       SN               VENDORNAME   PROVIDERVERSION   ONLINE   AGE
    content-xxxxxxx   huawei-csi/backend-demo     xxxxxxxxxxxxxx   Huawei       4.13.0            true     53d
    ```

2.  执行以下命令以YAML格式查看存储后端示例。

    ```
    kubectl get sbct content-xxxxxxx -o yaml
    ```

