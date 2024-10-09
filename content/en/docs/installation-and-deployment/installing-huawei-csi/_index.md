---
title: "Installing Huawei CSI"
linkTitle: "Installing Huawei CSI"
description: 
weight: 2
---

This section describes how to install Huawei CSI.

>![](/public_sys-resources/en/icon-note.gif)
>In the current version, resource requests and limits are added to Huawei CSI. For details, see  [Huawei CSI Resource Management](/docs/appendix/huawei-csi-resource-management).

## Prerequisites{#en-us_topic_0000001324610777_section19453102010152}

-   Operations described in  [Installation Preparations](/docs/installation-and-deployment/installation-preparations)  have been completed.
-   All worker nodes of the cluster communicate properly with the service network of the storage device to be connected. In iSCSI scenarios, the  **ping**  command can be used to verify the connectivity.
-   Software clients required by the corresponding protocol, such as iSCSI and NFS clients, have been installed on all worker nodes of the cluster.



