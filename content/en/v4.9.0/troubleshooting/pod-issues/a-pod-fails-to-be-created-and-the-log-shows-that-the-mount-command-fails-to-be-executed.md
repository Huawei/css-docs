---
title: "A Pod Fails to Be Created and the Log Shows That the mount Command Fails to Be Executed"
linkTitle: "A Pod Fails to Be Created and the Log Shows That the mount Command Fails to Be Executed"
description: 
weight: 5
---

## Symptom{#section16564369537}

In NAS scenarios, when a Pod is being created, the Pod keeps in the  **ContainerCreating**  status. In this case, check the log information of huawei-csi-node \(for details, see  [Viewing Huawei CSI Logs](/docs/common-o-m-operations/collecting-information/viewing-huawei-csi-logs)\). The log shows that the mount command fails to be executed.

## Root Cause Analysis{#section135642617536}

The possible cause is that the NFS 4.0/4.1/4.2 protocol is not enabled on the storage side. After the NFS v4 protocol fails to be used for mounting, the host does not negotiate to use the NFS v3 protocol for mounting.

## Solution or Workaround{#section75642613539}

-   Enable the NFS 3/4.0/4.1/4.2 protocol on the storage side and retry the default mounting.
-   Specify an available NFS protocol for mounting. For details, see  [Configuring a StorageClass](/docs/basic-services/storageclass-management/configuring-a-storageclass).

