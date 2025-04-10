---
title: "创建证书到存储后端"
linkTitle: "创建证书到存储后端"
description: 
weight: 1
---

## 前提条件{#section414814741510}

完成证书制作。以OceanStor Dorado为例，证书制作过程请参考：[点此前往](https://support.huawei.com/hedex/hdx.do?docid=EDOC1100214749&id=ZH-CN_TOPIC_0000001595814228)。

## 创建证书示例{#section1393413618152}

1.  提前准备好证书文件，如cert.crt。
2.  执行以下命令获取存储后端。

    ```
    oceanctl get backend  
    ```

    命令结果示例如下：

    ```
    NAMESPACE     NAME         PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-1    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    huawei-csi    backend-2    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.158:8088  
    ```

3.  执行以下命令为指定存储后端创建证书。

    ```
    oceanctl create cert cert-1 -b backend-1 -f /path/to/cert.crt
    ```

4.  检查证书创建结果。

    ```
    oceanctl get cert -b backend-1
    ```

    命令结果示例如下：

    ```
    NAMESPACE    NAME    BOUNDBACKEND   
    huawei-csi   cert-1  backend-1 
    ```

