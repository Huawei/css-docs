---
title: "配置卷快照"
linkTitle: "配置卷快照"
description: 
weight: 2
---

配置卷快照的方式按类型可分为动态制备卷快照和预制备卷快照。

-   动态制备卷快照通过创建VolumeSnapshot资源，从PVC中动态获取并创建快照，而不用使用已经存在的快照。
-   预制备卷快照需要管理员事先在存储设备上创建好所需要的快照，通过创建VolumeSnapshotContent的方式使用已存在的快照。并且可以在创建VolumeSnapshot时指定关联的VolumeSnapshotContent。



