---
title: "Installation Preparations"
linkTitle: "Installation Preparations"
description: 
weight: 1
---

This chapter describes the preparations for the installation.

## Prerequisites{#section7412194016270}

Before performing the operations described in this chapter, ensure that the following conditions are met:

-   A container management platform has been deployed and is running properly, and its compatibility meets the requirements described in  [Kubernetes and OS Compatibility](/docs/compatibility-and-features/kubernetes-and-os-compatibility).
-   \(Mandatory for enterprise storage\) Initial configuration for interconnecting with Huawei enterprise storage has been completed, including storage pool division and port configuration. The version of the storage product meets the requirements in  [Compatibility with Huawei Enterprise Storage](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage).
-   \(Mandatory for distributed storage\) Initial configuration for interconnecting with Huawei distributed storage has been completed, including storage pool division and port configuration. The version of the storage product meets the requirements in  [Compatibility with Huawei Distributed Storage](/docs/compatibility-and-features/compatibility-with-huawei-distributed-storage).
-   The connectivity between Huawei storage and the container platform host has been configured. For example, the worker node running huawei-csi-controller communicates properly with the management IP address of the storage device to be connected, and the worker node running huawei-csi-node communicates properly with the service IP address of the storage device to be connected. In iSCSI scenarios, the  **ping**  command can be used to verify the connectivity.
-   Ensure that the language of the operating system is English.
-   Ensure that storage resource names, such as storage pool names and tenant names, are in English.








