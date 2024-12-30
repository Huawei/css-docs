---
title: "创建Pod时，Pod的状态长时间处于ContainerCreating状态"
linkTitle: "创建Pod时，Pod的状态长时间处于ContainerCreating状态"
description: 
weight: 3
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

创建Pod时，Pod长时间处于ContainerCreating状态，此时查看huawei-csi-node的日志信息（详情请参考[如何查看华为CSI日志](/v4.5.0/common-operations/collecting-information/viewing-huawei-csi-logs)），huawei-csi-node的日志中无创建Pod的日志记录，执行**kubectl get volumeattachment**命令后，PV列无该Pod使用的PV名称。在等待较长时间后（超过十分钟），Pod正常创建，Pod状态变为Running状态。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

该问题是因为Kubernetes的kube-controller-manager组件服务异常导致。

## 解决措施或规避方法{#zh-cn_topic_0000001279996521_section164471213145410}

请联系容器平台侧工程师解决。

