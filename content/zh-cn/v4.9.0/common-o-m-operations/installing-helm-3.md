---
title: "安装Helm 3"
linkTitle: "安装Helm 3"
description: 
weight: 1
---

本章节指导用户如何安装Helm 3。

参考：[https://helm.sh/docs/intro/install/](https://helm.sh/docs/intro/install/)

## 前提条件{#zh-cn_topic_0000001274250896_section19453102010152}

确保Kubernetes集群中的master节点可以访问Internet。

## 操作步骤{#section164291640172317}

1.  执行以下命令，下载Helm 3的安装脚本。

    ```
    curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
    ```

2.  执行以下命令，修改Helm 3的安装脚本权限。

    ```
    chmod 700 get_helm.sh
    ```

3.  根据Helm与Kubernetes版本配套关系确认需要安装的Helm版本，配套关系请参考[Helm Version Support Policy](https://helm.sh/docs/topics/version_skew/#supported-version-skew)，执行以下命令，修改DESIRED\_VERSION环境变量为需要安装的Helm版本，并执行安装命令。

    ```
    DESIRED_VERSION=v3.9.0 ./get_helm.sh
    ```

4.  执行以下命令，查看指定版本的Helm 3是否安装成功。

    ```
    helm version
    ```

    命令结果示例如下，说明安装成功。

    ```
    version.BuildInfo{Version:"v3.9.0", GitCommit:"7ceeda6c585217a19a1131663d8cd1f7d641b2a7", GitTreeState:"clean", GoVersion:"go1.17.5"}
    ```

