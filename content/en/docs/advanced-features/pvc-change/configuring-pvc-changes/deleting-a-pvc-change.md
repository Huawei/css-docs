---
title: "Deleting a PVC Change"
linkTitle: "Deleting a PVC Change"
description: 
weight: 3
---

>![](/css-docs/public_sys-resources/en/icon-notice.gif) 
>-   If  **STATUS**  of a VolumeModifyClaim is  **Creating**, deleting the VolumeModifyClaim resource will delete the created resource on the storage side and then remove the cluster resource. After the deletion, if you continue to use the original StorageClass for PVC management, you need to restore the associated storage backend to a non-HyperMetro storage backend.
>-   If  **STATUS**  of a VolumeModifyClaim is  **Pending**  or  **Completed**, deleting the VolumeModifyClaim resource will only remove the cluster resource and will not delete the created resource on the storage side \(that is, there is not interaction with the storage side\).
>-   VolumeModifyContent resources are managed by VolumeModifyClaim. Do not manually manage VolumeModifyContent resources.
>-   If some PVCs among the PVCs to be changed meet the change requirements and the batch change fails, all PVC changes will be removed. As a result, the PVCs that meet the change requirements will not meet the change requirements.
>-   If a PVC to be changed has been manually managed on the storage side, the change may fail. Do not manually manage storage volumes when using the change feature.

This section describes how to use kubectl to delete a PVC change. The procedure is as follows.

## Procedure{#section694142182112}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to delete a PVC change. In the command,  _vmc-name_  indicates the name of the VolumeModifyClaim resource.

    ```
    kubectl delete volumemodifyclaims <vmc-name>
    ```

3.  Query the deletion result by following the instructions in  [Creating a PVC Change Resource](/docs/advanced-features/pvc-change/configuring-pvc-changes/creating-a-pvc-change/creating-a-pvc-change-resource).

