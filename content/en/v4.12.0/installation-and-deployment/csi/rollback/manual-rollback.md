---
title: "Manual Rollback"
linkTitle: "Manual Rollback"
description: 
weight: 2
---

Uninstall CSI by referring to  [Manual Uninstallation](/docs/installation-and-deployment/csi/uninstallation/manual-uninstallation), and then download and install CSI of the source version.

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   During the upgrade or rollback, the existing resources such as PVCs, snapshots, and Pods will run properly and will not affect your service access.
>-   During the upgrade or rollback, you cannot use Huawei CSI to create new resources or mount or unmount an existing PVC.
>-   During the upgrade or rollback, do not uninstall the snapshot-dependent component service.

## Prerequisites{#en-us_topic_0000001275627010_en-us_topic_0000001232767941_section19453102010152}

You have downloaded the CSI software package of the source version.

## Procedure{#section7449184616111}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Uninstall CSI. For details, see  [Manual Uninstallation](/docs/installation-and-deployment/csi/uninstallation/manual-uninstallation).
3.  Reinstall CSI of the source version. For details, see  [Manual Installation](/docs/installation-and-deployment/csi/installation/manual-installation).

