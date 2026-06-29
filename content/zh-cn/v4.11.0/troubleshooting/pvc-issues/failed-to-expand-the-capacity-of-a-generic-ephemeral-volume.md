---
title: "通用临时卷扩容失败"
linkTitle: "通用临时卷扩容失败"
description: 
weight: 3
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

在Kubernetes版本低于1.25环境中，对LUN类型的[通用临时卷](https://kubernetes.io/docs/concepts/storage/ephemeral-volumes/#generic-ephemeral-volumes)扩容失败，显示PV已经扩容，但PVC未成功更新容量。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

该问题是由Kubernetes的[bug](https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG/CHANGELOG-1.25.md)导致，Kubernetes在1.25版本中修复了该问题。

