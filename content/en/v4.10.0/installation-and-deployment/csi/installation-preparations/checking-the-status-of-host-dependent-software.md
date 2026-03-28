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

-   Check the status of the DataTurbo client. For details, see  [OceanStor DataTurbo 25.1.0 DTFS User Guide](https://support.huawei.com/enterprise/en/doc/EDOC1100483897/84a8a3d5).
-   Check the status of the NFS+ client. For details, see  [NFS+ Client 1.x User Guide](https://support.huawei.com/enterprise/en/doc/EDOC1100359503/1d67959e).

