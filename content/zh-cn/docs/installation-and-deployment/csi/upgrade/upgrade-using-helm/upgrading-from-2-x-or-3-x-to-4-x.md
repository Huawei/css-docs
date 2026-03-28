---
title: "从2.x或3.x升级至4.x版本"
linkTitle: "从2.x或3.x升级至4.x版本"
description: 
weight: 1
---

## 备份存储后端配置{#section3200825558}

如果您已按照以上须知评估风险后，确认需要从2.x或3.x版本的CSI升级至4.11.0版本，请按照以下操作步骤备份存储后端配置：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令备份后端信息到configmap.json文件中。OpenShift平台使用**oc**替换**kubectl**命令。

    ```
    kubectl get cm huawei-csi-configmap -n huawei-csi -o json > configmap.json
    ```

## 升级华为CSI{#section1413511233612}

请按照[升级华为CSI](/docs/installation-and-deployment/csi/upgrade/upgrade-using-helm/upgrading-huawei-csi-on-kubernetes-openshift-and-tanzu#section6841317173013)中的步骤进行升级。

## 配置存储后端{#section496812169812}

1.  请将[备份存储后端配置](#section3200825558)中备份的后端信息，按照[存储后端管理](/docs/basic-services/storage-backend-management)章节的说明配置存储后端。其中通过备份后端信息配置存储后端命令如下。

    ```
    oceanctl create backend -f configmap.json -i json -n huawei-csi
    ```

