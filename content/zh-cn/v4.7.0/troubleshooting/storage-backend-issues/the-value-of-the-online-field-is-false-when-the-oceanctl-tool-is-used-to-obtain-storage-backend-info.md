---
title: "使用oceanctl工具获取存储后端时，ONLINE字段值为false"
linkTitle: "使用oceanctl工具获取存储后端时，ONLINE字段值为false"
description: 
weight: 2
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

执行下列命令，查看存储后端状态：

```
oceanctl get backend
```

存储后端ONLINE字段值为false：

```
NAMESPACE    NAME                  PROTOCOL   STORAGETYPE     SN                     STATUS   ONLINE   Url
huawei-csi   backend-201-nas-nfs   nfs        oceanstor-nas   XXXXXXXXXXXXXX000006   Bound    false    https://192.168.129.157:8088
```

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

CSI使用创建存储后端时输入的账户和密码登录存储后端，若因为下列原因登录失败，则会将ONLINE字段值设置为false：

1.  账户密码错误：该原因可能是在存储侧修改密码后，未在Kubernetes集群侧更新导致。参考下列[解决措施或规避方法](#section155945247573)进行解决。
2.  账户被锁定：该问题请参考[存储侧更新密码后账户被锁定](/docs/troubleshooting/storage-backend-issues/an-account-is-locked-after-the-password-is-updated-on-the-storage-device)解决

## 解决措施或规避方法{#section155945247573}

1.  获取最新的账户密码。
2.  按照[oceanctl更新存储后端密码](/docs/storage-backend-management/managing-storage-backends/updating-a-storage-backend/updating-the-password-of-a-storage-backend-using-oceanctl)所示，更新存储后端密码。

