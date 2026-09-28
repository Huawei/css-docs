---
title: "删除存储后端"
linkTitle: "删除存储后端"
description: 
weight: 5
---

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>正在执行卷管理操作期间，请勿删除存储后端。

1.  执行以下命令删除StorageBackendClaim。

    ```
    kubectl delete sbc backend-demo -n huawei-csi
    ```

    删除StorageBackendClaim后，控制器会自动删除关联的StorageBackendContent。

2.  执行以下命令，确认StorageBackendContent已被删除。

    ```
    kubectl get sbct
    ```

    如果关联的StorageBackendContent不再列出，则删除成功。

3.  执行以下命令，手动删除关联的ConfigMap和Secret。

    ```
    kubectl delete configmap backend-demo -n huawei-csi
    kubectl delete secret backend-demo -n huawei-csi
    ```

