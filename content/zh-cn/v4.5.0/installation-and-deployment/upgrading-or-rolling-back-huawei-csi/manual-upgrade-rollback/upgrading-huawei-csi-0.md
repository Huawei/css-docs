---
title: "升级华为CSI"
linkTitle: "升级华为CSI"
description: 
weight: 1
---

本章节介绍如何手动升级华为CSI。

升级/回退过程中，已经存在的PVC/快照/Pod等资源会正常运行，不会影响您的业务访问。

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   部分2.x版本CSI已经下架，若升级失败，可能无法回退到已下架版本的CSI。
>-   在升级/回退过程中，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。
>-   在升级/回退过程中，请勿卸载Snapshot依赖组件服务。

## 2.x和3.x版本的CSI升级至4.5.0版本{#section260220843210}

如果您从2.x和3.x版本的CSI升级至4.5.0版本，请按照以下操作步骤升级：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  <a name="li1699321211285"></a>执行命令备份后端信息到configmap.json文件中。OpenShift平台使用**oc**替换**kubectl**命令。

    ```
    kubectl get cm huawei-csi-configmap -n huawei-csi -o json > configmap.json
    ```

3.  参考[手动卸载华为CSI](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/manually-uninstalling-huawei-csi)卸载CSI。
4.  参考[手动安装华为CSI](/v4.5.0/installation-and-deployment/installing-huawei-csi/manually-installing-huawei-csi)安装当前版本的CSI。
5.  将[2](#li1699321211285)中备份的后端信息，按照[管理存储后端](/v4.5.0/storage-backend-management/managing-storage-backends)章节的说明安装。

## 从4.x版本的CSI升级至4.5.0版本。{#section173369363219}

如果您从4.x版本的CSI升级至4.5.0版本，请按照以下操作步骤升级：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  参考[手动卸载华为CSI](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/manually-uninstalling-huawei-csi)卸载CSI。
3.  参考[手动安装华为CSI](/v4.5.0/installation-and-deployment/installing-huawei-csi/manually-installing-huawei-csi)安装当前版本的CSI。

