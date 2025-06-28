---
title: "首次安装华为CSI时配置IPv6"
linkTitle: "首次安装华为CSI时配置IPv6"
description: 
weight: 1
---

本章节介绍首次安装华为CSI时如何指定IPv6。

## 前提条件{#section11013445374}

-   仅存储后端类型为oceanstor-nas、oceanstor-san和oceanstor-dtree时，支持配置为IPv6。
-   主机环境、Kubernetes集群环境已支持IPv6协议。可参考[Kubernetes官方IPv4/IPv6双栈配置](https://kubernetes.io/docs/concepts/services-networking/dual-stack/)。

## 操作步骤{#section147071119142913}

1.  参考[安装步骤](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#section9426125115349)章节执行[1](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#zh-cn_topic_0000001324610777_li9582123242310)\~[7](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#li1759104413237)，完成CSI依赖组件的安装。
2.  执行**vi values.yaml**命令打开配置文件，修改service.ipFamilyPolicy和service.ipFamilies配置项，具体参数描述见[表5](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table258712427285)。

    修改示例如下：

    ```yaml
    service:
      ipFamilyPolicy: SingleStack
      ipFamilies:
        - IPv6
    ```

3.  参考[安装步骤](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#section9426125115349)章节执行[8](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#zh-cn_topic_0000001324610777_li888917271326)\~[9](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#zh-cn_topic_0000001324610777_li108160349154)，完成华为CSI的安装部署。
4.  执行以下命令查看huawei-csi命名空间下service的状态。

    ```
    kubectl get service -n huawei-csi
    ```

    命令结果示例如下：

    ```
    NAME                    TYPE        CLUSTER-IP         EXTERNAL-IP   PORT(S)    AGE
    huawei-csi-controller   ClusterIP   fd00:10:96::8136   <none>        4433/TCP   19m
    ```

5.  执行以下命令查看huawei-csi-controller service的ipFamilies字段值。

    ```
    kubectl get svc -n huawei-csi huawei-csi-controller -o=jsonpath='{.spec.ipFamilies}'
    ```

    命令结果示例如下：

    ```
    ["IPv6"]
    ```

6.  执行以下命令查看huawei-csi-controller service的ipFamilyPolicy字段值。

    ```
    kubectl get svc -n huawei-csi huawei-csi-controller -o=jsonpath='{.spec.ipFamilyPolicy}'
    ```

    命令结果示例如下：

    ```
    SingleStack
    ```

