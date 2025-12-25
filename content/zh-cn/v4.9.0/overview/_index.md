---
title: "概述"
linkTitle: "概述"
description: 
weight: 2
---

容器存储接口（[Container Storage Interface](https://github.com/container-storage-interface/spec/blob/master/spec.md#container-storage-interface)），简称 CSI，是一种行业标准协议，用于对接Kubernetes等容器平台与底层存储系统。华为CSI插件作为必备组件，实现华为企业存储和分布式存储产品与Kubernetes集群的对接，为容器工作负载提供持久化存储服务。

Kubernetes通过其官方维护的一系列sidecar组件负责注册监听Kubernetes对象资源，并调用CSI驱动程序，触发华为存储的物理操作。如创建一个[持久卷（Persistent Volume，PV）](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)时，华为CSI驱动会在存储设备中创建对应的LUN（块存储）或文件系统。Kubernetes、华为CSI以及华为存储的整体结构如[图1](#fig15167123218203)所示：

**图 1**  CSI整体架构<a name="fig15167123218203"></a>  
![](/css-docs/figures/CSI整体架构.png "CSI整体架构")

华为CSI主要有两大组件，分别为huawei-csi-controller和huawei-csi-node：

-   huawei-csi-controller：包含Controller Service和Identity Service，以Deployment方式运行的一个或多个Pod，主要负责与华为存储交互，使用RESTful方式进行通信，因此运行huawei-csi-controller组件的节点需要连通存储的管理面网络。
-   huawei-csi-node：包含Node Service和Identity Service，以DaemonSet方式运行在Kubernetes工作节点上的Pod，用于在工作节点上对华为存储提供的LUN/文件系统资源进行挂载和卸载等操作，因此运行huawei-csi-node组件的节点需要连通存储的业务面网络。

华为CSI的部署模型如[图2](#fig64461013274)所示：

**图 2**  CSI部署模型<a name="fig64461013274"></a>  
![](/css-docs/figures/CSI部署模型.png "CSI部署模型")

本文档主要介绍华为CSI V4.9.0插件的安装部署和使用。

