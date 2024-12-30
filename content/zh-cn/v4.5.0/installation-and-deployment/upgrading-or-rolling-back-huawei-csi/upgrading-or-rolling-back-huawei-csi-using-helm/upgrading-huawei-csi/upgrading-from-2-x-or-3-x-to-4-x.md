---
title: "从2.x或3.x升级至4.x版本"
linkTitle: "从2.x或3.x升级至4.x版本"
description: 
weight: 1
---

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>在CSI 2.x或3.x 版本中，使用块存储时，与存储建立映射的操作是在huawei-csi-node服务进行的，所以huawei-csi-node服务需要和存储管理网络通信。又由于huawei-csi-node服务是以DaemonSet部署的，在集群中每个节点都会部署一个huawei-csi-node服务，这样部署模型导致了在大规模集群下，每个huawei-csi-node服务都会向存储发起请求，可能导致存储连接数被占满，使得huawei-csi-node不能提供正常服务。
>在CSI 4.x版本优化了该部署模型，将与存储建立映射操作迁移至huawei-csi-controller服务，huawei-csi-node服务不再需要和存储管理网络通信，降低了华为CSI依赖的组网复杂度，同时huawei-csi-controller服务以Deployment形式部署，副本数根据客户可靠性要求设置，一般情况下，副本数为1\~3。所以极大的减少了华为CSI与存储的连接数量，使得华为CSI服务能够接入大规模集群。
>**该架构变化可能会导致一个问题**：升级后，使用2.x或3.x发放的工作负载，升级CSI至4.x版本之后，如果产生了一次新的挂载流程，并且CO（Container Orchestration system）未调用华为CSI提供的huawei-csi-controller服务，会导致挂载失败。问题请参考[创建Pod失败，Events日志显示“publishInfo doesn't exist”](/v4.5.0/troubleshooting/pod-issues/a-pod-fails-to-be-created-and-message-publishinfo-doesn-t-exist-is-displayed-in-the-events-log)。

## 备份存储后端配置{#section3200825558}

如果您已按照以上须知评估风险后，确认需要从2.x或3.x版本的CSI升级至4.5.0版本，请按照以下操作步骤备份存储后端配置：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令备份后端信息到configmap.json文件中。OpenShift平台使用**oc**替换**kubectl**命令。

    ```
    kubectl get cm huawei-csi-configmap -n huawei-csi -o json > configmap.json
    ```

## 升级华为CSI{#section1413511233612}

请按照[升级华为CSI](/v4.5.0/installation-and-deployment/upgrading-or-rolling-back-huawei-csi/upgrading-or-rolling-back-huawei-csi-using-helm/upgrading-huawei-csi/upgrading-huawei-csi-on-kubernetes-openshift-and-tanzu#section6841317173013)中的步骤进行升级。

## 配置存储后端{#section496812169812}

请将[备份存储后端配置](#section3200825558)中备份的后端信息，按照[管理存储后端](/v4.5.0/storage-backend-management/managing-storage-backends)章节的说明配置存储后端，存储后端配置成功后，请务必按照以上须知所述的风险处理方法进行操作，避免Pod在漂移过程中出现问题。

