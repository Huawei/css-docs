---
title: "Creating a VolumeSnapshot"
linkTitle: "Creating a VolumeSnapshot"
description: 
weight: 2
---

In Kubernetes, a  [VolumeSnapshot](https://kubernetes.io/docs/concepts/storage/volume-snapshots/)  is a snapshot of a volume on a storage system. The VolumeSnapshot capability provides Kubernetes users with a standard way to replicate the content of a volume at a specified point in time without creating a volume. For example, this function enables database administrators to back up the database before making changes such as editing or deleting.

This section describes how to create a VolumeSnapshot using Huawei CSI. To create a VolumeSnapshot, perform the following steps:

-   Checking information about volume snapshot-dependent components
-   Configuring a VolumeSnapshotClass
-   Configuring a VolumeSnapshot




