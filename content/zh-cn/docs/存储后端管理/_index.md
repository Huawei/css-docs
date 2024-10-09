---
title: "存储后端管理"
linkTitle: "存储后端管理"
description: 
weight: 6
---

后端是华为存储资源的抽象概念，每台华为存储设备可以通过租户/存储池/协议等特性抽象出多个后端资源，每个后端独立存在，其中定义了为Kubernetes集群供应持久卷时所需要的华为存储信息。

本章节用于描述使用oceanctl工具管理存储后端，包括后端的创建/查询/更新/删除操作

## oceanctl工具说明{#zh-cn_topic_0000001324610777_section19453102010152}

-   获取oceanctl工具，将oceanctl工具拷贝到环境目录下,例如（/usr/local/bin），且赋予可执行权限，oceanctl工具位于软件包/bin/oceanctl。
-   oceanctl工具依赖kubectl（Kubernetes平台）或oc（OpenShift平台）命令，因此需要在可执行kubectl或oc命令的节点运行。
-   默认情况下，执行oceanctl命令的用户需要有/var/log目录的读写权限。如果没有该目录权限，可通过“--log-dir=/path/to/custom”指定有权限目录作为日志文件目录。
-   oceanctl创建后端的命名空间默认为huawei-csi。
-   oceanctl命令详细说明请参考[oceanctl命令说明](/docs/存储后端管理/oceanctl命令说明)。




