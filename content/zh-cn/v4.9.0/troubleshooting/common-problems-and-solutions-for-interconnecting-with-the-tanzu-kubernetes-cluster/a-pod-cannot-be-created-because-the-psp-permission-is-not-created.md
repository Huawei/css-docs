---
title: "未创建PSP权限导致Pod无法创建"
linkTitle: "未创建PSP权限导致Pod无法创建"
description: 
weight: 1
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

创建huawei-csi-controller和huawei-csi-node时，仅Deployment和DaemonSet资源创建成功，controller和node的Pod未创建。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

创建资源使用的service account没有PSP策略的“use”权限。

## 解决措施或规避方法{#zh-cn_topic_0000001279996521_section164471213145410}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行**vi** _psp-use.yaml_  命令， 创建psp-use.yaml文件。

    ```
    vi psp-use.yaml
    ```

3.  配置psp-use.yaml文件。

    ```
    apiVersion: rbac.authorization.k8s.io/v1
    kind: ClusterRole
    metadata:
      name: huawei-csi-psp-role
    rules:
    - apiGroups: ['policy']
      resources: ['podsecuritypolicies']
      verbs: ['use']
    ---
    apiVersion: rbac.authorization.k8s.io/v1
    kind: ClusterRoleBinding
    metadata:
      name: huawei-csi-psp-role-cfg
    roleRef:
      kind: ClusterRole
      name: huawei-csi-psp-role
      apiGroup: rbac.authorization.k8s.io
    subjects:
    - kind: Group
      apiGroup: rbac.authorization.k8s.io
      name: system:serviceaccounts:huawei-csi
    - kind: Group
      apiGroup: rbac.authorization.k8s.io
      name: system:serviceaccounts:default
    
    ```

4.  执行以下命令，创建PSP权限。

    ```
    kubectl create -f psp-use.yaml
    ```

