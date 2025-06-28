---
title: "Creating a PVC"
linkTitle: "Creating a PVC"
description: 
weight: 1
---

Huawei CSI allows storage resources \(LUNs or file systems\) to be created on Huawei storage and provided for containers based on user settings. For details about the supported features, see  [Table 2](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage#table14995183994515)  or  [Table 2](/docs/compatibility-and-features/compatibility-with-huawei-distributed-storage#table175022559255).

A PVC can be created in dynamic volume provisioning or static volume provisioning mode.

-   Dynamic volume provisioning does not require a PV to be created in advance. Huawei CSI automatically creates resources required by a PV on storage devices based on a StorageClass. In addition, you can create a PV when creating a PVC.
-   Static volume provisioning requires the administrator to create required resources on a storage device in advance and use existing resources by creating a PV. In addition, you can specify the associated PV when creating a PVC.




