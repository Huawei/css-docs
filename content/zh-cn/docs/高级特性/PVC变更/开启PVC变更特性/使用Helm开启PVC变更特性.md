---
title: "使用Helm开启PVC变更特性"
linkTitle: "使用Helm开启PVC变更特性"
description: 
weight: 1
---

## 前提条件{#section10631153612202}

-   已使用Helm安装华为CSI。
-   要求华为CSI v4.5.0及以上版本。

## 操作步骤{#section1361061612118}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令检查PVC变更特性是否开启。

    其中helm-huawei-csi为安装时指定的Helm Chart名称，huawei-csi为安装时指定的Helm Chart命名空间。组件包路径请参考[表 软件包组件描述](/docs/安装部署/安装前准备/下载华为CSI软件包#zh-cn_topic_0150885197_table17200162435412)。

    ```
    helm get values helm-huawei-csi -n huawei-csi -a | grep volumeModify -A 1
    ```

    命令结果示例如下：

    -   若回显内容为“enabled: true”，则表示特性开启，可跳过后续步骤。
    -   若回显内容为“enabled: false”，请按照后续步骤开启PVC变更特性。

    ```yaml
    volumeModify:
      enabled: false
    ```

3.  进入/helm/esdk目录，执行命令，配置卷变更CRD。

    ```
    # kubectl apply -f ./crds/volume-modify/
    customresourcedefinition.apiextensions.k8s.io/volumemodifyclaims.xuanwu.huawei.io configured
    customresourcedefinition.apiextensions.k8s.io/volumemodifycontents.xuanwu.huawei.io configured
    ```

    >![](/css-docs/public_sys-resources/zh/icon-note.gif) 
    >如回显中存在“Warning: resource customresourcedefinitions/volumemodifycontents.xuanwu.huawei.io is missing the kubectl.kubernetes.io/last-applied-configuration...”提示，可忽略该提示。该提示出现原因是由于Helm安装应用时使用的是kubectl create命令而不是kubectl apply命令。

4.  <a name="li1230915254221"></a>执行以下命令，获取原有服务配置文件。

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

5.  执行**vi update-values.yaml**命令打开[4](#li1230915254221)中获取的文件，修改以下配置。修改完成后，按**Esc**，并输入**:wq!**，保存修改。

    ```yaml
    csiExtender:
      volumeModify:    
        enabled: true
    ```

6.  执行以下命令更新华为CSI服务。

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi  -f ./update-values.yaml
    ```

7.  执行命令检查服务是否启动。

    ```
    kubectl get pod -n huawei-csi
    ```

    命令结果示例如下，其中huawei-csi为华为CSI部署命名空间。

    ```
    NAME                                     READY     STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   10/10     Running   0          24m
    huawei-csi-node-tqs87                    3/3       Running   0          20m
    ```

