---
title: "日志收集"
linkTitle: "日志收集"
description: 
weight: 3
---

## 前置检查{#section298992810393}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群内有oceanctl工具的节点。
2.  执行以下命令，显示版本号为**v4.5.0**。

    ```
    oceanctl version
    ```

    命令结果示例如下：

    ```yaml
    Oceanctl Version: v4.5.0
    ```

3.  执行oceanctl collect logs --help命令，返回信息如下。

    ```
    $ oceanctl collect logs --help
    Collect logs of one or more nodes in specified namespace in Kubernetes
    
    Usage:
      oceanctl collect logs [flags]
    
    Examples:
      # Collect logs of all nodes in specified namespace
      oceanctl collect logs -n <namespace>
    
      # Collect logs of specified node in specified namespace
      oceanctl collect logs -n <namespace> -N <node>
    
      # Collect logs of all nodes in specified namespace
      oceanctl collect logs -n <namespace> -a
    
      # Collect logs of all nodes in specified namespace with a maximum of 50 nodes collected at the same time
      oceanctl collect logs -n <namespace> -a --threads-max=50
    
      # Collect logs of specified node in specified namespace
      oceanctl collect logs -n <namespace> -N <node> -a
    
    Flags:
      -a, --all                Collect all nodes messages
      -h, --help               help for logs
      -n, --namespace string   namespace of resources
      -N, --nodename string    Specify the node for which information is to be collected.
          --threads-max int    set maximum number[1~1000] of threads for nodes to be collected. (default 50)
    
    Global Flags:
          --log-dir string   Specify the directory for printing log files. (default "/var/log/huawei")
    ```

4.  执行以下****命令，检查Pod是否正常启动，其中，huawei-csi为CSI安装的命名空间。

    ```
    kubectl get deployment -n huawei-csi
    ```

    命令结果示例如下：

    ```
    NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
    huawei-csi-controller   1/1     1            1           21h
    ```

## 使用oceanctl收集CSI命名空间下所有日志{#section8464164063912}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录[前置检查](#section298992810393)章节中检查的节点。
2.  执行**oceanctl collect logs -n <namespace\> -a --threads-max=**<max\_node\_processing\_num\>命令，收集集群内所有CSI容器所在节点的CSI日志，其中threads-max参数指定了同时收集日志的最大节点数量，默认为50，可以根据主机性能与负载情况配置。

    ```
    oceanctl collect logs -n huawei-csi -a --threads-max=10
    ```

3.  检查/tmp目录下生成的日志压缩包，可以使用**unzip **<zip\_name\>** -d collect\_logs**解压日志压缩包，其中<zip\_name\>为压缩包的名字。

    ```
    # date
    Wed Sep 20 02:49:24 EDT 2023
    
    # ls
    huawei-csi-2023-09-20-02:48:22-all.zip
    ```

## 使用oceanctl收集CSI单个节点日志{#section1039148347}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录[前置检查](#section298992810393)章节中检查的节点。
2.  执行**oceanctl collect logs -n **<namespace\>** -N**  <nodeName\>命令，收集集群内所有CSI容器所在节点的CSI日志。

    ```
    oceanctl collect logs -n huawei-csi -N node-1
    ```

3.  检查/tmp目录下生成的日志压缩包，可以使用**unzip **<zip\_name\>** -d collect\_logs**解压日志压缩包，其中<zip\_name\>为压缩包的名字。

    ```
    # date
    Thu Sep 21 04:08:47 EDT 2023
    
    # ls
    huawei-csi-2023-09-21-04:05:15-node-1.zip
    ```

