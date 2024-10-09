---
title: "Using Huawei CSI"
linkTitle: "Using Huawei CSI"
description: 
weight: 7
---

This chapter describes how to use Huawei CSI to manage the lifecycle of PVs and snapshots.

>![](/css-docs/public_sys-resources/en/icon-notice.gif) 
>-   Do not delete a storage backend when using Huawei CSI to manage volumes.
>-   When block volumes are mapped, Huawei CSI automatically creates associated objects, such as hosts, host groups, and LUN groups, as well as mapping views. If these objects are manually created on the storage, the mapping logic of Huawei CSI will be affected. Therefore, ensure that these objects are deleted before mapping volumes using Huawei CSI.



