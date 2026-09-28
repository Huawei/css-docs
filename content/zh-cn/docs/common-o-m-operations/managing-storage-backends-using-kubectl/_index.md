---
title: "使用kubectl管理存储后端"
linkTitle: "使用kubectl管理存储后端"
description: 
weight: 11
---

CSI存储后端基于Kubernetes自定义资源（CRD）实现，除使用oceanctl工具外，也可以直接通过kubectl命令对存储后端资源进行管理。存储后端涉及以下两类CRD资源：

-   **StorageBackendClaim**（简称sbc）：命名空间级别资源，表示用户对存储后端的声明。用户通过创建该资源触发CSI控制器自动完成存储后端的接入。
-   **StorageBackendContent**（简称sbct）：集群级别资源，由CSI控制器在StorageBackendClaim绑定成功后自动创建，表示集群中实际存在的存储后端实例。用户不应直接创建或修改该资源。

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>-   使用kubectl管理存储后端前，请确保已安装CSI插件且CRD已正确注册到集群中。
>-   StorageBackendContent由控制器自动管理，请勿直接创建或手动修改，否则可能导致存储后端异常。
>-   正在执行卷管理操作期间，请勿删除存储后端。






