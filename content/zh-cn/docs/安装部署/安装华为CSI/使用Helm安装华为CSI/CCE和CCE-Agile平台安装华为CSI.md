---
title: "CCE和CCE Agile平台安装华为CSI"
linkTitle: "CCE和CCE Agile平台安装华为CSI"
description: 
weight: 2
---

本章节介绍如何在CCE / CCE Agile平台安装华为CSI。

## 制作Helm安装包{#section2032812215509}

CCE和CCE Agile平台无法直接通过Helm安装华为CSI，需要手动制作Helm安装包后上传至平台模板市场进行安装。

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录已部署Helm的任意节点。
2.  将华为CSI组件包中的"helm"目录拷贝到节点的任意目录下。Helm工具路径请参见[表 软件包组件描述](/docs/安装部署/安装前准备/下载华为CSI软件包#zh-cn_topic_0150885197_table17200162435412)。
3.  进入到helm的工作目录下。

    ```
    cd helm/
    ```

4.  修改helm/esdk/values.yaml文件中kubeletConfigDir和csiDriver.driverName参数。

    ```
    vi ./esdk/values.yaml
    ```

    修改如下参数：

    ```yaml
    # Specify kubelet config dir path.
    # kubernetes and openshift is usually /var/lib/kubelet
    # Tanzu is usually /var/vcap/data/kubelet
    # CCE is usually /mnt/paas/kubernetes/kubelet
    kubeletConfigDir: /mnt/paas/kubernetes/kubelet
    
    # The CSI driver parameter configuration
    csiDriver:
      # Driver name, it is strongly recommended not to modify this parameter
      # The CCE platform needs to modify this parameter, e.g. csi.oceanstor.com
      driverName: csi.oceanstor.com
    ```

5.  执行命令制作Helm安装包，该命令会将安装包生成到当前路径下。

    ```
    helm package ./esdk/ -d ./
    ```

## 安装华为CSI{#section3411185295111}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录已部署CCE Agile平台master的任意节点。
2.  执行命令创建部署华为CSI的命名空间，huawei-csi为自定义的命名空间。

    ```
    kubectl create namespace huawei-csi
    ```

3.  导出Helm安装包，具体请参考[制作Helm安装包](#section2032812215509)。
4.  在主页单击“模板市场\> 我的模板\>上传模板”，进入上传模板对话框。将导出的Helm安装包导入CCE Agile平台。

    ![](/figures/上传模板-ch.png)

5.  安装包上传完毕，在主页单击“模板市场\>我的模板”，进入我的模板页面，单击“安装\>提交”。其中模板实例名称可自定义填写。

    ![](/figures/安装csi中文.png)

6.  在主页单击“模板市场\>模板实例”，选择安装时指定的项目（例如样例中的项目是“default”）。安装成功后执行状态将回显为“安装成功”。

    ![](/figures/安装结果-ch.png)

