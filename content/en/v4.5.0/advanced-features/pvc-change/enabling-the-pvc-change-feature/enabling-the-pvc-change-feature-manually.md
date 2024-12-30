---
title: "Enabling the PVC Change Feature Manually"
linkTitle: "Enabling the PVC Change Feature Manually"
description: 
weight: 2
---

## Prerequisites{#section10631153612202}

Huawei CSI has been manually installed.

## Procedure{#section810241682811}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Go to the  **manual/esdk**  working directory and run the following command to configure the volume change CRD.

    ```
    kubectl apply -f ./crds/volume-modify/
    ```

3.  Run the following command. For details about the component package path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    kubectl apply -f ./deploy/huawei-csi-controller-extender.yaml
    ```

4.  Run the following command to check whether the services are started.

    ```
    kubectl get pod -n huawei-csi
    ```

    The following is an example of the command output. In the preceding command,  **huawei-csi**  indicates the namespace for deploying Huawei CSI.

    ```
    NAME                                     READY     STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   10/10     Running   0          24m
    huawei-csi-node-tqs87                    3/3       Running   0          24m
    ```

