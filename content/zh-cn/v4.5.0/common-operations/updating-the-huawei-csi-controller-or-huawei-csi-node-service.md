---
title: "更新huawei-csi-controller或huawei-csi-node服务"
linkTitle: "更新huawei-csi-controller或huawei-csi-node服务"
description: 
weight: 4
---

当您需要更新huawei-csi-controller或huawei-csi-node服务时，例如修改huawei-csi-controller服务的副本数时，执行此操作。

## 操作步骤{#section1452416823017}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  <a name="li1037712113474"></a>进入/helm/esdk 目录，执行以下命令，获取原有服务配置文件。其中helm-huawei-csi为旧版本安装时指定的Helm Chart名称，huawei-csi为旧版本安装时指定的Helm Chart命名空间。组件包路径请参考[表1](/v4.5.0/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

3.  执行  **vi update-values.yaml**  命令打开[2](#li1037712113474)中获取的文件，参考[Helm values.yaml参数说明](/v4.5.0/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm)修改配置项，修改完成后，按**Esc**，并输入  **:wq!**，保存修改。
4.  执行以下命令更新华为CSI服务。

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi  -f ./update-values.yaml
    ```

