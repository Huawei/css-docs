---
title: "存储后端证书管理"
linkTitle: "存储后端证书管理"
description: 
weight: 4
---

CSI支持通过添加存储证书的方式，使用TLS/SSL协议加密数据传输通道，提高与存储通信的安全性。

## 添加存储证书{#section1156241310541}

1.  完成证书制作。以OceanStor Dorado为例，证书制作过程请参考：[点此前往](https://support.huawei.com/hedex/hdx.do?docid=EDOC1100214749&id=ZH-CN_TOPIC_0000001595814228)。
2.  执行以下命令，从证书文件创建Secret。

    ```
    kubectl create secret generic cert-1 --from-file=tls.crt=/path/to/cert.crt -n huawei-csi
    ```

3.  执行以下命令更新StorageBackendClaim，启用证书并指定证书Secret。certSecret字段的格式为<namespace\>/<secret-name\>。

    ```
    kubectl patch sbc backend-demo -n huawei-csi --type merge -p '{"spec":{"useCert":true,"certSecret":"huawei-csi/cert-1"}}'
    ```

4.  执行以下命令检查存储后端更新结果。

    ```
    kubectl get StorageBackendContent
    ```

    命令结果示例如下，StorageBackendContent在线状态为true，则更新成功。

    ```
    NAME              CLAIM                       SN               VENDORNAME   PROVIDERVERSION   ONLINE   AGE
    content-xxxxxxx   huawei-csi/backend-demo     xxxxxxxxxxxxxx   Huawei       4.13.0            true     53d
    ```

## 移除存储证书{#section12785430175717}

1.  执行以下命令将StorageBackendClaim的证书配置清除。

    ```
    kubectl patch sbc backend-demo -n huawei-csi --type merge -p '{"spec":{"useCert":false,"certSecret":""}}'
    ```

2.  删除证书Secret。

    ```
    kubectl delete secret cert-1 -n huawei-csi
    ```

