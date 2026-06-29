---
title: "Updating the huawei-csi-controller or huawei-csi-node Service"
linkTitle: "Updating the huawei-csi-controller or huawei-csi-node Service"
description: 
weight: 4
---

Perform this operation when you need to update the huawei-csi-controller or huawei-csi-node service, for example, changing the number of copies for the huawei-csi-controller service.

## Procedure{#section1452416823017}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  <a name="li1037712113474"></a>Go to the  **/helm/esdk**  directory and run the following command to obtain the original service configuration file.  **helm-huawei-csi**  indicates the Helm chart name specified during the installation of the earlier version, and  **huawei-csi**  indicates the Helm chart namespace specified during the installation of the earlier version. For details about the component package path, see  [Table 1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

3.  Run the  **vi update-values.yaml**  command to open the file obtained in  [2](#li1037712113474)  and modify the configuration items by referring to  [Parameters in the values.yaml File of Helm](/docs/installation-and-deployment/csi/installation/installation-using-helm/parameters-in-the-values-yaml-file-of-helm). After the modification, press  **Esc**  and enter  **:wq!**  to save the modification.
4.  Run the following command to update Huawei CSI services.

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi  -f ./update-values.yaml
    ```

