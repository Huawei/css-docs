---
title: "开启ReadWriteOncePod功能门"
linkTitle: "开启ReadWriteOncePod功能门"
description: 
weight: 6
---

ReadWriteOnce访问模式是Kubernetes v1.22版本为PV和PVC引入的第四种访问模式。如果您使用ReadWriteOncePod访问模式的PVC创建一个Pod，Kubernetes会确保该Pod是整个集群中唯一可以读取或写入该PVC的Pod。

若Kubernetes版本小于v1.29，需要先在kube-apiserver、kube-scheduler和kubelet的feature-gates中开启ReadWriteOncePod特性才能使用。

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>当前CCE或CCE Agile平台不支持开启ReadWriteOncePod功能门

## 操作步骤{#zh-cn_topic_0000001259843616_section137882216292}

1.  为kube-apiserver启用ReadWriteOncePod功能门。
    1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
    2.  执行**vi /etc/kubernetes/manifests/kube-apiserver.yaml**命令，按**I**或**Insert**进入编辑状态，为 kube-apiserver容器添加参数--feature-gates=ReadWriteOncePod=true。修改完成后，按**Esc**，并输入  **:wq!**，保存修改。

        ```
        ...
        spec:
          containers:
          - command:
            - kube-apiserver
            - --feature-gates=ReadWriteOncePod=true
            ...
        ```

        >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
        >在编辑完成后，Kubernetes会自动应用更新，不需要手动更新。

2.  为kube-scheduler启用ReadWriteOncePod功能门。
    1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
    2.  执行**vi /etc/kubernetes/manifests/kube-scheduler.yaml**命令，按**I**或**Insert**进入编辑状态，为kube-scheduler容器添加参数--feature-gates=ReadWriteOncePod=true。修改完成后，按**Esc**，并输入  **:wq!**，保存修改。

        ```
        …
        spec:
          containers:
          - command:
            - kube-scheduler
            - --feature-gates=ReadWriteOncePod=true
            ...
        ```

        >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
        >在编辑完成后，Kubernetes会自动应用更新，不需要手动更新。

3.  为kubelet启用ReadWriteOncePod功能门。

    >![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
    >由于动态Kubelet配置功能在v1.22中已弃用，并且在v1.24中删除，因此集群中每个worker节点上的kubelet都需要执行以下操作。

    1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意worker节点。
    2.  执行**vi /var/lib/kubelet/config.yaml**命令，按**I**或**Insert**进入编辑状态，为KubeletConfiguration对象的featureGates字段添加ReadWriteOncePod: true，如果没有featureGates字段请一并添加。修改完成后，按**Esc**，并输入  **:wq!**，保存修改。

        ```
        apiVersion: kubelet.config.k8s.io/v1beta1
        featureGates:
          ReadWriteOncePod: true
          ...
        ```

        >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
        >kubelet配置文件的默认路径为/var/lib/kubelet/config.yaml，请根据实际情况填写。

    3.  在配置完成后，执行**systemctl restart kubelet**命令重启kubelet。

