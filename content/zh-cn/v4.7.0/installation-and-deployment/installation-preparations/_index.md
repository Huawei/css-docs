---
title: "安装前准备"
linkTitle: "安装前准备"
description: 
weight: 1
---

本章节将对安装前的准备工作进行详细说明。

## 前提条件{#section7412194016270}

在进行本章节所说明的操作前，请确保如下条件已经具备：

-   容器管理平台已部署完成并正常运行，且兼容性满足[Kubernetes及操作系统兼容性](/docs/compatibility-and-features/kubernetes-and-os-compatibility)章节的要求。
-   （企业存储必选）已完成对接华为企业存储初始化配置，包括存储池划分、端口配置等。且存储产品的版本满足[华为企业存储兼容性](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage)章节的要求。
-   （分布式存储必选）已完成对接华为分布式存储初始化配置，包括存储池划分、端口配置等。且存储产品的版本满足[华为分布式存储兼容性](/docs/compatibility-and-features/compatibility-with-huawei-distributed-storage)章节的要求。
-   完成华为存储和容器平台主机连通性配置，例如运行huawei-csi-controller的worker节点与待接入的存储设备的管理IP地址通信正常，运行huawei-csi-node的worker节点与待接入的存储设备的业务IP地址通信正常，iSCSI场景下允许使用ping命令进行连通性校验。
-   请确保操作系统的语言是英文。
-   请确保存储池、租户名称等相关存储资源名称是英文。








