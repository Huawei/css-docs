---
title: "启动华为CSI服务失败，提示错误：“/etc/localtime is not a file”"
linkTitle: "启动华为CSI服务失败，提示错误：“/etc/localtime is not a file”"
description: 
weight: 2
---

## 现象描述{#zh-cn_topic_0000001086137838_section1566717121452}

安装部署CSI时，Pod运行不起来，处于ContainerCreating状态，查看Pod中有打印告警事件：/etc/localtime is not a file。

## 根因分析{#zh-cn_topic_0000001086137838_section1425013451056}

容器挂载主机/etc/localtime文件时，识别类型有误，容器挂载不上主机侧/etc/localtime文件，导致Pod运行不起来。

## 操作步骤{#section158611659145513}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  <a name="li131611149192013"></a>执行命令，查看CSI服务Pod运行状态。

    ```
    kubectl get pod -n huawei-csi
    ```

    命令结果示例如下，其中huawei-csi为CSI服务部署的命名空间。

    ```
    NAME                                     READY   STATUS               RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   9/9     ContainerCreating    0          24m
    huawei-csi-controller-6dfcc4b79f-csphc   9/9     ContainerCreating    0          24m
    huawei-csi-node-g6f4k                    3/3     ContainerCreating    0          20m
    huawei-csi-node-tqs87                    3/3     ContainerCreating    0          20m
    ```

3.  执行命令，通过查看容器的“Events”参数。

    ```
    kubectl describe pod huawei-csi-controller-6dfcc4b79f-9vjtq -n huawei-csi
    ```

    命令结果示例如下。其中，_huawei-csi-controller-6dfcc4b79f-9vjtq_  为[2](#li131611149192013)中查找到的状态显示为“ContainerCreating”的Pod名称，huawei-csi为该Pod所在的命名空间。

    ```
    ...
    Events:
      Type     Reason       Age                From               Message
      ----     ------       ----               ----               -------
      Normal   Scheduled    96s                default-scheduler  Successfully assigned huawei-csi/huawei-csi-controller-6dfcc4b79f-9vjtq to node1
      Warning  FailedMount  33s (x8 over 96s)  kubelet            MountVolume.SetUp failed for volume "host-time" : hostPath type check failed: /etc/localtime is not a file
    ```

4.  执行命令**cd /helm/esdk/templates**，进入到CSI的安装包路径下。路径请参见[表1](/v4.5.0/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。
5.  以huawei-csi-controller.yaml文件为例，执行以下命令，查看文件内容。

    ```
    vi huawei-csi-controller.yaml
    ```

    找到对应volumes配置下的host-time挂载项，删除**type: File**这一行配置内容。对**templates**目录下涉及该配置项的huawei-csi-node.yaml部署文件，执行相同的操作。

    ```
    ...
    ...
    volumes:
      - hostPath:
          path: /var/log/
          type: Directory
        name: log
      - hostPath:
          path: /etc/localtime
          type: File
        name: host-time
    ...
    ...
    ```

6.  参考[Helm卸载华为CSI](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm)卸载服务后，重新安装服务。
7.  执行以下命令，查看华为CSI服务Pod运行状态为Running。

    ```
    kubectl get pod -n huawei-csi
    ```

    命令结果示例如下：

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjts   9/9     Running   0          24m
    huawei-csi-controller-6dfcc4b79f-csphb   9/9     Running   0          24m
    huawei-csi-node-g6f41                    3/3     Running   0          20m
    huawei-csi-node-tqs85                    3/3     Running   0          20m
    ```

