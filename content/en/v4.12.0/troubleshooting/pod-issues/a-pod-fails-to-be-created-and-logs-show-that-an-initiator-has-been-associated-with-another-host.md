---
title: "A Pod Fails to Be Created and Logs Show That an Initiator Has Been Associated with Another Host"
linkTitle: "A Pod Fails to Be Created and Logs Show That an Initiator Has Been Associated with Another Host"
description: 
weight: 10
---

## Symptom{#en-us_topic_0234872004_section1566717121452}

When a Pod is created using SAN storage, the Pod is always in the  **ContainerCreating**  status. The Pod logs report alarm event "rpc error: code = Internal desc = initiator xxx is already associated to another host".

## Root Cause Analysis{#en-us_topic_0234872004_section1425013451056}

Cause 1: CSI automatically creates hosts, host groups, and initiators based on certain rules. If the same resources exist on the storage side before CSI is used, conflicts will occur. The possible cause is that the same initiator has been added before CSI is used.

Cause 2: In the container cluster, the initiator names of different worker nodes are the same. In this case, perform the following steps to rectify the fault:

1.  Log in to different worker nodes in the container cluster and run the following command to check whether different worker nodes use the same initiator name:
    -   To view the iSCSI initiator name, run the following command:

        ```
        cat /etc/iscsi/initiatorname.iscsi
        ```

    -   To view the FC initiator name, run the following command:

        ```
        cat /sys/class/fc_host/host*/port_name
        ```

    -   To view the RoCE initiator name, run the following command:

        ```
        cat /etc/nvme/hostnqn
        ```

2.  If different worker nodes use the same initiator name, rectify the fault according to  [Solution or Workaround](#en-us_topic_0234872004_section350653016492).

## Solution or Workaround{#en-us_topic_0234872004_section350653016492}

1.  Check whether the host associated with the initiator has volumes in use. If the host has volumes in use, migrate the Pod in use to another node.
2.  After confirming that the host has no volume in use, change the initiator name to ensure that the initiator is unique.
3.  Run the following command to restart the iscsid service.

    ```
    systemctl restart iscsid
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
    >Restarting the iscsid service may cause I/O interruption. Before restarting the service, ensure that the host associated with the initiator has no volume in use.

4.  Restart the huawei-csi-node service.

