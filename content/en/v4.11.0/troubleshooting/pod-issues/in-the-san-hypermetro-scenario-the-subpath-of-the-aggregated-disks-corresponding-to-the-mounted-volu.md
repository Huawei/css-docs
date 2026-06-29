---
title: "In the SAN HyperMetro Scenario, the Subpath of the Aggregated Disks Corresponding to the Mounted Volume Is Lost"
linkTitle: "In the SAN HyperMetro Scenario, the Subpath of the Aggregated Disks Corresponding to the Mounted Volume Is Lost"
description: 
weight: 13
---

## Symptom{#en-us_topic_0234872004_section1566717121452}

The subpath of the aggregated disks corresponding to the mounted resource is lost.

## Root Cause Analysis{#en-us_topic_0234872004_section1425013451056}

**Figure  1**  SAN HyperMetro subpath loss<a name="fig18307183116559"></a>  
![](/css-docs/figures/san-hypermetro-subpath-loss.png "san-hypermetro-subpath-loss")

As shown in  [Figure 1](#fig18307183116559), if the link between the host and the storage device is disconnected due to factors such as HBA/NIC exceptions, switch/network jitter, or storage array service port faults, the host restarts and triggers disk scanning again. In this case, the link to the faulty storage device is disconnected on the host. After the fault is rectified, the link information is lost after the host scans the disks again. As a result, the lost link will not be automatically restored.

To restore the link, you can drift over a pod to another host and enable CSI to automatically remount the link. To manually restore the lost link on the current host, perform the following steps:

## Solution or Workaround \(iSCSI Protocol\){#en-us_topic_0234872004_section350653016492}

1.  Run the following command to check whether the iSCSI node corresponding to the service IP address exists on the host. In the command,  **192.168.1.100**  indicates the service IP address. If the node exists, go to  [3](#li231010151716). If the node does not exist, go to  [2](#li15574133618113).

    ```
    iscsiadm -m node | grep 192.168.1.100
    ```

2.  <a name="li15574133618113"></a>Run the following command to discover the iSCSI node:

    ```
    iscsiadm -m discovery -t st -p 192.168.1.100
    ```

3.  <a name="li231010151716"></a>Run the following command to log in to the iSCSI node:

    ```
    iscsiadm -m node -p 192.168.1.100 -l
    ```

4.  <a name="li1059255014315"></a>Run the following command to query the iSCSI host ID based on the corresponding service IP address:

    ```
    iscsiadm -m session -P3
    ```

5.  <a name="li385110117351"></a>Log in to DeviceManager, choose  **Services**  \>  **Host Groups**  \>  **Hosts**  \>  **Mapping**, and find the host LUN ID corresponding to the LUN.
6.  Run the following disk scanning command to supplement the lost link. In the command,  _host\_lun\_id_  indicates the host LUN ID obtained in  [5](#li385110117351), and  _host\_no_  indicates the host ID obtained in  [4](#li1059255014315).

    ```
    echo "- - <host_lun_id>" > /sys/class/scsi_host/host<host_no>/scan
    ```

7.  Run the following command to check whether the link is supplemented:

    ```
    multipath -ll
    ```

## Solution or Workaround \(FC Protocol\){#section133691529119}

1.  <a name="li1051181216016"></a>Run the following command to query all FC initiators on the current host:

    ```
    cat /sys/class/fc_host/host*/port_name | awk 'BEGIN{FS="0x";ORS=" "}{print $2}'
    ```

2.  <a name="li68321471013"></a>Run the following command to query the host ID of the initiator whose path is lost. In the command,  _port\_name_  indicates the initiator name obtained in  [1](#li1051181216016).

    ```yaml
    for h in /sys/class/fc_host/host*; do echo $h: $(cat $h/port_name); done | grep <port_name>
    ```

3.  <a name="li01848139518"></a>Log in to DeviceManager, choose  **Services**  \>  **Host Groups**  \>  **Hosts**  \>  **Mapping**, and find the host LUN ID corresponding to the LUN.
4.  Run the following disk scanning command to supplement the lost link. In the command,  _host\_lun\_id_  indicates the host LUN ID obtained in  [3](#li01848139518), and  _host\_no_  indicates the host ID obtained in  [2](#li68321471013).

    ```
    echo "- - <host_lun_id>" > /sys/class/scsi_host/host<host_no>/scan
    ```

5.  Run the following command to check whether the link has been supplemented:

    ```
    multipath -ll
    ```

