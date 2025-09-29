---
title: "检查主机依赖软件状态"
linkTitle: "检查主机依赖软件状态"
description: 
weight: 6
---

本章节介绍如何检查集群中工作节点上主机依赖软件状态是否正常。以主机操作系统为CentOS 7.9 x86\_64为例。

-   检查iSCSI客户端状态。

    ```
    systemctl status iscsi iscsid 
    ```

-   检查NFS客户端状态。

    ```
    systemctl status rpcbind 
    ```

-   检查DM-Multipath多路径软件状态。

    ```
    systemctl status multipathd.socket multipathd
    ```

-   检查UltraPath多路径软件状态。

    ```
    systemctl status nxup
    ```

-   检查UltraPath-NVMe多路径软件状态。

    ```
    systemctl status upudev upService_plus
    ```

-   检查DataTurbo客户端状态，请参考[《OceanStor DataTurbo 25.1.0 DTFS用户指南》](https://support.huawei.com/enterprise/zh/doc/EDOC1100483896/5c81c74a?idPath=7919749|251366268|250389224|263153904|264568316)。
-   检查NFS+客户端状态，请参考[《NFS+客户端 1.x 用户指南》](https://support.huawei.com/enterprise/zh/doc/EDOC1100359502/c54ef101)。

