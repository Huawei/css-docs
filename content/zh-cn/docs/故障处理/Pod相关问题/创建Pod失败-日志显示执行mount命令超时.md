---
title: "创建Pod失败，日志显示执行mount命令超时"
linkTitle: "创建Pod失败，日志显示执行mount命令超时"
description: 
weight: 4
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

创建Pod时，Pod一直处于ContainerCreating状态，此时查看huawei-csi-node的日志信息（详情请参考[如何查看华为CSI日志](/docs/常用操作/信息收集/如何查看华为CSI日志)），日志显示执行mount命令超时。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

原因1：该问题可能由于配置的业务IP网络不通，导致mount命令执行超时失败。

原因2：对于部分操作系统，如Kylin V10 SP1和SP2，使用NFSv3从容器内执行mount命令耗时较长，导致mount命令超时并报错“error: exit status 255”，该问题可能由于容器运行时containerd的LimitNOFILE参数值过大（10亿+）。

原因3：可能由于网络问题导致挂载失败，CSI默认挂载超时时间为30秒，超过30秒仍挂载失败，日志会显示执行mount命令超时。

## 解决措施或规避方法{#zh-cn_topic_0000001279996521_section164471213145410}

1.  执行ping命令判断业务IP网络是否连通，如果无法ping通，则为原因1，请配置可用的业务IP地址，如果可以ping通，则执行[2](#li21141916181411)。
2.  <a name="li21141916181411"></a>进入任意可以执行mount命令的容器中，指定使用NFSv3执行mount命令。如果命令超时，则可能是原因2，继续执行**systemctl status containerd.service**命令查看配置文件路径，然后执行**cat** _/xxx/containerd.service_命令查看配置文件。文件中如果有LimitNOFILE=infinity或LimitNOFILE的值大小为10亿，请执行[3](#li560665881414)。否则请联系华为工程师处理。
3.  <a name="li560665881414"></a>原因2可参考以下方式处理：
    -   尝试使用NFSv4.0及以上协议。
    -   参考[社区修改方案](https://github.com/containerd/containerd/issues/3201)，将LimitNOFILE参数值修改为合适的值。该方案将会重启容器运行时，请评估对业务的影响。

4.  在挂载失败的宿主机手动挂载该文件系统，如果时间超过30秒，需要用户自行排查该宿主机到存储节点网络是否存在问题。mount命令示例如下
    -   执行以下命令创建测试目录。

        ```
        mkdir /tmp/test_mount
        ```

    -   执行mount命令，挂载文件系统，并观察耗时，其中ip:nfs\_share\_path可以从huawei-csi-node日志中获取，详情请参考[如何查看华为CSI日志](/docs/常用操作/信息收集/如何查看华为CSI日志)

        ```
        time mount ip:nfs_share_path /tmp/test_mount
        ```

    -   测试结束，执行以下命令解挂载文件系统

        ```
        umount /tmp/test_mount
        ```

