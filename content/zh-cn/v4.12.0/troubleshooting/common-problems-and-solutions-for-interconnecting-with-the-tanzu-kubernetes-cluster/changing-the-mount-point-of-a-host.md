---
title: "修改主机挂载点"
linkTitle: "修改主机挂载点"
description: 
weight: 2
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

创建Pod时失败，华为CSI日志中报错“mount point does not exist”。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

huawei-csi-node中的“pods-dir”目录原生Kubernetes集群与Tanzu Kubernetes集群不一致。

## 解决措施或规避方法{#zh-cn_topic_0000001279996521_section164471213145410}

1.  进入helm/esdk/目录，执行**vi values.yaml**命令打开配置文件。

    ```
    vi values.yaml
    ```

2.  将kubeletConfigDir参数修改为kubelet实际的安装目录。

    ```yaml
    # Specify kubelet config dir path.
    # kubernetes and openshift is usually /var/lib/kubelet
    # Tanzu is usually /var/vcap/data/kubelet
    kubeletConfigDir: /var/vcap/data/kubelet
    ```

