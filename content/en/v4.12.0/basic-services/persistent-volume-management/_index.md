---
title: "Persistent Volume Management"
linkTitle: "Persistent Volume Management"
description: 
weight: 3
---

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   Do not delete a storage backend when using Huawei CSI to manage volumes.
>-   When block volumes are mapped, Huawei CSI automatically creates associated objects, such as hosts, host groups, and LUN groups, as well as mapping views. If these objects are manually created on the storage, the mapping logic of Huawei CSI will be affected. Therefore, ensure that these objects are deleted before mapping volumes using Huawei CSI.
>-   The host name of a node in the cluster must contain no more than 27 characters. The extra part will be truncated when the host is created on the storage device. As a result, multiple nodes in the cluster may be mapped to the same host on the storage device.

Based on service requirements, files in containers need to be persistently stored on disks. When the containers are re-built or re-allocated to new nodes, the persistent data can still be used.

To persistently store data on storage devices, you need to use the  [PersistentVolume \(PV\)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)  and  [PersistentVolumeClaim \(PVC\)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)  when provisioning containers.

-   PV: a piece of storage in the Kubernetes cluster that has been provisioned by an administrator or dynamically provisioned using a  [StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/).
-   PVC: a request for storage by a user. A PVC consumes PV resources. A PVC can request specific size and access modes. For example, a PV can be mounted in ReadWriteOnce, ReadOnlyMany, or ReadWriteMany mode. For details, see  [Access Modes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes).

This section describes how to use Huawei CSI to create, clone, and expand the capacity of a PV and PVC.



