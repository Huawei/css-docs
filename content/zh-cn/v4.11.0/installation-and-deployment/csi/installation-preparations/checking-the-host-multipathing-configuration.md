---
title: "检查主机多路径配置"
linkTitle: "检查主机多路径配置"
description: 
weight: 5
---

当您计划在容器环境中使用FC/iSCSI/NVMe over RoCE/NVMe over FC协议对华为存储进行访问时，推荐您使用主机多路径软件增强主机和存储的链路冗余和性能。如果您不准备使用多路径软件，请跳过本章节。

华为CSI软件支持对接的操作系统和多路径软件请参考[兼容性和特性](/docs/compatibility-and-features)章节中的操作系统兼容性。

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>-   如果您准备使用FC/iSCSI协议对接华为存储时，推荐使用操作系统自带的原生DM-Multipath。
>-   如果您准备使用NVMe over RoCE/NVMe over FC协议对接华为存储时，推荐使用华为自研的UltraPath-NVMe。
>-   如果您使用SCSI协议对接华为存储时，请关闭操作系统自带的DM-Multipath。

## 前提条件{#section43820464358}

主机多路径软件已经被正确的安装在主机上。

-   如果您使用的是操作系统自带的原生DM-Multipath，请咨询您的主机或操作系统提供商获取安装所需的资料和软件包。
-   如果您使用的是华为自研的UltraPath或者UltraPath-NVMe，请联系华为工程师获取UltraPath或者UltraPath-NVMe的资料和软件包。软件包版本请参考[兼容性和特性](/docs/compatibility-and-features)章节中的操作系统兼容性。

## 操作步骤{#section14674125816351}

-   如果您使用iSCSI/FC协议对接华为企业存储，请参考[OceanStor Dorado & OceanStor在Red Hat下的主机连通性指南](https://support.huawei.com/enterprise/zh/doc/EDOC1100112792/e369b5d4)，对主机多路径进行配置和检查。
-   如果您使用NVMe over RoCE/NVMe over FC协议对接华为企业存储，请参考[OceanStor Dorado & OceanStor在Red Hat下的主机连通性指南](https://support.huawei.com/enterprise/zh/doc/EDOC1100112792/2bb03fdc)，对主机多路径进行配置和检查。
-   如果您使用iSCSI协议对接华为分布式存储，请参考  [《FusionStorage 8.0.1 块存储基础业务配置指南》](https://support.huawei.com/enterprise/zh/doc/EDOC1100115351)中的“应用服务器配置多路径”章节，对主机多路径进行配置和检查。
-   如果您使用了操作系统原生多路径时，需要检查/etc/multipath.conf文件是否存在如下配置：

    ```
    defaults {
            user_friendly_names yes
            find_multipaths no
    }
    ```

    如果配置不存在，请在/etc/multipath.conf文件开始处增加该配置项。

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >user\_friendly\_names 和find\_multipaths 的参数作用请参考：[dm\_multipath/config\_file\_defaults](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/dm_multipath/config_file_defaults)

