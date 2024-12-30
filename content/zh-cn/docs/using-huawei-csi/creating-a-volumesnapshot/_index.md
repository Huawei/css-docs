---
title: "创建VolumeSnapshot"
linkTitle: "创建VolumeSnapshot"
description: 
weight: 2
---

在Kubernetes中，[卷快照（VolumeSnapshot）](https://kubernetes.io/docs/concepts/storage/volume-snapshots/)是一个存储系统上卷的快照。VolumeSnapshot能力为Kubernetes用户提供了一种标准的方式来在指定时间点复制卷的内容，并且不需要创建全新的卷。 例如，这一功能使得数据库管理员能够在执行编辑或删除之类的修改之前对数据库执行备份。

本章将介绍如何使用华为CSI创建VolumeSnapshot。为了完成创建VolumeSnapshot，需要完成如下三步：

-   检查卷快照依赖组件信息
-   配置VolumeSnapshotClass
-   配置VolumeSnapshot




