---
title: "Collecting Logs"
linkTitle: "Collecting Logs"
description: 
weight: 3
---

## Performing Check Before Collection{#section298992810393}

1.  Use a remote access tool, such as PuTTY, to log in to the node where the oceanctl tool is installed in the Kubernetes cluster through the management IP address.
2.  Run the following command. The displayed version is  **v4.8.0**.

    ```
    oceanctl version
    ```

    The following is an example of the command output.

    ```yaml
    Oceanctl Version: v4.8.0
    ```

3.  Run the  **oceanctl collect logs --help**  command. The following information is displayed.

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

4.  Run the following command to check whether a Pod is started properly. In the command,  _huawei-csi_  indicates the namespace for installing CSI.

    ```
    kubectl get deployment -n huawei-csi
    ```

    The following is an example of the command output.

    ```
    NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
    huawei-csi-controller   1/1     1            1           21h
    ```

## Collecting All Logs in the CSI Namespace Using oceanctl{#section8464164063912}

1.  Use a remote access tool, such as PuTTY, to log in to the node checked in  [Performing Check Before Collection](#section298992810393)  through the management IP address.
2.  Run the  **oceanctl collect logs -n <namespace\> -a --threads-max=**_<max\_node\_processing\_num\>_  command to collect CSI logs of all nodes where CSI containers reside in the cluster. In the command,  **threads-max**  indicates the maximum number of nodes for which logs can be collected at the same time. The default value is  **50**. You can set the value based on the host performance and load.

    ```
    oceanctl collect logs -n huawei-csi -a --threads-max=10
    ```

3.  Check the log package generated in the  **/tmp**  directory. You can run the  **unzip **_<zip\_name\>_** -d collect\_logs**  command to decompress the log package. In the preceding command,  _<zip\_name\>_  indicates the package name.

    ```
    # date
    Wed Sep 20 02:49:24 EDT 2023
    
    # ls
    huawei-csi-2023-09-20-02:48:22-all.zip
    ```

## Collecting the Log of a Single CSI Node Using oceanctl{#section1039148347}

1.  Use a remote access tool, such as PuTTY, to log in to the node checked in  [Performing Check Before Collection](#section298992810393)  through the management IP address.
2.  Run the  **oceanctl collect logs -n **_<namespace\>_** -N **_<nodeName\>_  command to collect CSI logs of all nodes where CSI containers reside in the cluster.

    ```
    oceanctl collect logs -n huawei-csi -N node-1
    ```

3.  Check the log package generated in the  **/tmp**  directory. You can run the  **unzip **_<zip\_name\>_** -d collect\_logs**  command to decompress the log package. In the preceding command,  _<zip\_name\>_  indicates the package name.

    ```
    # date
    Thu Sep 21 04:08:47 EDT 2023
    
    # ls
    huawei-csi-2023-09-21-04:05:15-node-1.zip
    ```

