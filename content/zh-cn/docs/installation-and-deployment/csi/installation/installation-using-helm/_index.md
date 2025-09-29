---
title: "使用Helm安装"
linkTitle: "使用Helm安装"
description: 
weight: 1
---

本章节介绍如何使用Helm 3安装部署华为CSI。

## Helm安装说明{#section16991437124819}

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   华为CSI的安装支持root用户和非root用户。使用非root用户安装华为CSI时，需要保证当前用户能够访问Kubernetes集群的API Server，配置非root用户访问Kubernetes集群请参考[配置非root用户访问Kubernetes集群](/docs/common-o-m-operations/configuring-access-to-the-kubernetes-cluster-as-a-non-root-user)。
>-   华为CSI必须在root用户权限下运行。

Helm是Kubernetes生态系统中的一个软件包管理工具，类似Ubuntu的APT、CentOS的YUM、或Python的pip一样，专门负责管理Kubernetes的应用资源。

使用Helm可以对Kubernetes应用进行统一打包、分发、安装、升级以及回退等操作。

-   Helm的获取、安装请参考：[https://helm.sh/docs/intro/install/](https://helm.sh/docs/intro/install/)
-   Helm与Kubernetes版本对应关系请参考：[https://helm.sh/docs/topics/version\_skew/](https://helm.sh/docs/topics/version_skew/)

Helm在安装huawei-csi-controller时，将在指定命名空间的Deployment类型的工作负载中部署以下组件：

-   huawei-csi-driver：华为CSI驱动。
-   storage-backend-controller：华为后端管理控制器，管理storageBackendClaim资源。
-   storage-backend-sidecar：用于管理storageBackendContent资源。
-   Kubernetes External Provisioner：用于提供/删除卷。
-   Kubernetes External Attacher：用于挂载/解挂载卷。
-   Kubernetes External Resizer：用于扩容卷。
-   Kubernetes External liveness-probe： 用来判断Pod健康状态。
-   （可选）huawei-csi-extender：华为CSI扩展。
-   （可选）Kubernetes External Snapshotter：提供快照支持（作为CRD安装）。
-   （可选）Kubernetes External Snapshot Controller ：用于卷快照控制。

Helm在安装huawei-csi-node时，将在指定命名空间的DaemonSet类型的工作负载中部署以下组件：

-   huawei-csi-driver：华为CSI驱动。
-   Kubernetes Node Registrar：处理驱动程序注册。
-   liveness-probe: 用来判断Pod健康状态。




