---
title: "Kubernetes、OpenShift、Tanzu卸载华为CSI"
linkTitle: "Kubernetes、OpenShift、Tanzu卸载华为CSI"
description: 
weight: 1
---

本章节介绍如何在Kubernetes、OpenShift、Tanzu平台卸载华为CSI。

## 操作步骤{#section9152125194710}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令卸载华为CSI，_helm-huawei-csi _是自定义的Helm Chart名称，_huawei-csi_  是该Helm Chart所在的命名空间。该卸载命令将会卸载华为CSI的huawei-csi-controller、huawei-csi-node和RBAC资源。

    ```
    helm uninstall helm-huawei-csi -n huawei-csi
    ```

    卸载命令执行后，还需要检查卸载是否成功。其中，_huawei-csi_为chart所在的命名空间。

    ```
    helm list -n huawei-csi
    ```

    命令结果示例如下，如果回显为空，则表示服务卸载成功。

    ```
    NAME    NAMESPACE       REVISION        UPDATED STATUS  CHART   APP VERSION
    ```

3.  卸载huawei-csi-host-info对象，请参考[卸载huawei-csi-host-info对象](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section870813403017)进行操作。
4.  卸载webhook资源，请参考[卸载Webhook资源](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section871155813014)进行操作。
5.  （可选）卸载快照依赖组件服务，请参考[卸载Snapshot依赖组件服务](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section48371491319)进行操作。
6.  （可选）卸载Lease资源，请参考[卸载Lease资源](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section263805014317)进行操作。

