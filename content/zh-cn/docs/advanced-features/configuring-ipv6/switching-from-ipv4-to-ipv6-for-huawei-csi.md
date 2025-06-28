---
title: "华为CSI由IPv4切换至IPv6"
linkTitle: "华为CSI由IPv4切换至IPv6"
description: 
weight: 2
---

本章节介绍更新华为CSI时如何由IPv4切换为IPv6。

## 前提条件{#section11013445374}

-   主机环境、Kubernetes集群环境已支持IPv6协议。可参考[Kubernetes官方IPv4/IPv6双栈配置](https://kubernetes.io/docs/concepts/services-networking/dual-stack/)。
-   华为CSI已安装且服务正常启动。

## 操作步骤{#section826141105010}

1.  <a name="li19355236151916"></a>执行以下命令，获取原有服务配置文件。其中helm-huawei-csi为旧版本安装时指定的Helm Chart名称，huawei-csi为旧版本安装时指定的Helm Chart命名空间。

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

2.  执行**vi update-values.yaml**命令打开[1](#li19355236151916)中获取的文件，修改service.ipFamilyPolicy和service.ipFamilies配置项，具体参数描述见[表5](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table258712427285)。

    修改示例如下：

    ```yaml
    service:
      ipFamilyPolicy: SingleStack
      ipFamilies:
        - IPv6
    ```

3.  切换IPv6前，先执行以下命令，删除huawei-csi命名空间下的service。

    ```
    kubectl delete service -n huawei-csi --all
    ```

4.  执行以下命令，升级华为CSI。其中helm-huawei-csi为指定的Helm Chart名称，huawei-csi为指定的Helm Chart命名空间，update-values.yaml为[1](#li19355236151916)中获取的文件。

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi -f ./values.yaml -f ./update-values.yaml
    ```

5.  执行以下命令查询更新后的huawei-csi-controller service的ipFamilies参数。

    ```
    kubectl get svc -n huawei-csi huawei-csi-controller -o=jsonpath='{.spec.ipFamilies}'
    ```

    预期结果如下：

    ```
    ["IPv6"]
    ```

