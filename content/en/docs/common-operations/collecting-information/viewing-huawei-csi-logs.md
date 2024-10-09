---
title: "Viewing Huawei CSI Logs"
linkTitle: "Viewing Huawei CSI Logs"
description: 
weight: 2
---

## Viewing Logs of the huawei-csi-controller Service{#en-us_topic_0000001191906803_section5326743451}

1.  Run the following command to obtain the node where huawei-csi-controller is located.

    ```
    kubectl get pod -A -o wide | grep huawei
    ```

    The following is an example of the command output, where  **IP**  indicates the node IP address and  **NODE**  indicates the node name.

    ```
    NAME                                    READY   STATUS    RESTARTS   AGE     IP             NODE         NOMINATED NODE   READINESS GATES
    huawei-csi-controller-695b84b4d8-tg64l  9/9     Running  0          14s     <host1-ip>     <host1-name> <none>           <none>
    ```

2.  Use a remote access tool, such as PuTTY, to log in to the node where the huawei-csi-controller service resides in the Kubernetes cluster through the management IP address.
3.  Go to the log directory.

    ```
    cd /var/log/huawei
    ```

4.  Run the following command to view the customized output logs of the container.

    ```
    vi huawei-csi-controller
    ```

5.  Go to the container directory.

    ```
    cd /var/log/containers
    ```

6.  Run the following command to view the standard output logs of the container.

    ```
    vi huawei-csi-controller-<name>_huawei-csi_huawei-csi-driver-<contrainer-id>.log
    ```

## Viewing Logs of the huawei-csi-node Service{#en-us_topic_0000001191906803_section66851055357}

1.  Run the following command to obtain the node where huawei-csi-node is located.

    ```
    kubectl get pod -A -o wide | grep huawei
    ```

    The following is an example of the command output, where  **IP**  indicates the node IP address and  **NODE**  indicates the node name.

    ```
    NAME                     READY   STATUS    RESTARTS   AGE     IP             NODE         NOMINATED NODE   READINESS GATES
    huawei-csi-node-g6f7z    3/3     Running  0          14s     <host2-ip>     <host2-name> <none>           <none>
    ```

2.  Use a remote access tool, such as PuTTY, to log in to the node where the huawei-csi-node service resides in the Kubernetes cluster through the management IP address.
3.  Go to the log directory.

    ```
    cd /var/log/huawei
    ```

4.  Run the following command to view the customized output logs of the container.

    ```
    vi huawei-csi-node
    ```

5.  Go to the container directory.

    ```
    cd /var/log/containers
    ```

6.  Run the following command to view the standard output logs of the container.

    ```
    vi huawei-csi-node-<name>_huawei-csi_huawei-csi-driver-<contrainer-id>.log
    ```

