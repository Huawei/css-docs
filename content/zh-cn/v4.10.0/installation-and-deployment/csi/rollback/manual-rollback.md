---
title: "手动回退"
linkTitle: "手动回退"
description: 
weight: 2
---

请参考[手动卸载](/docs/installation-and-deployment/csi/uninstallation/manual-uninstallation)卸载CSI，然后下载安装升级之前版本的CSI。

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   在升级/回退过程中，已经存在的PVC/快照/Pod等资源会正常运行，不会影响您的业务访问。
>-   在升级/回退过程中，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。
>-   在升级/回退过程中，请勿卸载Snapshot依赖组件服务。

## 前提条件{#zh-cn_topic_0000001275627010_zh-cn_topic_0000001232767941_section19453102010152}

已下载原版本CSI的软件包。

## 操作步骤{#section7449184616111}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  参考[手动卸载](/docs/installation-and-deployment/csi/uninstallation/manual-uninstallation)卸载CSI。
3.  参考[手动安装](/docs/installation-and-deployment/csi/installation/manual-installation)重新安装原版本的CSI。

