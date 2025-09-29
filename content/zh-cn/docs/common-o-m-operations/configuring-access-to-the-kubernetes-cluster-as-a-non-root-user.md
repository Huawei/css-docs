---
title: "配置非root用户访问Kubernetes集群"
linkTitle: "配置非root用户访问Kubernetes集群"
description: 
weight: 7
---

## 操作步骤{#zh-cn_topic_0000001283708426_section11147613122310}

1.  拷贝Kubernetes集群的认证文件，/etc/kubernetes/admin.conf修改为实际使用的认证文件。

    ```
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    ```

2.  修改认证文件的用户与用户组。

    ```
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
    ```

3.  配置当前用户的KUBECONFIG环境变量，以Ubuntu 20.04举例如下。

    ```
    echo "export KUBECONFIG=$HOME/.kube/config" >> ~/.bashrc
    source ~/.bashrc
    ```

