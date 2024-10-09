---
title: "使用华为CSI"
linkTitle: "使用华为CSI"
description: 
weight: 7
---

本章节主要介绍如何使用华为CSI对PV、快照的生命周期进行管理。

>![](/css-docs/public_sys-resources/zh/icon-notice.gif)  
>-   使用华为CSI进行卷管理操作期间，请勿删除存储后端。
>-   在映射block卷时，华为CSI会自动创建创建主机、主机组、LUN组等这些卷映射需要的关联对象，以及映射视图。如果手动在存储上创建了这些对象，会影响华为CSI的映射逻辑，请确保在使用华为CSI映射卷前删除这些对象。



