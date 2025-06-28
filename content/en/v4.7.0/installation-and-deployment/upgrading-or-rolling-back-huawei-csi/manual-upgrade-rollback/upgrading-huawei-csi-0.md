---
title: "Upgrading Huawei CSI"
linkTitle: "Upgrading Huawei CSI"
description: 
weight: 1
---

This section describes how to manually upgrade Huawei CSI.

During the upgrade or rollback, the existing resources such as PVCs, snapshots, and Pods will run properly and will not affect your service access.

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   Some CSI 2._x_  versions are unavailable now. If the upgrade fails, CSI may fail to be rolled back to a version which is unavailable now.
>-   During the upgrade or rollback, you cannot use Huawei CSI to create new resources or mount or unmount an existing PVC.
>-   During the upgrade or rollback, do not uninstall the snapshot-dependent component service.

## Upgrading CSI from 2.x or 3.x to  4.7.0{#section260220843210}

To upgrade CSI from 2._x_  or 3._x_  to  4.7.0, perform the following operations:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  <a name="li1699321211285"></a>Run the following command to back up the backend information to the  **configmap.json**  file. For the OpenShift platform, replace  **kubectl**  with  **oc**.

    ```
    kubectl get cm huawei-csi-configmap -n huawei-csi -o json > configmap.json
    ```

3.  Uninstall CSI. For details, see  [Manually Uninstalling Huawei CSI](/docs/installation-and-deployment/uninstalling-huawei-csi/manually-uninstalling-huawei-csi).
4.  Install CSI of the current version. For details, see  [Manually Installing Huawei CSI](/docs/installation-and-deployment/installing-huawei-csi/manually-installing-huawei-csi).
5.  Install the backend information backed up in  [2](#li1699321211285)  according to  [Managing Storage Backends](/docs/storage-backend-management/managing-storage-backends).

## Upgrading CSI from 4.x to  4.7.0{#section173369363219}

To upgrade CSI from 4._x_  to  4.7.0, perform the following operations:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Uninstall CSI. For details, see  [Manually Uninstalling Huawei CSI](/docs/installation-and-deployment/uninstalling-huawei-csi/manually-uninstalling-huawei-csi).
3.  Install CSI of the current version. For details, see  [Manually Installing Huawei CSI](/docs/installation-and-deployment/installing-huawei-csi/manually-installing-huawei-csi).

