---
title: "创建Pod失败，日志显示执行mount命令失败"
linkTitle: "创建Pod失败，日志显示执行mount命令失败"
description: 
weight: 5
---

## 现象描述{#section16564369537}

NAS场景下，创建Pod时，Pod一直处于ContainerCreating状态，此时查看huawei-csi-node的日志信息（详情请参考[如何查看华为CSI日志](/v4.5.0/common-operations/collecting-information/viewing-huawei-csi-logs)），日志显示执行mount命令失败。

## 根因分析{#section135642617536}

该问题可能由于存储侧未开启NFS 4.0/4.1/4.2协议，主机在使用NFS v4协议挂载失败后，未进行协商使用NFS v3协议挂载。

## 解决措施或规避方法{#section75642613539}

-   开启存储侧的NFS 3/4.0/4.1/4.2协议，重新尝试默认挂载。
-   直接指定可用的NFS协议进行挂载，参考[动态卷供应典型场景StorageClass配置示例](/v4.5.0/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/storageclass-configuration-examples-in-typical-dynamic-volume-provisioning-scenarios)。

