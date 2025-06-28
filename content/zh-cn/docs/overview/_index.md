---
title: "概述"
linkTitle: "概述"
description: 
weight: 2
---

容器存储接口（[Container Storage Interface](https://github.com/container-storage-interface/spec/blob/master/spec.md#container-storage-interface)），简称 CSI，是一种行业标准，用于将块和文件存储系统暴露给 Kubernetes 等容器编排系统 \(CO\) 上的容器工作负载。华为CSI插件用于和华为企业存储和分布式存储产品进行通信，为Kubernetes的容器工作负载提供存储服务。是华为企业存储和分布式存储在Kubernetes环境中使用的必须插件。

Kubernetes通过其官方维护的一系列sidecar组件负责注册监听Kubernetes对象资源，并在需要的时候通过gRPC发起对CSI Driver调用，华为CSI Driver将sidecar发起的调用在华为存储上实施，如创建一个[持久卷（Persistent Volume，PV）](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)的操作被实施为在华为存储上创建一个LUN/文件系统。Kubernetes、华为CSI以及华为存储的整体结构如下图所示：

**图 1**  CSI整体架构<a name="fig15167123218203"></a>  
![](/css-docs/figures/CSI整体架构.png "CSI整体架构")

华为CSI主要有两大组件，分别为huawei-csi-controller和huawei-csi-node：

-   huawei-csi-controller：包含Controller Service和Identity Service，以Deployment方式运行的一个或多个Pod，主要负责与华为存储交互，使用RESTful方式进行通信，因此运行huawei-csi-controller组件的节点需要连通存储的管理面网络。
-   huawei-csi-node：包含Node Service和Identity Service，以DaemonSet方式运行在Kubernetes工作节点上的Pod，用于在工作节点上对华为存储提供的LUN/文件系统资源进行挂载和卸载等操作，因此运行huawei-csi-node组件的节点需要连通存储的业务面网络。

华为CSI的部署模型如下所示：

**图 2**  CSI部署模型<a name="fig64461013274"></a>  
![](/css-docs/figures/CSI部署模型.png "CSI部署模型")

本文档主要介绍华为CSI V4.8.0插件的安装部署和使用。

