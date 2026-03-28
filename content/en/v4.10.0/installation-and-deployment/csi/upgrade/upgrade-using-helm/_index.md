---
title: "Upgrade Using Helm"
linkTitle: "Upgrade Using Helm"
description: 
weight: 1
---

This section describes how to upgrade Huawei CSI.

-   To upgrade Huawei CSI from 2._x_  to  4.10.0, uninstall it by referring to the user guide of the earlier version and install Huawei CSI by referring to  [Installation Using Helm](/docs/installation-and-deployment/csi/installation/installation-using-helm).
-   To upgrade Huawei CSI from 2._x_  or 3._x_  to  4.10.0, see  [Upgrading from 2.x or 3.x to 4.x](/docs/installation-and-deployment/csi/upgrade/upgrade-using-helm/upgrading-from-2-x-or-3-x-to-4-x).
-   To upgrade Huawei CSI from 4._x_  to  4.10.0, see  [Upgrading Huawei CSI on Kubernetes, OpenShift, and Tanzu](/docs/installation-and-deployment/csi/upgrade/upgrade-using-helm/upgrading-huawei-csi-on-kubernetes-openshift-and-tanzu).

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   Some CSI 2._x_  versions are unavailable now. If the upgrade fails, CSI may fail to be rolled back to a version which is unavailable now.
>-   After an upgrade from 2._x_, 3._x_, or 4._x_  to  4.10.0, a Pod that has been provisioned in the source version may fail to be mounted again. For details, see  [Upgrading from 2.x or 3.x to 4.x](/docs/installation-and-deployment/csi/upgrade/upgrade-using-helm/upgrading-from-2-x-or-3-x-to-4-x).
>-   During the upgrade or rollback, you cannot use Huawei CSI to create new resources or mount or unmount an existing PVC.
>-   During the upgrade or rollback, do not uninstall the snapshot-dependent component service.
>-   During the upgrade or rollback, the existing resources such as PVCs, snapshots, and Pods will run properly and will not affect your service access.




