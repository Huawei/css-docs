---
title: "创建PVC"
linkTitle: "创建PVC"
description: 
weight: 1
---

华为CSI支持在华为存储上创建存储资源（LUN/文件系统），并根据用户的设置供给容器使用。具体支持的特性请参考[表2](/v4.5.0/compatibility-and-features/compatibility-with-huawei-enterprise-storage#table14995183994515)或者[表2](/v4.5.0/compatibility-and-features/compatibility-with-huawei-distributed-storage#table175022559255)。

创建PVC的方式分为动态卷供应和静态卷供应。

-   动态卷供应不需要事先创建PV，华为CSI会根据StorageClass自动在存储设备上创建PV所需要的资源。并且可以在创建PVC时同时创建PV。
-   静态卷供应需要管理员事先在存储设备上创建好所需要的资源，通过创建PV的方式使用已存在的资源。并且可以在创建PVC时指定关联的PV。




