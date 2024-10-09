---
title: "创建Pod时，Pod的状态为ContainerCreating"
linkTitle: "创建Pod时，Pod的状态为ContainerCreating"
description: 
weight: 2
---

## 现象描述{#zh-cn_topic_0000001163875516_section1566717121452}

执行完成Pod的创建操作，一段时间后，Pod的状态仍然处于ContainerCreating，查看具体日志信息（详情请参考[如何查看华为CSI日志](/docs/常用操作/信息收集/如何查看华为CSI日志)），报错“Fibre Channel volume device not found”。

## 根因分析{#zh-cn_topic_0000001163875516_section1425013451056}

该问题是因为在主机节点有磁盘残留，导致下次创建Pod时，查找磁盘失败。

## 解决措施或规避方法{#zh-cn_topic_0000001163875516_section164471213145410}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  <a name="zh-cn_topic_0000001163875516_li134903196550"></a>执行以下命令，查看Pod所在节点信息。

    ```
    kubectl get pod -o wide
    ```

    命令结果示例如下。

    ```
    NAME        READY   STATUS              RESTARTS   AGE     IP             NODE   NOMINATED NODE   READINESS GATES
    mypod       0/1     ContainerCreating   0          51s     10.244.1.224   node1  <none>           <none>
    ```

3.  删除Pod。
4.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的 _node1_ 节点。_node1_ 节点为[2](#zh-cn_topic_0000001163875516_li134903196550)中查询的节点。
5.  移除盘符残留，详情请参考[解决措施或规避方法](/docs/故障处理/Pod相关问题/集群中worker节点宕机并恢复后-Pod完成failover-但是Pod所在源主机出现盘符残留#zh-cn_topic_0000001133091104_section350653016492)。

