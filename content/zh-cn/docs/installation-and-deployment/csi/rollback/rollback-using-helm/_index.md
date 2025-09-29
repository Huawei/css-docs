---
title: "使用Helm回退"
linkTitle: "使用Helm回退"
description: 
weight: 1
---

如果您从2.x和3.x版本的CSI升级至4.9.0版本失败，需要回退时，请参考[使用Helm卸载](/docs/installation-and-deployment/csi/uninstallation/uninstallation-using-helm)卸载CSI，然后下载安装升级之前版本的CSI。

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   在升级/回退过程中，已经存在的PVC/快照/Pod等资源会正常运行，不会影响您的业务访问。
>-   在升级/回退过程中，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。
>-   在升级/回退过程中，请勿卸载Snapshot依赖组件服务。



