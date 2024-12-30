---
title: "上传华为CSI镜像"
linkTitle: "上传华为CSI镜像"
description: 
weight: 2
---

华为提供huawei-csi镜像供用户使用，镜像文件获取请参考[下载华为CSI软件包](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package)。

为了后续在容器管理平台中可以使用CSI镜像，需要按照以下方式中的一种提前将CSI镜像导入到集群中：

-   使用Docker工具，将CSI镜像上传至镜像仓库（推荐）。
-   手动将CSI镜像导入到所有需要部署华为CSI的节点。

## 上传镜像到镜像仓库{#section93821739143119}

安装华为CSI依赖如下华为提供的镜像文件，请按照说明依次导入并上传下列镜像文件，镜像文件获取请参考[下载华为CSI软件包](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package)。

-   huawei-csi-v4.6.0-arch.tar
-   storage-backend-controller-v4.6.0-_arch_.tar
-   storage-backend-sidecar-v4.6.0-_arch_.tar
-   huawei-csi-extender-v4.6.0-arch.tar

**前提条件**

已准备一台已安装Docker的Linux主机，且该主机支持访问镜像仓库。

**操作步骤**

1.  执行以下命令，将CSI镜像导入当前节点。其中，arch为X86、ARM或PPC64LE。

    ```
    docker load -i huawei-csi-v4.6.0-<arch>.tar 
    ```

2.  执行以下命令，添加镜像仓库地址到镜像标签。其中repo.huawei.com表示镜像仓库的地址。

    ```
    docker tag huawei-csi:4.6.0 <repo.huawei.com>/huawei-csi:4.6.0
    ```

3.  执行以下命令，将CSI镜像上传到镜像仓库。其中repo.huawei.com表示镜像仓库的地址。

    ```
    docker push <repo.huawei.com>/huawei-csi:4.6.0
    ```

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   也可以使用containerd来进行镜像的导入和上传。
>-   CCE或CCE Agile平台请参考该平台用户手册完成镜像导入和上传。

## 上传镜像到本地节点{#section15439218133113}

若镜像已上传至镜像仓库，则跳过本章节。

**前提条件**

-   该节点已获取对应的华为CSI镜像文件，镜像文件获取请参考[下载华为CSI软件包](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package)。
-   该节点已经安装Docker或其他容器引擎。

**操作步骤**

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录需要导入镜像的节点。
2.  将Kubernetes CSI组件包中的"image"目录拷贝到当前节点的任意目录下。
3.  执行**cd image**命令，进入到image的工作目录。工具路径请参见[表1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。
4.  执行命令依次将image目录下的所有华为CSI镜像导入至本地节点，其中  _name_  参数是镜像tar包的名字。

    使用Docker容器引擎执行：

    ```
    docker load -i <name>.tar
    ```

    使用containerd容器引擎执行：

    ```
    ctr -n k8s.io image import <name>.tar
    ```

    使用Podman容器引擎执行：

    ```
    podman load -i <name>.tar
    ```

    >![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
    >当节点主机安装的是其他容器引擎时，请使用对应容器引擎的导入镜像命令。

