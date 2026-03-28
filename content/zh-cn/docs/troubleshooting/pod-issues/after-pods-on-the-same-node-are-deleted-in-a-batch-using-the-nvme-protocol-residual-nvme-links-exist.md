---
title: "使用nvme协议，批量删除同一节点上Pod后，节点上nvme链路残留"
linkTitle: "使用nvme协议，批量删除同一节点上Pod后，节点上nvme链路残留"
description: 
weight: 12
---

## 现象描述{#zh-cn_topic_0234872004_section1566717121452}

nvme协议场景，批量删除同一节点的Pod，Pod成功删除，但节点上nvme链路没有被清理干净

```
# nvme list-subsys
nvme-subsys0 - NQN=nqn.xxx.nvme:nvm-subsystem-sn-xxxxxxx
\
 +- nvme0 tcp traddr=xxx.xxx.xxx.xxx,trsvcid=4420,src_addr=xxx.xxx.xxx.xxx live 
 +- nvme1 tcp traddr=xxx.xxx.xxx.xxx,trsvcid=4420,src_addr=xxx.xxx.xxx.xxx live 
```

## 根因分析{#zh-cn_topic_0234872004_section1425013451056}

使用nvme协议，只有主机与存储资源解映射完成后，主机上的设备路径才会被清理。在多个Pod挂载同一个卷，且执行批量删除的场景下，CSI在解挂载阶段\(NodeUnstageVolume\)无法感知到后续解映射阶段\(ControllerUnpublishVolume\)的设备路径清理情况，导致无法及时清理nvme链路。

## 解决措施或规避方法{#zh-cn_topic_0234872004_section350653016492}

1.  nvme链路残留不影响CSI功能使用，但是会导致后续挂载的存储资源按照当前残留的链路扫描出对应的设备路径，若无链路数量减少的要求，则可不处理残留链路。
2.  若需要减少后续挂载时的链路数量，可以手动删除节点上的残留链路。以清理上述现象描述中的链路为例，需要执行以下命令：

    ```
    nvme disconnect -d nvme0
    nvme disconnect -d nvme1
    ```

