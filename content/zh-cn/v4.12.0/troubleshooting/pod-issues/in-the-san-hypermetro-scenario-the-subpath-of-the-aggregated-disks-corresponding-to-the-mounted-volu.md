---
title: "SAN双活场景，已挂载的卷对应聚合盘的子路径丢失"
linkTitle: "SAN双活场景，已挂载的卷对应聚合盘的子路径丢失"
description: 
weight: 13
---

## 现象描述{#zh-cn_topic_0234872004_section1566717121452}

已挂载的资源对应聚合盘的子路径丢失。

## 根因分析{#zh-cn_topic_0234872004_section1425013451056}

**图 1**  SAN双活子路径丢失故障示意图<a name="fig18307183116559"></a>  
![](/css-docs/figures/SAN双活子路径丢失故障示意图.png "SAN双活子路径丢失故障示意图")

如[图1](#fig18307183116559)所示，当HBA卡/网卡异常，交换机/网络抖动，存储阵列业务端口故障等因素导致主机与存储一端链路断开后，主机发生重启并触发重新扫盘，此时主机上缺失已故障一端存储的链路。待故障恢复后，由于主机重新扫盘后，链路信息已丢失，缺失的链路不会自动恢复。

想要恢复缺失的链路，通常可以通过漂移Pod到其他主机方式，交由CSI自动重新挂载，并补齐缺失的链路。若需手动在当前主机上恢复缺失链路，请参考以下方法。

## 解决措施或规避方法（iSCSI协议）{#zh-cn_topic_0234872004_section350653016492}

1.  执行以下命令，查询主机上对应业务IP的iSCSI节点是否存在，其中"192.168.1.100"为业务IP。若节点存在则跳转到[3](#li231010151716)，不存在则到[2](#li15574133618113)。

    ```
    iscsiadm -m node | grep 192.168.1.100
    ```

2.  <a name="li15574133618113"></a>执行以下命令，发现iSCSI节点。

    ```
    iscsiadm -m discovery -t st -p 192.168.1.100
    ```

3.  <a name="li231010151716"></a>执行以下命令，登录iSCSI节点。

    ```
    iscsiadm -m node -p 192.168.1.100 -l
    ```

4.  <a name="li1059255014315"></a>执行以下命令，并根据对应的业务IP，查找其下iSCSI host编号。

    ```
    iscsiadm -m session -P3
    ```

5.  <a name="li385110117351"></a>登录存储DM界面，通过服务-\>主机组-\>主机-\>映射，找到lun对应的主机LUN ID
6.  执行以下扫盘命令，补齐缺失的链路，其中"host\_lun\_id"为[5](#li385110117351)中找到的主机LUN ID，"host\_no"为[4](#li1059255014315)中获取的host编号

    ```
    echo "- - <host_lun_id>" > /sys/class/scsi_host/host<host_no>/scan
    ```

7.  执行以下命令，查看链路是否已经补齐

    ```
    multipath -ll
    ```

## 解决措施或规避方法（FC协议）{#section133691529119}

1.  <a name="li1051181216016"></a>执行以下命令，查找所有当前主机上的FC启动器

    ```
    cat /sys/class/fc_host/host*/port_name | awk 'BEGIN{FS="0x";ORS=" "}{print $2}'
    ```

2.  <a name="li68321471013"></a>执行以下命令，查找路径缺失启动器下对应的host编号，其中"port\_name"为[1](#li1051181216016)中获取的启动器名称

    ```yaml
    for h in /sys/class/fc_host/host*; do echo $h: $(cat $h/port_name); done | grep <port_name>
    ```

3.  <a name="li01848139518"></a>登录存储DM界面，通过服务-\>主机组-\>主机-\>映射，找到lun对应的主机LUN ID
4.  执行以下扫盘命令，补齐缺失的链路，其中"host\_lun\_id"为[3](#li01848139518)中找到的主机LUN ID，"host\_no"为[2](#li68321471013)中获取的host编号

    ```
    echo "- - <host_lun_id>" > /sys/class/scsi_host/host<host_no>/scan
    ```

5.  执行以下命令，查看链路是否已经补齐

    ```
    multipath -ll
    ```

