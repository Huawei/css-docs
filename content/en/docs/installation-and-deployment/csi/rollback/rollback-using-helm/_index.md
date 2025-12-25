---
title: "Rollback Using Helm"
linkTitle: "Rollback Using Helm"
description: 
weight: 1
---

If CSI fails to be upgraded from 2._x_  or 3._x_  to  4.10.0  and needs to be rolled back, uninstall CSI by referring to  [Uninstallation Using Helm](/docs/installation-and-deployment/csi/uninstallation/uninstallation-using-helm)  and then download and install CSI of the source version.

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   During the upgrade or rollback, the existing resources such as PVCs, snapshots, and Pods will run properly and will not affect your service access.
>-   During the upgrade or rollback, you cannot use Huawei CSI to create new resources or mount or unmount an existing PVC.
>-   During the upgrade or rollback, do not uninstall the snapshot-dependent component service.



