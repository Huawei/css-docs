---
title: "删除PVC变更"
linkTitle: "删除PVC变更"
description: 
weight: 3
---

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   当VolumeModifyClaim的STATUS值为Creating时，删除VolumeModifyClaim资源，将会在存储侧删除此次变更创建的资源，然后移除集群资源。在删除后，如果继续使用原有的StorageClass进行PVC管理，需要将关联的存储后端恢复为非双活存储后端。
>-   当VolumeModifyClaim的STATUS值为Pending或Completed时，删除VolumeModifyClaim资源，仅会移除集群资源，不会和存储交互，即不会在存储侧删除变更创建的资源。
>-   VolumeModifyContent被VolumeModifyClaim管理，请勿手动管理VolumeModifyContent资源。
>-   若待变更PVC中已有部分PVC满足变更要求，当批量变更失败时，会移除掉所有PVC的变更，导致已满足变更条件的PVC不再满足。
>-   若待变更PVC已经在存储侧被手动管理，则可能导致变更失败。使用变更特性时，请勿手动管理存储卷。

当前章节介绍如何使用kubectl删除PVC变更，基于步骤如下。

## 操作步骤{#section694142182112}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行 命令，删除PVC变更。其中  _vmc-name_  为VolumeModifyClaim资源名称。

    ```
    kubectl delete volumemodifyclaims <vmc-name>
    ```

3.  参考[创建PVC变更资源](/v4.5.0/advanced-features/pvc-change/configuring-pvc-changes/creating-a-pvc-change/creating-a-pvc-change-resource)查询删除结果。

