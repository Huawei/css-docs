---
title: "Failed to Start huawei-csi Services with the Status Displayed as InvalidImageName"
linkTitle: "Failed to Start huawei-csi Services with the Status Displayed as InvalidImageName"
description: 
weight: 3
---

## Symptom{#en-us_topic_0000001205368783_section1566717121452}

The huawei-csi services \(huawei-csi-controller or huawei-csi-node\) cannot be started. After the  **kubectl get pod -A | grep huawei**  command is executed, the command output shows that the service status is  **InvalidImageName**.

```
kubectl get pod -A | grep huawei
```

The following is an example of the command output.

```
huawei-csi     huawei-csi-controller-fd5f97768-qlldc     6/9     InvalidImageName     0          16s
huawei-csi     huawei-csi-node-25txd                     2/3     InvalidImageName     0          15s
```

## Root Cause Analysis{#en-us_topic_0000001205368783_section1425013451056}

In the .yaml configuration files of the controller and node, the Huawei CSI image version number is incorrect. For example:

```
        ...
        - name: huawei-csi-driver
          image: huawei-csi:4.5.0
        ...
```

## Solution or Workaround{#en-us_topic_0000001205368783_section350653016492}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to modify the configuration file of the huawei-csi-node service. Press  **I**  or  **Insert**  to enter the insert mode and modify related parameters. After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

    ```
    kubectl edit daemonset huawei-csi-node -o yaml -n=huawei-csi
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >-   In  **huawei-csi-driver**  in the sample .yaml file, modify  **image**  to Huawei CSI image  **huawei-csi:4.5.0**.
    >    ```
    >    containers:
    >      ...
    >      - name: huawei-csi-driver
    >        image: huawei-csi:4.5.0
    >    ```

3.  Run the following command to modify the configuration file of the huawei-csi-controller service: Press  **I**  or  **Insert**  to enter the insert mode and modify related parameters. After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

    ```
    kubectl edit deployment huawei-csi-controller -o yaml -n=huawei-csi
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >-   In  **huawei-csi-driver**  in the sample .yaml file, modify  **image**  to Huawei CSI image  **huawei-csi:4.5.0**.
    >    ```
    >    containers:
    >      ...
    >      - name: huawei-csi-driver
    >        image: huawei-csi:4.5.0
    >    ```

4.  Wait until the huawei-csi-node and huawei-csi-controller services are started.
5.  Run the following command to check whether the huawei-csi services are started.

    ```
    kubectl get pod -A  | grep huawei
    ```

    The following is an example of the command output. If the Pod status is  **Running**, the services are started successfully.

    ```
    huawei-csi   huawei-csi-controller-58799449cf-zvhmv   9/9     Running       0          2m29s
    huawei-csi   huawei-csi-node-7fxh6                    3/3     Running       0          12m
    ```

