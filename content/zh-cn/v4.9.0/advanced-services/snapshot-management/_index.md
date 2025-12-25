---
title: "快照管理"
linkTitle: "快照管理"
description: 
weight: 1
---

在Kubernetes中，[卷快照（VolumeSnapshot）](https://kubernetes.io/docs/concepts/storage/volume-snapshots/)是一个存储系统上卷的快照。VolumeSnapshot能力为Kubernetes用户提供了一种标准的方式来在指定时间点复制卷的内容，并且不需要创建全新的卷。 例如，这一功能使得数据库管理员能够在执行编辑或删除之类的修改之前对数据库执行备份。

本章将介绍如何使用华为CSI创建VolumeSnapshot。为了完成创建VolumeSnapshot，需要完成如下三步：

-   检查卷快照依赖组件信息
-   配置VolumeSnapshotClass
-   配置VolumeSnapshot

## 前提条件{#section12590411394}

-   支持创建VolumeSnapshot的存储请参考存储自身的[特性表](/docs/compatibility-and-features)，选择对应存储类型和业务类型进行查询。
-   支持创建VolumeSnapshot的Kubernetes版本请参考[表1](/docs/appendix/kubernetes-feature-matrix#table134589135522)。
-   如果您需要在容器环境中使用卷快照以及卷快照关联的特性，请通过[检查卷快照依赖组件](/docs/installation-and-deployment/csi/installation-preparations/checking-volume-snapshot-dependent-components)检查您的环境是否部署了卷快照依赖组件以及卷快照api-versions信息。
-   源PVC存在，且PVC所在的backend支持创建VolumeSnapshot。



