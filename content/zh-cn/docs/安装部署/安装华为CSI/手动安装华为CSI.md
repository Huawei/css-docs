---
title: "手动安装华为CSI"
linkTitle: "手动安装华为CSI"
description: 
weight: 2
---

本章节介绍如何手动安装华为CSI。

>![](/css-docs/public_sys-resources/zh/icon-note.gif) 
>手动安装华为CSI当前仅支持Kubernetes平台。

## 安装步骤{#section113761618183018}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录集群的任意master节点。
2.  将Kubernetes CSI组件包中的"manual"目录拷贝到master节点的任意目录下。
3.  执行命令创建一个命名空间。

    ```
    kubectl create ns huawei-csi
    ```

4.  进入到manual/esdk的工作目录下。具体路径请参见[表 软件包组件描述](/docs/安装部署/安装前准备/下载华为CSI软件包#zh-cn_topic_0150885197_table17200162435412)。

    ```
    cd manual/esdk
    ```

5.  执行命令，更新存储后端CRD

    ```
    kubectl apply -f ./crds/backend/
    ```

6.  **（可选）**  请务必按照[检查卷快照依赖组件](/docs/安装部署/安装前准备/检查卷快照依赖组件)章节检查快照依赖组件，确认无误后执行执行命令更新快照CRD，如果Kubernetes版本低于v1.17，跳过本步骤。

    ```
    kubectl apply -f ./crds/snapshot-crds/ --validate=false
    ```

7.  **（可选）**  执行命令安装CSIDriver。如果不使用CSIDriver特性，可跳过本步骤，详情请参考[CSIDriver](https://kubernetes-csi.github.io/docs/csi-driver-object.html)特性。

    ```
    kubectl apply -f ./deploy/csidriver.yaml 
    ```

8.  执行命令安装huawei-csi-controller服务。如果Kubernetes版本低于v1.17，删除名称为csi-snapshotter和snapshot-controller的容器，并根据[检查CSI依赖的镜像](/docs/安装部署/安装前准备/检查CSI依赖的镜像)中的版本要求，修改其它容器镜像版本。

    ```
    kubectl apply -f ./deploy/huawei-csi-controller.yaml
    ```

9.  执行命令安装huawei-csi-node服务。

    ```
    kubectl apply -f ./deploy/huawei-csi-node.yaml 
    ```

10. 执行命令检查服务是否启动。

    ```
    kubectl get pod -n huawei-csi
    ```

    回显示例如下，Pod状态为“Running“则安装成功。

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-68745d489c-v5xkj   9/9     Running   0          13m
    huawei-csi-node-4hbqp                    3/3     Running   0          13m
    huawei-csi-node-f7dkf                    3/3     Running   0          13m
    huawei-csi-node-xrntc                    3/3     Running   0          13m
    ```

>![](/css-docs/public_sys-resources/zh/icon-note.gif) 
>多副本controller部署场景下可以通过修改 _./deploy/huawei-csi-controller.yaml_ 文件中Deployment资源的spec.replica字段来指定副本个数，修改完成后，执行以下命令生效：
>```
>kubectl apply -f ./deploy/huawei-csi-controller.yaml
>```

