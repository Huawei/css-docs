---
title: "创建Pod失败，日志显示启动器已关联至其他主机"
linkTitle: "创建Pod失败，日志显示启动器已关联至其他主机"
description: 
weight: 10
---

## 现象描述{#zh-cn_topic_0234872004_section1566717121452}

使用SAN存储创建Pod时，Pod一直处于ContainerCreating状态，查看Pod中有打印告警事件：rpc error: code = Internal desc = initiator xxx is already associated to another host。

## 根因分析{#zh-cn_topic_0234872004_section1425013451056}

原因1：CSI会根据一定规则自动创建主机、主机组、启动器，若相同资源在使用CSI前已经在存储侧存在，则会出现冲突。该报错原因可能为使用CSI前已添加过相同的启动器。

原因2：容器集群中，不同工作节点的启动器名称重复，请根据下列步骤进行排查：

1.  登录到容器集群的不同工作节点，执行命令查看启动器名称，确认是否存在不同工作节点使用相同启动器名称。
    -   查看iSCSI启动器名称，执行下列命令：

        ```
        cat /etc/iscsi/initiatorname.iscsi
        ```

    -   查看FC启动器名称，执行下列命令：

        ```
        cat /sys/class/fc_host/host*/port_name
        ```

    -   查看RoCE启动器名称，执行下列命令：

        ```
        cat /etc/nvme/hostnqn
        ```

2.  若存在不同工作节点使用相同启动器名称，请按[解决措施或规避方法](#zh-cn_topic_0234872004_section350653016492)解决。

## 解决措施或规避方法{#zh-cn_topic_0234872004_section350653016492}

1.  确认启动器关联的主机是否存在使用中的卷，若有使用中的卷，需先将使用中的Pod漂移至其他节点。
2.  确认主机中不存在使用中的卷后，修改启动器名称，确保启动器的唯一性。
3.  执行下列命令，重启iscsid服务。

    ```
    systemctl restart iscsid
    ```

    >![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
    >重启iscsid服务可能导致I/O中断，请确保启动器关联的主机中没有正在使用中的卷，再进行重启操作。

4.  重启huawei-csi-node服务。

