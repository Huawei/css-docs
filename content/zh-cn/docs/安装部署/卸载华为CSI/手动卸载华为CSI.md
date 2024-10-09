---
title: "手动卸载华为CSI"
linkTitle: "手动卸载华为CSI"
description: 
weight: 2
---

本章节介绍如何手动卸载华为CSI。

>![](/public_sys-resources/zh/icon-notice.gif)  
>如果您不是出于升级的目的卸载华为CSI，请确保卸载华为CSI前已经在您的容器平台中将华为CSI发放的资源（PV、PVC、快照、存储后端等）全部清理。否则一旦您卸载华为CSI后，这些资源将无法被自动调度、管理或者清理。

## 卸载huawei-csi-node服务{#section1012817231386}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令卸载 huawei-csi-node 服务，huawei-csi 替换为华为CSI所在的命名空间。

    ```
    kubectl delete daemonset huawei-csi-node -n huawei-csi
    ```

3.  执行以下命令检查服务是否已成功卸载（如果提示NotFound错误，表示已成功卸载）。

    ```
    kubectl get daemonset huawei-csi-node -n huawei-csi
    ```

## 卸载huawei-csi-controller服务{#section34281930180}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令卸载 huawei-csi-controller 服务，huawei-csi 替换为华为CSI所在的命名空间。

    ```
    kubectl delete deployment huawei-csi-controller -n huawei-csi
    ```

3.  执行以下命令检查服务是否已成功卸载（如果提示NotFound错误，表示已成功卸载）。

    ```
    kubectl get deployment huawei-csi-controller -n huawei-csi
    ```

## 卸载csidriver对象{#section4229471288}

如果[安装时未使用CSIDriver特性](/docs/安装部署/安装华为CSI/手动安装华为CSI#li395973220487)，可跳过本步骤。

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令卸载csidriver对象。

    ```
    kubectl delete csidriver csi.huawei.com
    ```

3.  执行以下命令检查服务是否已成功卸载（如果提示NotFound错误，表示已成功卸载）。

    ```
    kubectl get csidriver csi.huawei.com
    ```

## 删除RBAC权限{#section111616512911}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  删除RBAC权限。

    ```
    kubectl -n huawei-csi -l provisioner=csi.huawei.com delete ServiceAccount,Service,role,rolebinding,ClusterRole,ClusterRoleBinding
    ```

## 其它资源卸载{#section1370361019919}

1.  卸载huawei-csi-host-info对象，请参考[卸载huawei-csi-host-info对象](/docs/安装部署/卸载华为CSI/Helm卸载华为CSI/卸载CSI依赖组件服务#section870813403017)进行操作。
2.  卸载webhook资源，请参考[卸载Webhook资源](/docs/安装部署/卸载华为CSI/Helm卸载华为CSI/卸载CSI依赖组件服务#section871155813014)进行操作。
3.  （可选）卸载快照依赖组件服务，请参考[卸载Snapshot依赖组件服务](/docs/安装部署/卸载华为CSI/Helm卸载华为CSI/卸载CSI依赖组件服务#section48371491319)进行操作。
4.  （可选）卸载Lease资源，请参考[卸载Lease资源](/docs/安装部署/卸载华为CSI/Helm卸载华为CSI/卸载CSI依赖组件服务#section263805014317)进行操作。

