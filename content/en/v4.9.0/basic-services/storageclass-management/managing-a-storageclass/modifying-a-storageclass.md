---
title: "Modifying a StorageClass"
linkTitle: "Modifying a StorageClass"
description: 
weight: 2
---

Kubernetes allows only the  **allowVolumeExpansion**  field of a StorageClass to be modified. The modification method is as follows:

1.  Run the following command to check whether the StorageClass can be expanded:

    ```
    kubectl get sc mysc
    ```

    If the command output is displayed as the following example, the StorageClass  **mysc**  cannot be expanded:

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           false                  8s
    ```

2.  Run the following command to enable capacity expansion for the StorageClass:

    ```
    kubectl patch sc mysc --patch '{"allowVolumeExpansion":true}'
    ```

3.  Check the StorageClass again and ensure that the modification is successful.

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           true                   8s
    ```

