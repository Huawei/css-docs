---
title: "PVC管理"
linkTitle: "PVC管理"
description: 
weight: 1
---

根据业务的需求，容器中的文件需要在磁盘上进行持久化。当容器被重建或者重新分配至新的节点时，可以继续使用这些持久化数据。

为了可以将数据持久化到存储设备上，您需要在发放容器时使用[持久卷（PersistentVolume，PV）](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)以及[持久卷申领（PersistentVolumeClaim，PVC）](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)。

-   PV：是Kubernetes集群中的一块存储，可以由管理员事先制备， 或者使用[存储类（StorageClass）](https://kubernetes.io/docs/concepts/storage/storage-classes/)来动态制备。
-   PVC：是用户对存储的请求。PVC会耗用 PV 资源。PVC可以请求特定的大小和访问模式 （例如，可以要求 PV能够以 ReadWriteOnce、ReadOnlyMany 或 ReadWriteMany 模式之一来挂载，参见[访问模式](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)）。

本章将介绍如何使用华为CSI对PV/PVC进行创建、扩容、克隆以及从快照创建PVC。





