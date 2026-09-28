---
title: "更新存储后端信息"
linkTitle: "更新存储后端信息"
description: 
weight: 3
---

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>-   PVC发放需要基于已配置的存储后端，因此当存储后端已经发放PVC时，请勿随便修改存储后端。
>-   名称是存储后端的唯一标识，已发放PVC的存储后端不允许修改名称。
>-   存储后端修改后，新增配置仅作用于新发放的卷。
>-   存储后端修改期间，请勿执行卷管理操作。

## 操作步骤{#section1223254955011}

1.  参考[删除存储后端](/docs/basic-services/storage-backend-management/managing-storage-backends/deleting-a-storage-backend)章节，删除待修改存储后端。
2.  参考[配置存储后端](/docs/basic-services/storage-backend-management/configuring-the-storage-backend)章节，创建同名存储后端，存储后端名称不可变更。

