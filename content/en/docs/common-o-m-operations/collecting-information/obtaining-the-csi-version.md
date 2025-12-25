---
title: "Obtaining the CSI Version"
linkTitle: "Obtaining the CSI Version"
description: 
weight: 1
---

This section describes how to view the CSI version.

## Procedure{#section1883055741114}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to query information about the node where huawei-csi-node resides.

    ```
    kubectl get pod -A  -owide | grep huawei-csi-node
    ```

    The following is an example of the command output.

    ```
    NAMESPACE     NAME                                       READY   STATUS    RESTARTS        AGE     IP               NODE            NOMINATED NODE   READINESS GATES
    huawei-csi    huawei-csi-node-87mss                      3/3     Running   0               6m41s   192.168.129.155      node-1          <none>           <none>
    huawei-csi    huawei-csi-node-xp8cc                      3/3     Running   0               6m41s   192.168.129.156      node-2          <none>           <none
    ```

3.  Use a remote access tool, such as PuTTY, to log in to any node where huawei-csi-node resides through the node IP address.
4.  Run the following command to view the CSI version.

    ```
    cat /var/lib/kubelet/plugins/csi.huawei.com/version
    ```

    The version information is displayed as follows:

    ```
    4.10.0
    ```

