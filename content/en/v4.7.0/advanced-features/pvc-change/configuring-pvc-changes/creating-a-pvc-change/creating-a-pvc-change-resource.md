---
title: "Creating a PVC Change Resource"
linkTitle: "Creating a PVC Change Resource"
description: 
weight: 2
---

This section describes how to create a PVC change resource based on a configured PVC change file.

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   Only the HyperMetro active-active \(AA\) mode is supported.
>-   When a common volume is changed to a HyperMetro volume, only the storage volume at the primary site can be changed.
>-   Do not use Huawei CSI to manage a PVC during PVC change resource creation.
>-   Multiple VolumeModifyClaim resources cannot be created for the same PVC. If the target PVC needs to be changed for multiple times, perform the changes one by one.

## Procedure{#section694142182112}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to create a PVC change.

    ```
    kubectl create -f volumemodifyclaim.yaml 
    ```

3.  Query the creation result by following the instructions in  [Querying a PVC Change](/docs/advanced-features/pvc-change/configuring-pvc-changes/querying-a-pvc-change).

