---
title: "Huawei CSI Services Fail to Be Started and Error Message \"/etc/localtime is not a file\" Is Displayed"
linkTitle: "Huawei CSI Services Fail to Be Started and Error Message \"/etc/localtime is not a file\" Is Displayed"
description: 
weight: 2
---

## Symptom{#en-us_topic_0000001086137838_section1566717121452}

During the installation and deployment of CSI, a Pod fails to run and is in the  **ContainerCreating**  state. Alarm  **/etc/localtime is not a file**  is generated for the Pod.

## Root Cause Analysis{#en-us_topic_0000001086137838_section1425013451056}

When the container mounts the  **/etc/localtime**  file on the host, the type is incorrectly identified. As a result, the container fails to mount the  **/etc/localtime**  file on the host and the Pod cannot run.

## Procedure{#section158611659145513}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  <a name="li131611149192013"></a>Run the following command to check the running status of the Pod of the CSI services.

    ```
    kubectl get pod -n huawei-csi
    ```

    The following is an example of the command output.  _huawei-csi_  indicates the namespace where the CSI services are deployed.

    ```
    NAME                                     READY   STATUS               RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   9/9     ContainerCreating    0          24m
    huawei-csi-controller-6dfcc4b79f-csphc   9/9     ContainerCreating    0          24m
    huawei-csi-node-g6f4k                    3/3     ContainerCreating    0          20m
    huawei-csi-node-tqs87                    3/3     ContainerCreating    0          20m
    ```

3.  Run the following command to check the  **Events**  parameter of the container.

    ```
    kubectl describe pod huawei-csi-controller-6dfcc4b79f-9vjtq -n huawei-csi
    ```

    The following is an example of the command output. In the command,  _huawei-csi-controller-6dfcc4b79f-9vjtq_  indicates the name of the Pod in the  **ContainerCreating**  state found in  [2](#li131611149192013), and  _huawei-csi_  indicates the namespace to which the Pod belongs.

    ```
    ...
    Events:
      Type     Reason       Age                From               Message
      ----     ------       ----               ----               -------
      Normal   Scheduled    96s                default-scheduler  Successfully assigned huawei-csi/huawei-csi-controller-6dfcc4b79f-9vjtq to node1
      Warning  FailedMount  33s (x8 over 96s)  kubelet            MountVolume.SetUp failed for volume "host-time" : hostPath type check failed: /etc/localtime is not a file
    ```

4.  Run the  **cd /helm/esdk/templates**  command to go to the CSI installation package path. For the path, see  [Table 1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).
5.  Take the  **huawei-csi-controller.yaml**  file as an example. Run the following command to view the file content.

    ```
    vi huawei-csi-controller.yaml
    ```

    Find the  **host-time**  configuration item under  **volumes**, and delete the  **type: File**  line. Perform the same operations on the  **huawei-csi-node.yaml**  deployment file that involves the configuration item in the  **templates**  directory.

    ```
    ...
    ...
    volumes:
      - hostPath:
          path: /var/log/
          type: Directory
        name: log
      - hostPath:
          path: /etc/localtime
          type: File
        name: host-time
    ...
    ...
    ```

6.  Uninstall and reinstall the service by referring to  [Uninstallation Using Helm](/docs/installation-and-deployment/csi/uninstallation/uninstallation-using-helm).
7.  Run the following command to check whether the Pod running status of Huawei CSI services is  **Running**.

    ```
    kubectl get pod -n huawei-csi
    ```

    The following is an example of the command output.

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjts   9/9     Running   0          24m
    huawei-csi-controller-6dfcc4b79f-csphb   9/9     Running   0          24m
    huawei-csi-node-g6f41                    3/3     Running   0          20m
    huawei-csi-node-tqs85                    3/3     Running   0          20m
    ```

