---
title: "回退华为CSI"
linkTitle: "回退华为CSI"
description: 
weight: 2
---

如果您从2.x和3.x版本的CSI升级至4.5.0版本失败，需要回退时，请参考[Helm卸载华为CSI](/docs/安装部署/卸载华为CSI/Helm卸载华为CSI)卸载CSI，然后下载安装升级之前版本的CSI。

>![](/css-docs/public_sys-resources/zh/icon-notice.gif)  
>-   在升级/回退过程中，已经存在的PVC/快照/Pod等资源会正常运行，不会影响您的业务访问。
>-   在升级/回退过程中，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。
>-   在升级/回退过程中，请勿卸载Snapshot依赖组件服务。



