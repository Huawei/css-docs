---
title: "删除存储后端"
linkTitle: "删除存储后端"
description: 
weight: 4
---

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>正在执行卷管理操作期间，请勿删除存储后端。

## 删除后端示例{#section20764568435}

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

2.  执行以下命令删除指定存储后端。

    ```
    oceanctl delete backend backend-1
    ```

3.  执行以下命令检查删除结果。

    ```
    oceanctl get backend backend-1
    ```

    命令结果示例如下，如果回显为“not found”则删除成功。

    ```yaml
    Error from server (NotFound): backend "backend-1" not found
    ```

