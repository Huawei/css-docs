---
title: "更新存储后端证书"
linkTitle: "更新存储后端证书"
description: 
weight: 3
---

更新证书前请准备好新的证书文件，并参考本章节更新存储后端证书。如果不再使用证书，请参考[删除存储后端证书](/docs/storage-backend-management/adding-a-certificate-to-a-storage-backend/deleting-a-storage-backend-certificate)章节移除存储后端上的证书。

## 操作步骤{#section127643118416}

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

2.  执行以下命令查看指定存储后端是否存在证书。

    ```
    oceanctl get cert -b backend-1
    ```

    命令结果示例如下：

    ```
    NAMESPACE   NAME    BOUNDBACKEND    
    huawei-csi  cert-1  backend-1  
    ```

3.  执行以下命令更新指定存储后端的证书。

    ```
    oceanctl update cert -b backend-1 -f /path/to/cert.crt
    ```

