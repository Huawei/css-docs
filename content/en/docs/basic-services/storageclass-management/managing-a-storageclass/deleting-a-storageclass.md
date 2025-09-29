---
title: "Deleting a StorageClass"
linkTitle: "Deleting a StorageClass"
description: 
weight: 3
---

1.  Run the following command to view the StorageClass:

    ```
    kubectl get sc mysc
    ```

    The following is an example of the command output.

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           false                  8s
    ```

2.  Run the following command to delete the StorageClass:

    ```
    kubectl delete sc mysc
    ```

    If the following information is displayed, the deletion is successful:

    ```
    storageclass.storage.k8s.io "mysc" deleted
    ```

