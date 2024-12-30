---
title: "如何查看华为CSI日志"
linkTitle: "如何查看华为CSI日志"
description: 
weight: 2
---

## 查看huawei-csi-controller服务的日志{#zh-cn_topic_0000001191906803_section5326743451}

1.  执行以下命令，获取huawei-csi-controller所在的节点

    ```
    kubectl get pod -A -o wide | grep huawei
    ```

    命令结果示例如下，其中IP为节点主机IP地址，NODE为节点主机名称。

    ```
    NAME                                    READY   STATUS    RESTARTS   AGE     IP             NODE         NOMINATED NODE   READINESS GATES
    huawei-csi-controller-695b84b4d8-tg64l  9/9     Running  0          14s     <host1-ip>     <host1-name> <none>           <none>
    ```

2.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群中huawei-csi-controller服务所在节点
3.  进入日志目录。

    ```
    cd /var/log/huawei
    ```

4.  执行以下命令，查看容器自定义输出日志。

    ```
    vi huawei-csi-controller
    ```

5.  进入容器目录。

    ```
    cd /var/log/containers
    ```

6.  执行以下命令， 查看容器标准输出日志。

    ```
    vi huawei-csi-controller-<name>_huawei-csi_huawei-csi-driver-<container-id>.log
    ```

## 查看huawei-csi-node服务的日志{#zh-cn_topic_0000001191906803_section66851055357}

1.  执行以下命令，获取huawei-csi-node所在的节点

    ```
    kubectl get pod -A -o wide | grep huawei
    ```

    命令结果示例如下，其中IP为节点主机IP地址，NODE为节点主机名称。

    ```
    NAME                     READY   STATUS    RESTARTS   AGE     IP             NODE         NOMINATED NODE   READINESS GATES
    huawei-csi-node-g6f7z    3/3     Running  0          14s     <host2-ip>     <host2-name> <none>           <none>
    ```

2.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群中huawei-csi-node服务所在节点
3.  进入日志目录。

    ```
    cd /var/log/huawei
    ```

4.  执行以下命令，查看容器自定义输出日志。

    ```
    vi huawei-csi-node
    ```

5.  进入容器目录。

    ```
    cd /var/log/containers
    ```

6.  执行以下命令，  查看容器标准输出日志。

    ```
    vi huawei-csi-node-<name>_huawei-csi_huawei-csi-driver-<container-id>.log
    ```

