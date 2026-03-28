---
title: "After a Worker Node in the Cluster Breaks Down and Recovers, Pod Failover Is Complete but the Source Host Where the Pod Resides Has Residual Drive Letters"
linkTitle: "After a Worker Node in the Cluster Breaks Down and Recovers, Pod Failover Is Complete but the Source Host Where the Pod Resides Has Residual Drive Letters"
description: 
weight: 1
---

## Symptom{#en-us_topic_0000001133091104_section1566717121452}

A Pod is running on worker node A, and an external block device is mounted to the Pod through CSI. After worker node A is powered off abnormally, the Kubernetes platform detects that the node is faulty and switches the Pod to worker node B. After worker node A recovers, the drive letters on worker node A change from normal to faulty.

## Environment Configuration{#en-us_topic_0000001133091104_section87566339513}

Kubernetes version: 1.18 or later

Storage type: block storage

## Root Cause Analysis{#en-us_topic_0000001133091104_section1425013451056}

After worker node A recovers, Kubernetes initiates an unmapping operation on the storage, but does not initiate a drive letter removal operation on the host. After Kubernetes completes the unmapping, residual drive letters exist on worker node A.

## Solution or Workaround{#en-us_topic_0000001133091104_section350653016492}

Currently, you can only manually clear the residual drive letters on the host. Alternatively, restart the host again and use the disk scanning mechanism during the host restart to clear the residual drive letters. The specific method is as follows:

1.  <a name="en-us_topic_0000001133091104_li195731859152815"></a>Check the residual drive letters on the host.
    1.  <a name="en-us_topic_0000001133091104_li177163210119"></a>Run the following command to check whether a DM multipathing device with abnormal multipathing status exists.

        ```
        multipath -ll
        ```

        The following is an example of the command output. The path status is  **failed faulty running**, the corresponding DM multipathing device is  **dm-12**, and the associated SCSI disks are  **sdi**  and  **sdj**. If multiple paths are configured, multiple SCSI disks exist. Record these SCSI disks.

        ```
        mpathb (3618cf24100f8f457014a764c000001f6) dm-12 HUAWEI  ,XSG1            
        size=100G features='0' hwhandler='0' wp=rw
        `-+- policy='service-time 0' prio=-1 status=active
          |- 39:0:0:1        sdi 8:48  failed faulty running
          `- 38:0:0:1        sdj 8:64  failed faulty running
        ```

        -   If yes, go to  [step 1.2](#en-us_topic_0000001133091104_li4217105512811).
        -   If no, no further action is required.

    2.  <a name="en-us_topic_0000001133091104_li4217105512811"></a>Run the following command to check whether the residual DM multipathing device is readable.

        ```
        dd if=/dev/dm-12 of=/dev/null count=1 bs=1M iflag=direct
        ```

        The following is an example of the command output. If the returned result is  **Input/output error**  and the read data is  **0 bytes \(0 B\) copied**, the device is unreadable.  _dm-xx_  indicates the device ID obtained in  [step 1.1](#en-us_topic_0000001133091104_li177163210119).

        ```
        dd: error reading '/dev/dm-12': Input/output error
        0+0 records in
        0+0 records out
        0 bytes (0 B) copied, 0.0236862 s, 0.0 kB/s
        ```

        -   If yes, record the residual  _dm-xx_  device and associated disk IDs \(for details, see  [step 1.1](#en-us_topic_0000001133091104_li177163210119)\) and perform the clearing operation.
        -   If the command execution is suspended, go to  [step 1.3](#en-us_topic_0000001133091104_li6716192111111).
        -   If other cases, contact technical support engineers.

    3.  <a name="en-us_topic_0000001133091104_li6716192111111"></a>Log in to the node again in another window.
        1.  Run the following command to view the suspended process.

            ```
            ps -ef | grep dm-12 | grep -w dd
            ```

            The following is an example of the command output.

            ```
            root     21725  9748  0 10:33 pts/10   00:00:00 dd if=/dev/dm-12 of=/dev/null count=1 bs=10M iflag=direct
            ```

        2.  Kill the pid.

            ```
            kill -9 pid
            ```

        3.  Record the residual  _dm-xx_  device and associated disk IDs \(for details, see  [step 1.1](#en-us_topic_0000001133091104_li177163210119)\) and perform the clearing operation.

2.  Clear the residual drive letters on the host.
    1.  Run the following command to delete residual multipathing aggregation device information according to the DM multipathing device obtained in  [step 1](#en-us_topic_0000001133091104_li195731859152815).

        ```
        multipath -f /dev/dm-12
        ```

        If an error is reported, contact technical support engineers.

    2.  Run the following command to clear the residual SCSI disks according to the drive letters of the residual disks obtained in  [step 1](#en-us_topic_0000001133091104_li195731859152815).

        ```
        echo 1 > /sys/block/xxxx/device/delete
        ```

        When multiple paths are configured, clear the residual disks based on the drive letters. The residual paths are  **sdi**  and  **sdj**.

        ```
        echo 1 > /sys/block/sdi/device/delete
        echo 1 > /sys/block/sdj/device/delete
        ```

        If an error is reported, contact technical support engineers.

    3.  Check whether the DM multipathing device and SCSI disk information has been cleared.

        Run the following commands in sequence to query the multipathing and disk information. If the residual  **dm-12**  device and SCSI disks  **sdi**  and  **sdj**  are cleared, the clearing is complete.

        1.  View multipathing information.

            ```
            multipath -ll
            ```

            The following is an example of the command output. The residual  **dm-12**  device is cleared.

            ```
            mpathb (3618cf24100f8f457014a764c000001f6) dm-3 HUAWEI  ,XSG1            
            size=100G features='0' hwhandler='0' wp=rw
            `-+- policy='service-time 0' prio=-1 status=active
              |- 39:0:0:1        sdd 8:48  active ready running
              `- 38:0:0:1        sde 8:64  active ready running
            mpathn (3618cf24100f8f457315a764c000001f6) dm-5 HUAWEI  ,XSG1            
            size=100G features='0' hwhandler='0' wp=rw
            `-+- policy='service-time 0' prio=-1 status=active
              |- 39:0:0:2        sdc 8:32  active ready running
              `- 38:0:0:2        sdb 8:16  active ready running
            ```

        2.  View device information.

            ```
            ls -l /sys/block/
            ```

            The following is an example of the command output. SCSI disks  **sdi**  and  **sdj**  are cleared.

            ```
            total 0
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 dm-0 -> ../devices/virtual/block/dm-0
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 dm-1 -> ../devices/virtual/block/dm-1
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 dm-2 -> ../devices/virtual/block/dm-2
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 dm-3 -> ../devices/virtual/block/dm-3
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 sdb -> ../devices/platform/host35/session2/target35:0:0/35:0:0:1/block/sdb
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 sdc -> ../devices/platform/host34/target34:65535:5692/34:65535:5692:0/block/sdc
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 sdd -> ../devices/platform/host39/session6/target39:0:0/39:0:0:1/block/sdd
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 sde -> ../devices/platform/host38/session5/target38:0:0/38:0:0:1/block/sde
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 sdh -> ../devices/platform/host39/session6/target39:0:0/39:0:0:3/block/sdh
            lrwxrwxrwx 1 root root 0 Aug 11 19:56 sdi -> ../devices/platform/host38/session5/target38:0:0/38:0:0:3/block/sdi
            ```

        3.  View disk information.

            ```
            ls -l /dev/disk/by-id/
            ```

            The following is an example of the command output. SCSI disks  **sdi**  and  **sdj**  are cleared.

            ```
            total 0
            lrwxrwxrwx 1 root root 10 Aug 11 19:57 dm-name-mpathb -> ../../dm-3
            lrwxrwxrwx 1 root root 10 Aug 11 19:58 dm-name-mpathn -> ../../dm-5
            lrwxrwxrwx 1 root root 10 Aug 11 19:57 dm-uuid-mpath-3618cf24100f8f457014a764c000001f6 -> ../../dm-3
            lrwxrwxrwx 1 root root 10 Aug 11 19:58 dm-uuid-mpath-3618cf24100f8f457315a764c000001f6 -> ../../dm-5
            lrwxrwxrwx 1 root root  9 Aug 11 19:57 scsi-3618cf24100f8f457014a764c000001f6 -> ../../sdd
            lrwxrwxrwx 1 root root  9 Aug 11 19:57 scsi-3618cf24100f8f45712345678000103e8 -> ../../sdi
            lrwxrwxrwx 1 root root  9 Aug  3 15:17 scsi-3648435a10058805278654321ffffffff -> ../../sdb
            lrwxrwxrwx 1 root root  9 Aug  2 14:49 scsi-368886030000020aff44cc0d060c987f1 -> ../../sdc
            lrwxrwxrwx 1 root root  9 Aug 11 19:57 wwn-0x618cf24100f8f457014a764c000001f6 -> ../../sdd
            lrwxrwxrwx 1 root root  9 Aug 11 19:57 wwn-0x618cf24100f8f45712345678000103e8 -> ../../sdi
            lrwxrwxrwx 1 root root  9 Aug  3 15:17 wwn-0x648435a10058805278654321ffffffff -> ../../sdb
            lrwxrwxrwx 1 root root  9 Aug  2 14:49 wwn-0x68886030000020aff44cc0d060c987f1 -> ../../sdc
            ```

