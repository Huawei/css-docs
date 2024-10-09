---
title: "Kubernetes平台第一次搭建时， iscsi\_tcp服务没有正常启动，导致创建Pod失败"
linkTitle: "Kubernetes平台第一次搭建时， iscsi\_tcp服务没有正常启动，导致创建Pod失败"
description: 
weight: 9
---

## 现象描述{#zh-cn_topic_0234872004_section1566717121452}

创建Pod时报错，在/var/log/huawei-csi-node日志中报错“ Cannot connect ISCSI portal \*.\*.\*.\*: libkmod: kmod\_module\_insert\_module: could not find module by name='iscsi\_tcp'。

## 根因分析{#zh-cn_topic_0234872004_section1425013451056}

搭建Kubernete和安装iSCSI服务后， iscsi\_tcp服务可能会被停掉，可通过执行以下命令查看服务是否被停掉。

```
lsmod | grep iscsi | grep iscsi_tcp
```

命令结果示例如下。

```
iscsi_tcp              18333  6 
libiscsi_tcp           25146  1 iscsi_tcp
libiscsi               57233  2 libiscsi_tcp,iscsi_tcp
scsi_transport_iscsi    99909  3 iscsi_tcp,libiscsi
```

## 解决措施或规避方法{#zh-cn_topic_0234872004_section350653016492}

执行以下命令，手动加载iscsi\_tcp服务。

```
modprobe iscsi_tcp
lsmod | grep iscsi | grep iscsi_tcp
```

