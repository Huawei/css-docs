---
title: "Rolling Back Huawei CSI on CCE or CCE Agile"
linkTitle: "Rolling Back Huawei CSI on CCE or CCE Agile"
description: 
weight: 2
---

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   During the upgrade or rollback, the existing resources such as PVCs, snapshots, and Pods will run properly and will not affect your service access.
>-   During the upgrade or rollback, you cannot use Huawei CSI to create new resources or mount or unmount an existing PVC.
>-   During the upgrade or rollback, do not uninstall the snapshot-dependent component service.

## Prerequisites{#en-us_topic_0000001275627010_en-us_topic_0000001232767941_section19453102010152}

You have downloaded the CSI software package of the source version.

## Procedure{#section7449184616111}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Uninstall CSI. For details, see  [Procedure](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-huawei-csi-on-cce-or-cce-agile#section1489941282414).
3.  Reinstall CSI of the source version. For details, see  [Installing Huawei CSI on the CCE or CCE Agile Platform](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-the-cce-or-cce-agile-platform).

