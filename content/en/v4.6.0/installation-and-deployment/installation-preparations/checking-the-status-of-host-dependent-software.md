---
title: "Checking the Status of Host-Dependent Software"
linkTitle: "Checking the Status of Host-Dependent Software"
description: 
weight: 6
---

This section describes how to check whether the status of host-dependent software on worker nodes in a cluster is normal. In this example, the host OS is CentOS 7.9 x86\_64.

-   Check the status of the iSCSI client.

    ```
    systemctl status iscsi iscsid 
    ```

-   Check the status of the NFS client.

    ```
    systemctl status rpcbind 
    ```

-   Check the status of DM-Multipath.

    ```
    systemctl status multipathd.socket multipathd
    ```

-   Check the status of UltraPath.

    ```
    systemctl status nxup
    ```

-   Check the status of UltraPath-NVMe.

    ```
    systemctl status upudev upService_plus
    ```

