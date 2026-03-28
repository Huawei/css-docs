---
title: "PVC扩容的目标容量超过存储池容量导致扩容失败"
linkTitle: "PVC扩容的目标容量超过存储池容量导致扩容失败"
description: 
weight: 4
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

在低于1.23版本的Kubernetes环境中，对PVC进行扩容，当目标容量超过存储池容量时，扩容失败。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

Kubernetes社区已知问题，详情请参考[处理扩充卷过程中的失败](https://kubernetes.io/zh-cn/docs/concepts/storage/persistent-volumes/#recovering-from-failure-when-expanding-volumes)。

## 解决措施或规避方法{#section1730118471221}

参考[处理扩充卷过程中的失败](https://kubernetes.io/zh-cn/docs/concepts/storage/persistent-volumes/#recovering-from-failure-when-expanding-volumes)。

