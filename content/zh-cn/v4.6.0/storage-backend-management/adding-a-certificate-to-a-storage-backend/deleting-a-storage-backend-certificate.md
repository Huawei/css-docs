---
title: "删除存储后端证书"
linkTitle: "删除存储后端证书"
description: 
weight: 4
---

## 操作步骤{#section14609953142910}

1.  执行以下命令获取存储后端。

    ```
    oceanctl get backend  
    ```

    命令结果示例如下：

    ```
    NAMESPACE     NAME         PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-1    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    huawei-csi    backend-2    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.158:8088  
    ```

2.  执行以下命令获取指定存储后端的证书。

    ```
    oceanctl get cert -b backend-1
    ```

    命令结果示例如下：

    ```
    NAMESPACE   NAME    BOUNDBACKEND    
    huawei-csi  cert-1  backend-1  
    ```

3.  执行以下命令删除指定存储后端的证书。

    ```
    oceanctl delete cert -b backend-1
    ```

4.  检查删除结果。

    ```
    oceanctl get cert -b backend-1
    ```

    命令结果示例如下，如果回显为“no cert found”则删除成功。

    ```yaml
    Error from server (NotFound): no cert found on backend backend-1 in huawei-csi namespace
    ```

