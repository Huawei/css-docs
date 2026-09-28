---
title: "Configuring a VolumeSnapshot"
linkTitle: "Configuring a VolumeSnapshot"
description: 
weight: 2
---

VolumeSnapshot configurations can be classified into dynamically provisioned VolumeSnapshots and pre-provisioned VolumeSnapshots.

-   A dynamically provisioned VolumeSnapshot is created by using VolumeSnapshot resources to dynamically obtain and create a snapshot from PVCs, without using existing snapshots.
-   A pre-provisioned VolumeSnapshot requires the administrator to create the required snapshot on the storage device in advance and use the existing snapshot by creating a VolumeSnapshotContent. In addition, you can specify the associated VolumeSnapshotContent when creating a VolumeSnapshot.



