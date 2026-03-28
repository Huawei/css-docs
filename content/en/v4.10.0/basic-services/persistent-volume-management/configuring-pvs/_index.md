---
title: "Configuring PVs"
linkTitle: "Configuring PVs"
description: 
weight: 1
---

Huawei CSI allows storage resources \(LUNs or file systems\) to be created on Huawei storage and provided for containers based on user settings. For details about the supported features, see  [Compatibility and Features](/docs/compatibility-and-features)  of the storage device.

PV configurations can be classified into configuring dynamic PVs or static PVs, and managing PVs.

-   Configuring dynamic PV does not require a PV to be created in advance. Huawei CSI automatically creates resources required by a PV on storage devices based on a StorageClass. In addition, you can create a PV when creating a PVC.
-   Configuring a static PV requires the administrator to create required resources on a storage device in advance and use existing resources by creating a PV. In addition, you can specify the associated PV when creating a PVC.
-   Managing PVs does not require a PV to be created in advance. You can specify the StorageClass and resource information on the storage device in a PVC. Create the PVC and PV at the same time, and manage all existing storage resources in the cluster.




