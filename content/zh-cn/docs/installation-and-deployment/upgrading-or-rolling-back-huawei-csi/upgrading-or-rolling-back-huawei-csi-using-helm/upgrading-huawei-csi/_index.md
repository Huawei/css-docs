---
title: "升级华为CSI"
linkTitle: "升级华为CSI"
description: 
weight: 1
---

本章节介绍如何升级华为CSI。

如果您从2.x版本升级至4.6.0版本，请参考旧版本用户指南卸载CSI，然后参考[使用Helm安装华为CSI](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm)章节安装华为CSI。

如果您从2.x或3.x版本升级至4.6.0版本，请参考[从2.x或3.x升级至4.x版本](/docs/installation-and-deployment/upgrading-or-rolling-back-huawei-csi/upgrading-or-rolling-back-huawei-csi-using-helm/upgrading-huawei-csi/upgrading-from-2-x-or-3-x-to-4-x)章节升级华为CSI。

如果您从4.x版本升级至4.6.0版本，请参考[Kubernetes、OpenShift、Tanzu升级华为CSI](/docs/installation-and-deployment/upgrading-or-rolling-back-huawei-csi/upgrading-or-rolling-back-huawei-csi-using-helm/upgrading-huawei-csi/upgrading-huawei-csi-on-kubernetes-openshift-and-tanzu)章节升级华为CSI。

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   部分2.x版本CSI已经下架，若升级失败，可能无法回退到已下架版本的CSI。
>-   从2.x或3.x版本或4.x版本升级至4.6.0版本，可能存在旧版本已发放Pod重新挂载时失败的问题，具体请参考[从2.x或3.x升级至4.x版本](/docs/installation-and-deployment/upgrading-or-rolling-back-huawei-csi/upgrading-or-rolling-back-huawei-csi-using-helm/upgrading-huawei-csi/upgrading-from-2-x-or-3-x-to-4-x)
>-   在升级/回退过程中，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。
>-   在升级/回退过程中，请勿卸载Snapshot依赖组件服务。
>-   升级/回退过程中，已经存在的PVC/快照/Pod等资源会正常运行，不会影响您的业务访问。




