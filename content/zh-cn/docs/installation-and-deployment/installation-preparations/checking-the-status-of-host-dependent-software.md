---
title: "检查主机依赖软件状态"
linkTitle: "检查主机依赖软件状态"
description: 
weight: 6
---

本章节介绍如何检查集群中工作节点上主机依赖软件状态是否正常。本例中主机操作系统为CentOS 7.9 x86\_64。

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

