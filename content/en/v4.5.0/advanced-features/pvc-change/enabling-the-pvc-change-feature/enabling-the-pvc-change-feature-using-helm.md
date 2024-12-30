---
title: "Enabling the PVC Change Feature Using Helm"
linkTitle: "Enabling the PVC Change Feature Using Helm"
description: 
weight: 1
---

## Prerequisites{#section10631153612202}

-   You have installed Huawei CSI using Helm.
-   Huawei CSI v4.5.0  or later is used.

## Procedure{#section1361061612118}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to check whether the PVC change feature is enabled.

    **helm-huawei-csi**  indicates the Helm chart name specified during installation, and  **huawei-csi**  indicates the Helm chart namespace specified during installation. For details about the component package path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    helm get values helm-huawei-csi -n huawei-csi -a | grep volumeModify -A 1
    ```

    The following is an example of the command output.

    -   If  **enabled: true**  is displayed in the command output, the feature is enabled. In this case, skip the following steps.
    -   If  **enabled: false**  is displayed in the command output, perform the following steps to enable the PVC change feature.

    ```yaml
    volumeModify:
      enabled: false
    ```

3.  Go to the  **/helm/esdk**  directory and run the following command to configure the volume change CRD.

    ```
    # kubectl apply -f ./crds/volume-modify/
    customresourcedefinition.apiextensions.k8s.io/volumemodifyclaims.xuanwu.huawei.io configured
    customresourcedefinition.apiextensions.k8s.io/volumemodifycontents.xuanwu.huawei.io configured
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >If the command output contains  **Warning: resource customresourcedefinitions/volumemodifycontents.xuanwu.huawei.io is missing the kubectl.kubernetes.io/last-applied-configuration...**, you can ignore it. This message is displayed because the  **kubectl create**  command instead of the  **kubectl apply**  command is used for installation by Helm.

4.  <a name="li1230915254221"></a>Run the following command to obtain the original service configuration file.

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

5.  Run the  **vi update-values.yaml**  command to open the file obtained in  [4](#li1230915254221)  and modify the following configuration. After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

    ```yaml
    csiExtender:
      volumeModify:    
        enabled: true
    ```

6.  Run the following command to update Huawei CSI services.

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi  -f ./update-values.yaml
    ```

7.  Run the following command to check whether the services are started.

    ```
    kubectl get pod -n huawei-csi
    ```

    The following is an example of the command output. In the preceding command,  **huawei-csi**  indicates the namespace for deploying Huawei CSI.

    ```
    NAME                                     READY     STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   10/10     Running   0          24m
    huawei-csi-node-tqs87                    3/3       Running   0          20m
    ```

