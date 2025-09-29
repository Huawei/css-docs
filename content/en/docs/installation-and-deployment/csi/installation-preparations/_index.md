---
title: "Installation Preparations"
linkTitle: "Installation Preparations"
description: 
weight: 1
---

This chapter describes the preparations for the installation.

## Prerequisites{#section7412194016270}

-   The container management platform has been deployed and is running properly. The container platform compatibility requirements in  [Compatibility and Features](/docs/compatibility-and-features)  are met.
-   \(Mandatory for enterprise storage\) Initial configuration for interconnecting with Huawei enterprise storage has been completed, including storage pool division and port configuration. The version of the storage product meets the requirements in  [Compatibility and Features](/docs/compatibility-and-features).
-   \(Mandatory for distributed storage\) Initial configuration for interconnecting with Huawei distributed storage has been completed, including storage pool division and port configuration. The version of the storage product meets the requirements in  [Compatibility and Features](/docs/compatibility-and-features).
-   The connectivity between Huawei storage and the container platform host has been configured. For example, the worker node running huawei-csi-controller communicates properly with the management IP address of the storage device to be connected, and the worker node running huawei-csi-node communicates properly with the service IP address of the storage device to be connected. In iSCSI scenarios, the  **ping**  command can be used to verify the connectivity.
-   Ensure that the language of the operating system is English.
-   Ensure that storage resource names, such as storage pool names and tenant names, are in English.








