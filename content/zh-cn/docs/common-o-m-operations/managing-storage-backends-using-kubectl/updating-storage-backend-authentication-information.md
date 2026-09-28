---
title: "更新存储后端认证信息"
linkTitle: "更新存储后端认证信息"
description: 
weight: 3
---

为避免直接修改现有Secret导致存储后端短暂不可用，建议采用"先创建新Secret、替换引用、再删除旧Secret"的方式更新认证信息。

## 操作步骤{#section051012213157}

1.  准备新的Secret配置文件，如backend-secret-new.yaml。

    ```yaml
    apiVersion: v1
    kind: Secret
    metadata:
      name: backend-demo-new
      namespace: huawei-csi
    type: Opaque
    stringData:
      user: "admin"
      password: "******"
      authenticationMode: "0"
    ```

2.  执行以下命令创建新的Secret。

    ```
    kubectl apply -f backend-secret-new.yaml
    ```

3.  更新StorageBackendClaim，将secretMeta指向新的Secret。CSI会自动将新Secret同步到StorageBackendContent，并使用新的认证信息重新登录存储设备。

    ```
    kubectl patch sbc backend-demo -n huawei-csi --type merge -p '{"spec":{"secretMeta":"huawei-csi/backend-demo-new"}}'
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

5.  删除旧的Secret。

    ```
    kubectl delete secret backend-demo -n huawei-csi
    ```

