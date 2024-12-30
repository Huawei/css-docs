---
title: "修改日志输出模式"
linkTitle: "修改日志输出模式"
description: 
weight: 5
---

huawei-csi支持两种日志输出模式，分别是file和console。file指的是输出到固定的日志目录（例如：/var/log/huawei）；console指的是输出到容器标准目录。用户可以根据自身需求自行设置日志输出模式，默认为file.

## 操作步骤{#section130112319346}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  <a name="li1037712113474"></a>进入/helm/esdk 目录，执行以下命令，获取原有服务配置文件。其中helm-huawei-csi为旧版本安装时指定的Helm Chart名称，huawei-csi为旧版本安装时指定的Helm Chart命名空间。组件包路径请参考[表1](/v4.5.0/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

3.  执行**vi update-values.yaml**命令打开[2](#li1037712113474)中获取的文件，修改配置项，修改完成后，按**Esc**，并输入  **:wq!**，保存修改。

    ```yaml
    # The CSI driver parameter configuration
    csiDriver:
      # Driver name, it is strongly recommended not to modify this parameter
      # The CCE platform needs to modify this parameter, e.g. csi.oceanstor.com
      driverName: csi.huawei.com
      # Endpoint, it is strongly recommended not to modify this parameter
      endpoint: /csi/csi.sock
      # DR Endpoint, it is strongly recommended not to modify this parameter
      drEndpoint: /csi/dr-csi.sock
      # Maximum number of concurrent disk scans or detaches, support 1~10
      connectorThreads: 4
      # Flag to enable or disable volume multipath access, support [true, false]
      volumeUseMultipath: true
      # Multipath software used by fc/iscsi. support [DM-multipath, HW-UltraPath, HW-UltraPath-NVMe]
      scsiMultipathType: DM-multipath
      # Multipath software used by roce/fc-nvme. only support [HW-UltraPath-NVMe]
      nvmeMultipathType: HW-UltraPath-NVMe
      # Timeout interval for waiting for multipath aggregation when DM-multipath is used on the host. support 1~600
      scanVolumeTimeout: 3
      # Timeout interval for running command on the host. support 1~600
      execCommandTimeout: 30
      # check the number of paths for multipath aggregation
      # Allowed values:
      #   true: the number of paths aggregated by DM-multipath is equal to the number of online paths
      #   false: the number of paths aggregated by DM-multipath is not checked.
      # Default value: false
      allPathOnline: false
      # Interval for updating backend capabilities. support 60~600
      backendUpdateInterval: 60
      # Huawei-csi-controller log configuration
      controllerLogging:
        # Log record type, support [file, console]
        module: file
        # Log Level, support [debug, info, warning, error, fatal]
        level: info
        # Directory for storing logs
        fileDir: /var/log/huawei
        # Size of a single log file
        fileSize: 20M
        # Maximum number of log files that can be backed up.
        maxBackups: 9
      # Huawei-csi-node log configuration
      nodeLogging:
        # Log record type, support [file, console]
        module: file
        # Log Level, support [debug, info, warning, error, fatal]
        level: info
        # Directory for storing logs
        fileDir: /var/log/huawei
        # Size of a single log file
        fileSize: 20M
        # Maximum number of log files that can be backed up.
        maxBackups: 9
    ```

4.  执行以下命令更新日志配置。

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi  -f ./update-values.yaml
    ```

