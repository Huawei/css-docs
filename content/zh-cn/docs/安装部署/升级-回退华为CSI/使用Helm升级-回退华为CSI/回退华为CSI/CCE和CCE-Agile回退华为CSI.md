---
title: "CCE和CCE Agile回退华为CSI"
linkTitle: "CCE和CCE Agile回退华为CSI"
description: 
weight: 2
---

>![](/public_sys-resources/zh/icon-notice.gif)  
>-   在升级/回退过程中，已经存在的PVC/快照/Pod等资源会正常运行，不会影响您的业务访问。
>-   在升级/回退过程中，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。
>-   在升级/回退过程中，请勿卸载Snapshot依赖组件服务。

## 前提条件{#zh-cn_topic_0000001275627010_zh-cn_topic_0000001232767941_section19453102010152}

已下载原版本CSI的软件包。

## 操作步骤{#section7449184616111}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  参考[操作步骤](/docs/安装部署/卸载华为CSI/Helm卸载华为CSI/CCE和CCE-Agile卸载华为CSI#section1489941282414)卸载CSI。
3.  参考[CCE和CCE Agile平台安装华为CSI](/docs/安装部署/安装华为CSI/使用Helm安装华为CSI/CCE和CCE-Agile平台安装华为CSI)重新安装原版本的CSI。

