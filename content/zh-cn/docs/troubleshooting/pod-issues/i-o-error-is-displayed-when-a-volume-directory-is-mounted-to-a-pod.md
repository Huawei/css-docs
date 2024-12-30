---
title: "Pod挂载卷目录提示I/O error"
linkTitle: "Pod挂载卷目录提示I/O error"
description: 
weight: 8
---

## 现象描述{#section16564369537}

Pod对所挂载卷进行读写时，提示I/O error。

## 根因分析{#section135642617536}

使用SCSI等协议时，如果Pod持续往挂载目录写入数据时，存储发生重启，导致主机上设备到存储的链路中断，触发I/O error。存储恢复时，挂载目录仍然为只读。

## 解决措施{#section75642613539}

重新挂载该卷，即通过重建Pod可以触发重新挂载。

