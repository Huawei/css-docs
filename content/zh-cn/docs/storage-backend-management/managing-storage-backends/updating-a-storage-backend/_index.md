---
title: "更新存储后端"
linkTitle: "更新存储后端"
description: 
weight: 3
---

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   当前使用oceanctl更新存储后端信息时，仅支持更新存储后端密码。
>-   若在存储侧更新了后端的账号密码，CSI插件会因登录失败而重试，可能会导致账号被锁定。如果账号被锁定，请参考[存储侧更新密码后账户被锁定](/docs/troubleshooting/storage-backend-issues/the-value-of-the-online-field-is-false-when-the-oceanctl-tool-is-used-to-obtain-storage-backend-info)章节修改。



