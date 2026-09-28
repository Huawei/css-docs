---
title: "Deleting a Storage Backend"
linkTitle: "Deleting a Storage Backend"
description: 
weight: 5
---

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>Do not delete a storage backend when a volume management operation is being performed on it.

1.  Delete the StorageBackendClaim.

    ```
    kubectl delete sbc backend-demo -n huawei-csi
    ```

    After the StorageBackendClaim is deleted, the controller automatically deletes the associated StorageBackendContent.

2.  Check whether StorageBackendContent is deleted.

    ```
    kubectl get sbct
    ```

    If the associated StorageBackendContent is no longer listed, the deletion is successful.

3.  Run the following commands to manually delete the associated ConfigMap and secret:

    ```
    kubectl delete configmap backend-demo -n huawei-csi
    kubectl delete secret backend-demo -n huawei-csi
    ```

