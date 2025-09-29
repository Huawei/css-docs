---
title: "如何获取CSI版本信息"
linkTitle: "如何获取CSI版本信息"
description: 
weight: 1
---

本章节指导用户如何查看CSI版本信息。

## 操作步骤{#section1883055741114}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，查看huawei-csi-node所在节点信息。

    ```
    kubectl get pod -A  -owide | grep huawei-csi-node
    ```

    命令结果示例如下：

    ```
    NAMESPACE     NAME                                       READY   STATUS    RESTARTS        AGE     IP               NODE            NOMINATED NODE   READINESS GATES
    huawei-csi    huawei-csi-node-87mss                      3/3     Running   0               6m41s   192.168.129.155      node-1          <none>           <none>
    huawei-csi    huawei-csi-node-xp8cc                      3/3     Running   0               6m41s   192.168.129.156      node-2          <none>           <none
    ```

3.  使用远程访问工具（以PuTTY为例），通过节点IP地址，登录任意huawei-csi-node所在节点。
4.  执行以下命令，查看CSI版本信息。

    ```
    cat /var/lib/kubelet/plugins/csi.huawei.com/version
    ```

    命令显示版本信息如下。

    ```
    4.9.0
    ```

