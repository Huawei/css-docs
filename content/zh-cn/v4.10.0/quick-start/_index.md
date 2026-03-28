---
title: "快速开始"
linkTitle: "快速开始"
description: 
weight: 3
---

本章节说明如何快速上手安装并使用华为CSI管理PVC。

## 华为CSI使用流程概览{#section10356165115616}

**图 1**  CSI安装及使用流程图<a name="fig111116220210"></a>  
![](/css-docs/figures/CSI安装及使用流程图.png "CSI安装及使用流程图")

## 兼容性和特性{#section17589135519713}

使用前请先了解对接的华为存储、容器平台和主机操作系统相关的兼容性以及支持的特性，具体请参考[兼容性和特性](/docs/compatibility-and-features)。

## 安装前准备{#section1698093774519}

安装华为CSI前，需要对容器平台、主机等环境做相关配置准备，参考[安装前准备](/docs/installation-and-deployment/csi/installation-preparations)。

## 安装部署{#section48621535144915}

华为CSI提供了Helm和手动安装两种安装方式，并适用于包含Kubernetes、OpenShift等不同的容器平台，参考[安装部署](/docs/installation-and-deployment)。

## 创建存储后端{#section18261514524}

在使用华为CSI前，需要先创建存储后端资源，参考[配置存储后端](/docs/basic-services/storage-backend-management/configuring-the-storage-backend)。

## 使用华为CSI{#section1855354751020}

现在，您可以开始使用华为CSI进行PVC管理了，参考[配置存储类](/docs/basic-services/storageclass-management/configuring-a-storageclass)，[配置持久卷](/docs/basic-services/persistent-volume-management/configuring-pvs)。

