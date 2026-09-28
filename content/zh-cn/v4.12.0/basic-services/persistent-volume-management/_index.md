---
title: "持久卷管理"
linkTitle: "持久卷管理"
description: 
weight: 3
---

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   使用华为CSI进行卷管理操作期间，请勿删除存储后端。
>-   在映射block卷时，华为CSI会自动创建创建主机、主机组、LUN组等这些卷映射需要的关联对象，以及映射视图。如果手动在存储上创建了这些对象，会影响华为CSI的映射逻辑，请确保在使用华为CSI映射卷前删除这些对象。
>-   集群中节点的主机名称长度需小于等于27个字符，名称中超长部分会在存储上创建主机时被截断，这可能会导致集群多个节点映射到存储上同一个主机。

根据业务的需求，容器中的文件需要在磁盘上进行持久化。当容器被重建或者重新分配至新的节点时，可以继续使用这些持久化数据。

为了可以将数据持久化到存储设备上，您需要在发放容器时使用[持久卷（PersistentVolume，PV）](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)以及[持久卷申领（PersistentVolumeClaim，PVC）](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)。

-   PV：是Kubernetes集群中的一块存储，可以由管理员事先制备， 或者使用[存储类（StorageClass）](https://kubernetes.io/docs/concepts/storage/storage-classes/)来动态制备。
-   PVC：是用户对存储的请求。PVC会耗用 PV 资源。PVC可以请求特定的大小和访问模式 （例如，可以要求 PV能够以 ReadWriteOnce、ReadOnlyMany 或 ReadWriteMany 模式之一来挂载，参见[访问模式](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)）。

本章将介绍如何使用华为CSI对PV/PVC进行创建、扩容、克隆等操作。



