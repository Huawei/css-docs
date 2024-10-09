---
title: "Upgrading Huawei CSI"
linkTitle: "Upgrading Huawei CSI"
description: 
weight: 1
---

This section describes how to upgrade Huawei CSI.

During the upgrade or rollback, the existing resources such as PVCs, snapshots, and Pods will run properly and will not affect your service access.

>![](/public_sys-resources/en/icon-notice.gif) 
>-   Some CSI 2._x_  versions are unavailable now. If the upgrade fails, CSI may fail to be rolled back to a version which is unavailable now.
>-   After an upgrade from 2._x_, 3._x_, or 4._x_  to  4.5.0, a Pod that has been provisioned in the source version may fail to be mounted again. For details, see  [Upgrading from 2.x or 3.x to 4.x](/docs/installation-and-deployment/upgrading-or-rolling-back-huawei-csi/upgrading-or-rolling-back-huawei-csi-using-helm/upgrading-huawei-csi/upgrading-from-2-x-or-3-x-to-4-x).
>-   During the upgrade or rollback, you cannot use Huawei CSI to create new resources or mount or unmount an existing PVC.
>-   During the upgrade or rollback, do not uninstall the snapshot-dependent component service.




