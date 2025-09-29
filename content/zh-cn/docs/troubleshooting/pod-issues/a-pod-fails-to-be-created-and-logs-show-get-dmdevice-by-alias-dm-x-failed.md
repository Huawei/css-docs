---
title: "创建Pod失败，日志显示“Get DMDevice by alias: dm-x failed”"
linkTitle: "创建Pod失败，日志显示“Get DMDevice by alias: dm-x failed”"
description: 
weight: 11
---

## 现象描述{#zh-cn_topic_0234872004_section1566717121452}

创建Pod时，Pod长时间处于ContainerCreating状态，此时查看huawei-csi-node的日志信息（详情请参考[如何查看华为CSI日志](/docs/common-o-m-operations/collecting-information/viewing-huawei-csi-logs)），报错：

```
check device: dm-1 is a partition device failed. error: Get DMDevice by alias:dm-1 failed. error: Can not get DMDevice by alias: dm-1
```

## 根因分析{#zh-cn_topic_0234872004_section1425013451056}

DM-Multipath的配置文件中未配置user\_friendly\_names参数为yes。

## 解决措施或规避方法{#zh-cn_topic_0234872004_section350653016492}

1.  确认Pod运行所在工作节点是否存在使用中的卷，若有使用中的卷，需先将使用中的Pod漂移至其他节点。
2.  按照[检查主机多路径配置](/docs/installation-and-deployment/csi/installation-preparations/checking-the-host-multipathing-configuration)章节，配置 /etc/multipath.con 文件。
3.  执行下列命令，重启多路径软件。

    ```
    systemctl reload multipathd.service
    systemctl restart multipathd
    ```

    >![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
    >重启多路径软件可能导致I/O中断，请确保Pod运行所在工作节点中没有正在使用中的卷，再进行重启操作。

