---
title: "Updating a Storage Backend"
linkTitle: "Updating a Storage Backend"
description: 
weight: 3
---

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   PVC provisioning must be based on a configured storage backend. Therefore, if a PVC has been provisioned on a storage backend, do not change the storage backend.
>-   The name uniquely identifies a storage backend. The name of a storage backend with a PVC provisioned cannot be changed.
>-   After a storage backend is modified, the new configuration applies only to volumes to be provisioned.
>-   Do not perform volume management operations during the modification of a storage backend.

## Procedure{#section1223254955011}

1.  Delete the storage backend to be modified. For details, see  [Deleting a Storage Backend](/docs/basic-services/storage-backend-management/managing-storage-backends/deleting-a-storage-backend).
2.  Create a storage backend with the same name. For details, see  [Configuring the Storage Backend](/docs/basic-services/storage-backend-management/configuring-the-storage-backend). The storage backend name cannot be changed.

