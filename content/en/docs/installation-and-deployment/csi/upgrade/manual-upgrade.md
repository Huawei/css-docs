---
title: "Manual Upgrade"
linkTitle: "Manual Upgrade"
description: 
weight: 2
---

This section describes how to manually upgrade Huawei CSI.

During the upgrade or rollback, the existing resources such as PVCs, snapshots, and Pods will run properly and will not affect your service access.

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   Some CSI 2._x_  versions are unavailable now. If the upgrade fails, CSI may fail to be rolled back to a version which is unavailable now.
>-   During the upgrade or rollback, you cannot use Huawei CSI to create new resources or mount or unmount an existing PVC.
>-   During the upgrade or rollback, do not uninstall the snapshot-dependent component service.

## Upgrading CSI from 2.x or 3.x to  4.10.0{#section260220843210}

To upgrade CSI from 2._x_  or 3._x_  to  4.10.0, perform the following operations:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  <a name="li1699321211285"></a>Run the following command to back up the backend information to the  **configmap.json**  file. For the OpenShift platform, replace  **kubectl**  with  **oc**.

    ```
    kubectl get cm huawei-csi-configmap -n huawei-csi -o json > configmap.json
    ```

3.  Uninstall CSI. For details, see  [Manual Uninstallation](/docs/installation-and-deployment/csi/uninstallation/manual-uninstallation).
4.  Install CSI of the current version. For details, see  [Manual Installation](/docs/installation-and-deployment/csi/installation/manual-installation).
5.  Install the backend information backed up in  [2](#li1699321211285)  according to  [Storage Backend Management](/docs/basic-services/storage-backend-management).

## Upgrading CSI from 4.x to  4.10.0{#section173369363219}

To upgrade CSI from 4._x_  to  4.10.0, perform the following operations:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Uninstall CSI. For details, see  [Manual Uninstallation](/docs/installation-and-deployment/csi/uninstallation/manual-uninstallation).
3.  Install CSI of the current version. For details, see  [Manual Installation](/docs/installation-and-deployment/csi/installation/manual-installation).

