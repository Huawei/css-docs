---
title: "启动huawei-csi-node失败，提示错误为：“/var/lib/iscsi is not a directory”"
linkTitle: "启动huawei-csi-node失败，提示错误为：“/var/lib/iscsi is not a directory”"
description: 
weight: 1
---

## 现象描述{#zh-cn_topic_0000001086137838_section1566717121452}

启动huawei-csi-node时，无法启动huawei-csi-node服务， 使用**kubectl describe daemonset huawei-csi-node -n huawei-csi**命令查看，提示错误为：“/var/lib/iscsi is not a directory”。

## 根因分析{#zh-cn_topic_0000001086137838_section1425013451056}

huawei-csi-node中容器内部无/var/lib/iscsi目录。

## 解决措施或规避方法{#zh-cn_topic_0000001086137838_section350653016492}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  进入Helm工程的目录下，如果无法找到之前的Helm工程，则将组件包中的helm目录拷贝到master节点的任意目录下，组件包路径请参考[表1](/v4.5.0/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。
3.  进入下一级目录templates,找到huawei-csi-node.yaml文件。

    ```
    cd /templates
    ```

4.  执行以下命令，将huawei-csi-node.yaml \> volumes \> iscsi-dir \> hostPath中“path“设置为“/var/lib/iscsi“  ，然后保存并退出文件。

    ```
    vi huawei-csi-node.yaml
    ```

5.  执行以下命令升级Helm chart。升级命令将更新Deployment、DaemonSet和RBAC资源。其中，helm-huawei-csi为自定义的chart名称，huawei-csi为自定义的命名空间。

    ```
    helm upgrade helm-huawei-csi ./  -n huawei-csi -f values.yaml
    ```

    命令结果示例如下：

    ```
    Release "helm-huawei-csi" has been upgraded. Happy Helming!
    NAME: helm-huawei-csi
    LAST DEPLOYED: Thu Jun  9 07:58:15 2022
    NAMESPACE: huawei-csi
    STATUS: deployed
    REVISION: 2
    TEST SUITE: None
    ```

