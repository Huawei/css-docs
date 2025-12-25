---
title: "卸载CSI依赖组件服务"
linkTitle: "卸载CSI依赖组件服务"
description: 
weight: 3
---

本章节介绍如何卸载CSI依赖组件服务。

## 卸载huawei-csi-host-info对象{#section870813403017}

名称为huawei-csi-host-info的Secret对象中保存着集群中各个节点的启动器信息，例如iSCSI启动器。使用helm uninstall命令时不会卸载该资源，若需卸载该资源，请参考以下步骤：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令卸载Secret对象，其中huawei-csi-host-info是Secret对象的名称，huawei-csi是Secret对象所在的命名空间。

    ```
    kubectl delete secret huawei-csi-host-info -n huawei-csi
    ```

3.  执行以下命令检查Secret对象是否卸载成功。

    ```
    kubectl get secret huawei-csi-host-info -n huawei-csi 
    ```

    命令结果示例如下，如果命令回显提示“NotFound”表示huawei-csi-host-info对象已成功卸载。

    ```yaml
    Error from server (NotFound): secrets "huawei-csi-host-info" not found
    ```

## 卸载Webhook资源{#section871155813014}

名称为storage-backend-controller.xuanwu.huawei.io的webhook资源用于校验Backend的秘钥信息和与存储的连通性，使用helm uninstall命令时不会卸载该资源，若需卸载该资源，请参考以下步骤：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，查询webhook依赖组件服务。

    ```
    kubectl get validatingwebhookconfigurations.admissionregistration.k8s.io storage-backend-controller.xuanwu.huawei.io
    ```

    命令结果示例如下：

    ```
    NAME                                          WEBHOOKS   AGE
    storage-backend-controller.xuanwu.huawei.io   1          12d
    ```

3.  执行以下命令，卸载webhook依赖组件服务。

    ```
    kubectl delete validatingwebhookconfigurations.admissionregistration.k8s.io storage-backend-controller.xuanwu.huawei.io
    ```

4.  执行以下命令，检查服务是否已成功卸载。如果结果为空，表示已成功卸载。

    ```
    kubectl get validatingwebhookconfigurations.admissionregistration.k8s.io storage-backend-controller.xuanwu.huawei.io
    ```

## 卸载Snapshot依赖组件服务{#section48371491319}

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   请勿在存在快照时卸载Snapshot依赖组件服务，否则Kubernetes会自动删除所有的用户快照且无法恢复。详细说明请参见[删除 CustomResourceDefinition](https://kubernetes.io/zh/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/#delete-a-customresourcedefinition)。
>-   请勿在CSI升级时卸载Snapshot依赖组件服务。

**场景说明**

-   当前华为CSI使用了快照特性。
-   当前Kubernetes集群仅存在华为CSI，且不再使用华为CSI。
-   在卸载前请确保在Kubernetes集群中已经没有华为CSI管理的VolumeSnapshot资源。

**操作步骤**

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，卸载Snapshot依赖组件服务。

    ```
    kubectl delete crd volumesnapshotclasses.snapshot.storage.k8s.io volumesnapshotcontents.snapshot.storage.k8s.io volumesnapshots.snapshot.storage.k8s.io
    ```

3.  执行以下命令，检查服务是否已成功卸载。如果结果为空，表示已成功卸载。

    ```
    kubectl get crd | grep snapshot.storage.k8s.io
    ```

## 卸载Lease资源{#section263805014317}

当使用多副本方式部署huawei-csi-controller时，会生成Lease资源，用于保存当前Holder信息。使用helm uninstall命令时不会卸载该资源，若需卸载该资源，请参考以下步骤：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，查询Lease信息。

    ```
    kubectl get lease -n huawei-csi
    ```

    命令结果示例如下：

    ```
    NAME                                         HOLDER    AGE
    csi-huawei-com                               node-1    24d
    external-attacher-leader-csi-huawei-com      node-1    24d
    external-resizer-csi-huawei-com              node-1    24d
    external-snapshotter-leader-csi-huawei-com   node-1    24d
    snapshot-controller-leader                   node-1    24d
    storage-backend-controller                   node-1    24d
    huawei-csi-extender                          node-1    24d
    ```

3.  执行以下命令，卸载Lease资源。

    ```
    kubectl delete lease -n huawei-csi csi-huawei-com external-attacher-leader-csi-huawei-com external-resizer-csi-huawei-com external-snapshotter-leader-csi-
    ```

4.  执行以下命令，检查是否已成功卸载。

    ```
    kubectl get lease -n huawei-csi
    ```

    命令结果示例如下，如果结果为空，表示已成功卸载。

    ```
    No resources found in huawei-csi namespace.
    ```

