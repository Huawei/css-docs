---
title: "创建PVC变更资源"
linkTitle: "创建PVC变更资源"
description: 
weight: 2
---

本章节介绍如何基于已配置的PVC变更文件创建PVC变更资源。

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>-   仅支持双活AA模式。
>-   如果变更场景为普通卷变更为双活卷，则仅支持变更主站点端存储卷。
>-   创建PVC变更资源期间，请勿使用华为CSI管理PVC。
>-   不支持对同一个PVC创建多个VolumeModifyClaim资源，若存在对目标PVC的多次变更，请在单次变更完成之后再执行。

## 操作步骤{#section694142182112}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，创建PVC变更。

    ```
    kubectl create -f volumemodifyclaim.yaml 
    ```

3.  参考[查询PVC变更](/docs/advanced-features/pvc-change/configuring-pvc-changes/querying-a-pvc-change)查询创建结果。

