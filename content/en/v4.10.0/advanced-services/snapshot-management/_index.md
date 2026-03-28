---
title: "Snapshot Management"
linkTitle: "Snapshot Management"
description: 
weight: 1
---

In Kubernetes, a  [VolumeSnapshot](https://kubernetes.io/docs/concepts/storage/volume-snapshots/)  is a snapshot of a volume on a storage system. The VolumeSnapshot capability provides Kubernetes users with a standard way to replicate the content of a volume at a specified point in time without creating a volume. For example, this function enables database administrators to back up the database before making changes such as editing or deleting.

This section describes how to create a VolumeSnapshot using Huawei CSI. To create a VolumeSnapshot, perform the following steps:

-   Checking information about volume snapshot-dependent components
-   Configuring a VolumeSnapshotClass
-   Configuring a VolumeSnapshot

## Prerequisites{#section12590411394}

-   [Compatibility and Features](/docs/compatibility-and-features)  lists storage that support VolumeSnapshot creation. You need to search by the storage type and service type.
-   For details about the Kubernetes versions that support VolumeSnapshot creation, see  [Table 1](/docs/appendix/kubernetes-feature-matrix#table134589135522).
-   If you need to use volume snapshots and features associated with volume snapshots in the container environment, perform the operations in  [Checking Volume Snapshot-Dependent Components](/docs/installation-and-deployment/csi/installation-preparations/checking-volume-snapshot-dependent-components)  to check whether volume snapshot-dependent components have been deployed in your environment and check the api-versions information about volume snapshots.
-   The source PVC exists, and the backend where the PVC resides supports VolumeSnapshot creation.



