---
title: "手动方式开启PVC变更特性"
linkTitle: "手动方式开启PVC变更特性"
description: 
weight: 2
---

## 前提条件{#section10631153612202}

已使用手动方式安装华为CSI。

## 操作步骤{#section810241682811}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  进入manual/esdk工作目录下，执行以下命令，配置卷变更CRD。

    ```
    kubectl apply -f ./crds/volume-modify/
    ```

3.  执行以下命令。组件包路径请参考[表1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。

    ```
    kubectl apply -f ./deploy/huawei-csi-controller-extender.yaml
    ```

4.  执行命令检查服务是否启动。

    ```
    kubectl get pod -n huawei-csi
    ```

    命令结果示例如下，其中huawei-csi为华为CSI部署命名空间。

    ```
    NAME                                     READY     STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   10/10     Running   0          24m
    huawei-csi-node-tqs87                    3/3       Running   0          24m
    ```

