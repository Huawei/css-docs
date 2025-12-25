---
title: "使用oceanctl工具创建后端失败，报错：context deadline exceeded"
linkTitle: "使用oceanctl工具创建后端失败，报错：context deadline exceeded"
description: 
weight: 1
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

用户使用oceanctl工具创建存储后端失败，控制台回显：“failed to call webhook: xxx :context deadline exceeded; error: exist status 1”。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

创建存储后端时，将会调用CSI提供的webhook服务校验与存储管理网络的连通性和存储账号密码信息，出现该问题原因可能是以下两种原因：

-   华为CSI校验存储管理网络连通性失败。
-   kube-apiserver和CSI webhook通信异常。

## 华为CSI校验存储管理网络连通性失败{#section17680127184319}

请按照以下步骤检查是否是华为CSI校验存储管理网络连通性失败。

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  <a name="li1895283018493"></a>执行命令，获取CSI服务信息。其中，huawei-csi为CSI服务部署的命名空间。

    ```
    kubectl get pod -n huawei-csi -owide
    ```

    命令结果示例如下：

    ```
    NAME                        READY   STATUS    RESTARTS   AGE   IP         NODE       NOMINATED NODE   READINESS GATES
    huawei-csi-controller-xxx   9/9     Running   0          19h   host-ip1   host-1     <none>           <none>
    huawei-csi-node-mnqbz       3/3     Running   0          19h   host-ip1   host-1     <none>           <none>
    ```

3.  登录huawei-csi-controller所在节点，如[2](#li1895283018493)中的host-1。
4.  进入到/var/log/huawei目录。

    ```yaml
    # cd /var/log/huawei
    ```

5.  查看storage-backend-controller日志，以连接存储超时为例。

    ```
    tail -n 1000 storage-backend-controller
    ```

    日志示例如下：

    ```
    2024-01-01 06:30:44.280661 1 [INFO]: Try to login https://192.168.129.155:8088/deviceManager/rest
    2024-01-01 06:31:44.281626 1 [ERROR]: Send request method: POST, Url: https://192.168.129.155:8088/deviceManager/rest/xx/sessions, error: Post "https://192.168.129.155:8088/deviceManager/rest/xx/sessions": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
    2024-01-01 06:31:44.281793 1 [WARNING]: Login https://192.168.129.155:8088/deviceManager/rest error due to connection failure, gonna try another Url
    2024-01-01 06:31:44.291668 1 [INFO]: Finished validateCreate huawei-csi/backend-test.
    2024-01-01 06:31:44.291799 1 [ERROR]: Failed to validate StorageBackendClaim, error: unconnected
    ```

6.  如果日志中有相关登录超时、登录失败或者请求耗时较长，请检查宿主机和存储连通性或网络情况。
7.  如果日志中没有收到任何请求，则是kube-apiserver和CSI webhook通信异常。

## kube-apiserver和CSI webhook通信异常{#section56891019204012}

联系Kubernetes平台管理员查看kube-apiserver与CSI webhook网络问题。例如kube-apiserver存在HTTPS代理时可能无法访问CSI webhook服务。

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>临时规避方案中，将会删除webhook资源，该资源用于在创建存储后端时校验输入的账户信息是否正确和能否和存储建立连接，因此删除该资源仅影响创建后端时的校验，无其他功能影响，但需要注意以下几点。
>-   请保证huawei-csi-controller服务所在宿主机能和存储通信。
>-   请保证输入的账号密码正确。

1.  可执行以下命令查看CSI webhook信息。

    ```
    kubectl get validatingwebhookconfiguration storage-backend-controller.xuanwu.huawei.io
    ```

    命令结果示例如下：

    ```
    NAME                                          WEBHOOKS   AGE
    storage-backend-controller.xuanwu.huawei.io   1          4d22h
    ```

2.  联系Kubernetes平台管理员检查kube-apiserver与CSI webhook是否存在通信异常。
3.  临时规避方案：可执行以下命令删除webhook。

    ```
    kubectl delete validatingwebhookconfiguration storage-backend-controller.xuanwu.huawei.io
    ```

4.  创建存储后端，可参考[存储后端管理](/docs/basic-services/storage-backend-management)。
5.  如果kube-apiserver与CSI webhook通信恢复正常，需要重建webhook，执行以下命令，重启CSI Controller，通过指定“**--replicas=\***”恢复CSI Controller的副本数，下例为恢复至1个，请根据实际情况修改。

    先将副本数修改为0。

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=0 
    ```

    再将副本数恢复为原数量。

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=1
    ```

