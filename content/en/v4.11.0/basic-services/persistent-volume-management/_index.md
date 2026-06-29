---
title: "Persistent Volume Management"
linkTitle: "Persistent Volume Management"
description: 
weight: 3
---

Based on service requirements, files in containers need to be persistently stored on disks. When the containers are re-built or re-allocated to new nodes, the persistent data can still be used.

To persistently store data on storage devices, you need to use the  [PersistentVolume \(PV\)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)  and  [PersistentVolumeClaim \(PVC\)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)  when provisioning containers.

-   PV: a piece of storage in the Kubernetes cluster that has been provisioned by an administrator or dynamically provisioned using a  [StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/).
-   PVC: a request for storage by a user. A PVC consumes PV resources. A PVC can request specific size and access modes. For example, a PV can be mounted in ReadWriteOnce, ReadOnlyMany, or ReadWriteMany mode. For details, see  [Access Modes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes).

This section describes how to use Huawei CSI to create, clone, and expand the capacity of a PV and PVC.



