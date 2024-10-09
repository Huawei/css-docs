---
title: "Overview"
linkTitle: "Overview"
description: 
weight: 2
---

[Container Storage Interface](https://github.com/container-storage-interface/spec/blob/master/spec.md#container-storage-interface)  \(CSI\) is an industry standard used to expose block and file storage systems to container workloads on container orchestration systems \(COs\) such as Kubernetes. Huawei CSI plug-in is used to communicate with Huawei enterprise storage and distributed storage products and provide storage services for Kubernetes container workloads. It is a mandatory plug-in used by Huawei enterprise storage and distributed storage in the Kubernetes environment.

Kubernetes uses a series of officially maintained sidecar components to register and listen to Kubernetes object resources and call CSI Driver through gRPC when necessary. Huawei CSI Driver implements the call initiated by sidecar on Huawei storage, for example, creating a  [Persistent Volume \(PV\)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)  is to create a LUN or file system on Huawei storage. The following figure shows the overall structure of Kubernetes, Huawei CSI, and Huawei storage.

**Figure  1**  CSI overall architecture<a name="fig15167123218203"></a>  
![](/figures/csi-overall-architecture.png "csi-overall-architecture")

Huawei CSI consists of two components: huawei-csi-controller and huawei-csi-node.

-   huawei-csi-controller: one or more Pods \(including Controller Service and Identity Service\) running in Deployment mode. It is used to interact with Huawei storage using RESTful. Therefore, the node running the huawei-csi-controller component must be connected to the management plane network of the storage.
-   huawei-csi-node: a Pod \(including Node Service and Identity Service\) that runs on Kubernetes worker nodes in DaemonSet mode. It is used to mount and unmount a LUN/file system provided by Huawei storage on worker nodes. Therefore, the node running the huawei-csi-node component must be connected to the service plane network of the storage.

The following figure shows the deployment model of Huawei CSI.

**Figure  2**  CSI deployment model<a name="fig64461013274"></a>  
![](/figures/csi-deployment-model.png "csi-deployment-model")

This document describes how to install, deploy, and use the Huawei CSI V4.5.0  plug-in.

