---
title: "Kubernetes、OpenShift、Tanzu回退华为CSI"
linkTitle: "Kubernetes、OpenShift、Tanzu回退华为CSI"
description: 
weight: 1
---

## 前提条件{#section12493103133711}

-   已使用Helm 3完成CSI的更新。

## 操作步骤{#section1015846181614}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  进入到helm/esdk的工作目录下，目录路径请参见[表1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。

    ```
    cd helm/esdk
    ```

3.  <a name="li92161141175717"></a>执行命令，查看Helm部署CSI服务的历史版本。

    ```
    helm history helm-huawei-csi -n huawei-csi 
    ```

    命令结果示例如下：

    ```
    REVISION        UPDATED                         STATUS          CHART           APP VERSION     DESCRIPTION     
    1       	Mon Jan  8 04:15:40 2024	superseded	esdk-4.4.0	4.4.0      	Install complete
    2       	Mon Jan  8 04:16:12 2024	deployed  	esdk-4.8.0	4.8.0      	Upgrade complete
    ```

4.  执行命令，回退CSI服务到指定版本。

    其中，revision-number为[3](#li92161141175717)查询到的版本号。例如版本为：1。

    ```
    helm rollback helm-huawei-csi -n huawei-csi 1
    ```

    命令结果示例如下，回显中有Rollback was a success，则表示回退CSI服务到指定版本成功。

    ```
    Rollback was a success! Happy Helming!
    ```

