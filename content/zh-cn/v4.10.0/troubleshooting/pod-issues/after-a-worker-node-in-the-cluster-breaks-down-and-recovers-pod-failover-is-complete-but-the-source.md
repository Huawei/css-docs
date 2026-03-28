---
title: "集群中worker节点宕机并恢复后，Pod完成failover，但是Pod所在源主机出现盘符残留"
linkTitle: "集群中worker节点宕机并恢复后，Pod完成failover，但是Pod所在源主机出现盘符残留"
description: 
weight: 1
---

## 现象描述{#zh-cn_topic_0000001133091104_section1566717121452}

worker节点 A上运行Pod, 并通过CSI挂载外置块设备到该Pod；异常掉电节点worker节点A； Kubernetes平台会在感知到节点故障后，将Pod切换至worker节点B；恢复worker节点A， 节点A上的盘符会从正常变为故障。

## 环境配置{#zh-cn_topic_0000001133091104_section87566339513}

Kubernetes版本：1.18及以上

存储类型：块存储

## 根因分析{#zh-cn_topic_0000001133091104_section1425013451056}

worker节点A恢复后，Kubernetes会向存储发起解除映射操作，但是不会发起主机侧的移除盘符操作。在Kubernetes解除映射后，worker节点A上就会出现盘符残留。

## 解决措施或规避方法{#zh-cn_topic_0000001133091104_section350653016492}

目前的解决方法只能人工介入，手动清理掉主机的残留盘符（或者再次重启主机，利用主机重启过程中扫盘机制，清理掉残留盘符）。具体方法如下：

1.  <a name="zh-cn_topic_0000001133091104_li195731859152815"></a>排查主机的残留盘符。
    1.  <a name="zh-cn_topic_0000001133091104_li177163210119"></a>执行命令，判断是否存在多路径状态异常的DM多路径设备：

        ```
        multipath -ll
        ```

        命令结果示例如下。路径状态为failed faulty running表示异常，对应的DM多路径设备为dm-12，关联的SCSI磁盘为sdi和sdj，在配置多条路径时，会有多个SCSI磁盘。记录这些SCSI磁盘。

        ```
        mpathb (3618cf24100f8f457014a764c000001f6) dm-12 HUAWEI  ,XSG1            
        size=100G features='0' hwhandler='0' wp=rw
        `-+- policy='service-time 0' prio=-1 status=active
          |- 39:0:0:1        sdi 8:48  failed faulty running
          `- 38:0:0:1        sdj 8:64  failed faulty running
        ```

        -   **是**  =\> 继续执行[步骤1.2](#zh-cn_topic_0000001133091104_li4217105512811)。
        -   **否**  =\> 不涉及。

    2.  <a name="zh-cn_topic_0000001133091104_li4217105512811"></a>执行以下命令，判断残留的DM多路径设备是否可读。

        ```
        dd if=/dev/dm-12 of=/dev/null count=1 bs=1M iflag=direct
        ```

        命令结果示例如下。如果返回结果为：Input/output error，且读取数据为“0 bytes \(0 B\) copied”，表示该设备不可读。其中，_dm-xx_为[步骤1.1](#zh-cn_topic_0000001133091104_li177163210119)查到的设备号：

        ```
        dd: error reading '/dev/dm-12': Input/output error
        0+0 records in
        0+0 records out
        0 bytes (0 B) copied, 0.0236862 s, 0.0 kB/s
        ```

        -   **是**  =\>  **记录残留的dm-xx设备以及关联磁盘号（见[步骤1.1](#zh-cn_topic_0000001133091104_li177163210119)），执行清理步骤**。
        -   **命令卡死**  =\> 继续执行[步骤1.3](#zh-cn_topic_0000001133091104_li6716192111111)
        -   **其他**  =\> 联系技术支持。

    3.  <a name="zh-cn_topic_0000001133091104_li6716192111111"></a>在另一窗口再次登录该节点。
        1.  执行以下命令，查看卡死的进程。

            ```
            ps -ef | grep dm-12 | grep -w dd
            ```

            命令结果示例如下：

            ```
            root     21725  9748  0 10:33 pts/10   00:00:00 dd if=/dev/dm-12 of=/dev/null count=1 bs=10M iflag=direct
            ```

        2.  将该pid杀死。

            ```
            kill -9 pid
            ```

        3.  记录残留的dm-xx设备以及关联磁盘号（见[步骤1.1](#zh-cn_topic_0000001133091104_li177163210119)），执行清理步骤。

2.  清理主机的残留盘符。
    1.  根据[步骤1](#zh-cn_topic_0000001133091104_li195731859152815)获取的DM多路径设备，执行命令，清理残留的多路径聚合设备信息。

        ```
        multipath -f /dev/dm-12
        ```

        如果执行报错，请联系技术支持。

    2.  清理残留的SCSI磁盘，根据[步骤1](#zh-cn_topic_0000001133091104_li195731859152815)获取的残留磁盘的盘符，依次执行命令：

        ```
        echo 1 > /sys/block/xxxx/device/delete
        ```

        配置多条多路径时，依次根据盘符清除，本次残留路径为sdi/sdj：

        ```
        echo 1 > /sys/block/sdi/device/delete
        echo 1 > /sys/block/sdj/device/delete
        ```

        如果执行报错，请联系技术支持。

    3.  确认DM多路径设备和SCSI磁盘信息是否已经清理干净。

        依次执行下列命令，查询的多路径和磁盘信息显示，残留的dm-12和SCSI磁盘sdi/sdj均已消失，则证明清理完成。

        1.  查看多路径信息。

            ```
            multipath -ll
            ```

            命令结果示例如下，残留的dm-12已消失：

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

        2.  查看设备信息。

            ```
            ls -l /sys/block/
            ```

            命令结果示例如下，SCSI磁盘sdi/sdj均已消失：

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

        3.  查看磁盘信息

            ```
            ls -l /dev/disk/by-id/
            ```

            命令结果示例如下，SCSI磁盘sdi/sdj均已消失：

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

