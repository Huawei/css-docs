---
title: "配置ALUA特性"
linkTitle: "配置ALUA特性"
description: 
weight: 10
---

ALUA（Asymmetric Logical Unit Access，非对称逻辑单元访问），是一种多目标器端口访问模型。在多路径状态下，ALUA标准提供了一种将卷的Active/Passive模型呈现给主机的方式。同时还提供了端口的可访问状态切换接口，可用来实现卷工作控制器切换等。例如，卷在一个控制器故障时，可以将该控制器的端口置为Unavailable，支持ALUA的主机多路径软件收到该状态后，会将I/O切换到另一端控制器。






