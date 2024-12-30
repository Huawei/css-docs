---
title: "创建临时卷失败"
linkTitle: "创建临时卷失败"
description: 
weight: 4
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

创建[通用临时卷](https://kubernetes.io/docs/concepts/storage/ephemeral-volumes/#generic-ephemeral-volumes)失败，报错PodSecurityPolicy: unable to admit pod: \[spec.volumes\[0\]: Invalid value: "ephemeral": ephemeral volumes are not allowed to be used spec.volumes\[0\]

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

当前使用的PSP策略中没有使用“ephemeral”卷的权限。

## 解决措施或规避方法{#zh-cn_topic_0000001279996521_section164471213145410}

在默认PSP "pks-privileged"和"pks-restricted"中增加使用“ephemeral”卷的权限，以修改"pks-privileged"举例：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行命令， 修改pks-privileged的配置。

    ```
    kubectl edit psp pks-privileged
    ```

3.  在spec.volumes中增加“ephemeral”，示例如下：

    ```yaml
    # Please edit the object below. Lines beginning with a '#' will be ignored,
    # and an empty file will abort the edit. If an error occurs while saving this file will be
    # reopened with the relevant failures.
    #
    apiVersion: policy/v1beta1
    kind: PodSecurityPolicy
    metadata:
      annotations:
        apparmor.security.beta.kubernetes.io/allowedProfileName: '*'
        seccomp.security.alpha.kubernetes.io/allowedProfileNames: '*'
      creationTimestamp: "2022-10-11T08:07:00Z"
      name: pks-privileged
      resourceVersion: "1227763"
      uid: 2f39c44a-2ce7-49fd-87ca-2c5dc3bfc0c6
    spec:
      allowPrivilegeEscalation: true
      allowedCapabilities:
      - '*'
      supplementalGroups:
        rule: RunAsAny
      volumes:
      - glusterfs
      - hostPath
      - iscsi
      - nfs
      - persistentVolumeClaim
      - ephemeral
    ```

4.  执行命令，确认是否添加成功。

    ```
    kubectl get psp pks-privileged -o yaml
    ```

