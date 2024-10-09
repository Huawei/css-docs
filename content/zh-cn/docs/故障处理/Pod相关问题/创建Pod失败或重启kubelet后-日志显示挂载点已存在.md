---
title: "创建Pod失败或重启kubelet后，日志显示挂载点已存在"
linkTitle: "创建Pod失败或重启kubelet后，日志显示挂载点已存在"
description: 
weight: 7
---

## 现象描述{#section16564369537}

创建Pod时，Pod一直处于ContainerCreating状态，或者重启kubelet后，日志中显示挂载点已存在。此时查看huawei-csi-node的日志信息（详情请参考[如何查看华为CSI日志](/docs/常用操作/信息收集/如何查看华为CSI日志)），日志提示错误为：The mount /var/lib/kubelet/pods/xxx/mount is already exist, but the source path is not /var/lib/kubelet/plugins/kubernetes.io/xxx/globalmount

## 根因分析{#section135642617536}

该问题的根因是Kubernetes进行重复挂载操作。

## 解决措施或规避方法{#section75642613539}

执行以下命令，将已存在的路径解除挂载，其中“/var/lib/kubelet/pods/xxx/mount”为日志中提示的已存在的挂载路径。

```
umount /var/lib/kubelet/pods/xxx/mount
```

