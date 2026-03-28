---
title: "Modifying the Log Output Mode"
linkTitle: "Modifying the Log Output Mode"
description: 
weight: 5
---

huawei-csi supports two log output modes:  **file**  and  **console**.  **file**  indicates that logs are output to the fixed directory \(**/var/log/huawei**\), and  **console**  indicates that logs are output to the standard directory of the container. You can set the log output mode as required. The default mode is  **file**.

## Procedure{#section130112319346}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  <a name="li1037712113474"></a>Go to the  **/helm/esdk**  directory and run the following command to obtain the original service configuration file.  **helm-huawei-csi**  indicates the Helm chart name specified during the installation of the earlier version, and  **huawei-csi**  indicates the Helm chart namespace specified during the installation of the earlier version. For details about the component package path, see  [Table 1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

3.  Run the  **vi update-values.yaml**  command to open the file obtained in  [2](#li1037712113474)  and modify the configuration items. After the modification, press  **Esc**  and enter  **:wq!**  to save the modification.

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

4.  Run the following command to update the log configuration.

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi  -f ./update-values.yaml
    ```

