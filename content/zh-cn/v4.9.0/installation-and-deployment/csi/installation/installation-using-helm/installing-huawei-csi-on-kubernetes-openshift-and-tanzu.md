---
title: "Kubernetes、OpenShift、Tanzu安装华为CSI"
linkTitle: "Kubernetes、OpenShift、Tanzu安装华为CSI"
description: 
weight: 1
---

## 安装步骤{#section9426125115349}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录集群的任意master节点。
2.  将Kubernetes CSI组件包中的"helm"目录拷贝到master节点的任意目录下。Helm工具路径请参见[表1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。
3.  进入到helm/esdk的工作目录下。

    ```
    cd helm/esdk
    ```

4.  准备**values.yaml**文件，华为CSI已经在软件包的helm/esdk目录下提供了values.yaml模板文件，您也可以根据[Helm values.yaml参数说明](/docs/installation-and-deployment/csi/installation/installation-using-helm/parameters-in-the-values-yaml-file-of-helm)修改参数对华为CSI进行定制。
5.  安装前配置：
    -   若容器平台为Kubernetes，可跳过该步骤。
    -   若容器平台为OpenShift，请根据[OpenShift平台安装配置](#section14977616204416)进行配置。
    -   若容器平台为Tanzu，请根据[Tanzu平台安装配置](#section9291624164514)进行配置。

6.  执行命令，更新存储后端CRD

    ```
    kubectl apply -f ./crds/backend/
    ```

7.  **（可选）**  请务必按照[检查卷快照依赖组件](/docs/installation-and-deployment/csi/installation-preparations/checking-volume-snapshot-dependent-components)章节检查快照依赖组件，确认无误后执行执行命令更新快照CRD，如果controller.snapshot.enabled参数设置为false或Kubernetes版本低于v1.20，可跳过本步骤，详情请参考[表2](/docs/installation-and-deployment/csi/installation/installation-using-helm/parameters-in-the-values-yaml-file-of-helm#table813124411459)。

    ```
    kubectl apply -f ./crds/snapshot-crds/ --validate=false
    ```

8.  执行如下命令安装华为CSI。其中，helm-huawei-csi为自定义的Helm Chart名称，./表示使用当前目录下的Helm工程，huawei-csi为自定义的Helm Chart命名空间。

    ```
    helm install helm-huawei-csi ./ -n huawei-csi --create-namespace
    ```

    命令结果示例如下：

    ```yaml
    NAME: helm-huawei-csi
    LAST DEPLOYED: Wed Jun  8 11:50:28 2022
    NAMESPACE: huawei-csi
    STATUS: deployed
    REVISION: 1
    TEST SUITE: None
    ```

9.  完成huawei-csi服务部署后，可执行如下命令检查服务是否启动。

    ```
    kubectl get pod -n huawei-csi
    ```

    命令结果示例如下，Pod状态为“Running“则安装成功。

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   9/9     Running   0          24m
    huawei-csi-controller-6dfcc4b79f-csphc   9/9     Running   0          24m
    huawei-csi-node-g6f4k                    3/3     Running   0          20m
    huawei-csi-node-tqs87                    3/3     Running   0          20m
    ```

## OpenShift平台安装配置{#section14977616204416}

OpenShift平台请根据以下步骤创建SecurityContextConstraints资源。

1.  执行命令，编辑helm\_scc.yaml文件。

    ```
    vi helm_scc.yaml
    ```

2.  修改helm\_scc.yaml文件。其中huawei-csi是指创建的命名空间，请根据实际情况填写。

    ```yaml
    apiVersion: security.openshift.io/v1
    kind: SecurityContextConstraints
    metadata:
      name: helm-scc
    allowHostDirVolumePlugin: true
    allowHostIPC: true
    allowHostNetwork: true
    allowHostPID: true
    allowHostPorts: true
    allowPrivilegeEscalation: true
    allowPrivilegedContainer: true
    
    defaultAddCapabilities:
    - SYS_ADMIN
    runAsUser:
      type: RunAsAny
    seLinuxContext:
      type: RunAsAny
    fsGroup:
      type: RunAsAny
    users:
    - system:serviceaccount:huawei-csi:huawei-csi-controller
    - system:serviceaccount:huawei-csi:huawei-csi-node
    ```

3.  执行命令，创建SecurityContextConstraints。

    ```
    oc create -f helm_scc.yaml
    ```

## Tanzu平台安装配置{#section9291624164514}

Tanzu平台请执行以下命令配置kubelet安装目录。

1.  进入到安装包的helm/esdk目录下，执行以下命令打开配置文件。安装包目录请参见[表1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。

    ```
    vi values.yaml
    ```

2.  修改kubeletConfigDir参数如下并保存：

    ```yaml
    # Specify kubelet config dir path.
    # kubernetes and openshift is usually /var/lib/kubelet
    # Tanzu is usually /var/vcap/data/kubelet
    # CCE is usually /mnt/paas/kubernetes/kubelet
    kubeletConfigDir: /var/vcap/data/kubelet
    ```

Tanzu平台TKGI 1.16版本及以下请执行以下命令配置RBAC权限

1.  执行命令， 创建rbac.yaml文件。

    ```
    vi rbac.yaml
    ```

2.  粘贴如下内容至rbac.yaml，保存并退出：

    ```
    apiVersion: rbac.authorization.k8s.io/v1
    kind: ClusterRole
    metadata:
      name: huawei-csi-psp-role
    rules:
    - apiGroups: ['policy']
      resources: ['podsecuritypolicies']
      verbs: ['use']
    ---
    apiVersion: rbac.authorization.k8s.io/v1
    kind: ClusterRoleBinding
    metadata:
      name: huawei-csi-psp-role-cfg
    roleRef:
      kind: ClusterRole
      name: huawei-csi-psp-role
      apiGroup: rbac.authorization.k8s.io
    subjects:
    - kind: Group
      apiGroup: rbac.authorization.k8s.io
      name: system:serviceaccounts:huawei-csi
    - kind: Group
      apiGroup: rbac.authorization.k8s.io
      name: system:serviceaccounts:default
    ```

3.  执行命令，创建RBAC权限。

    ```
    kubectl create -f rbac.yaml
    ```

