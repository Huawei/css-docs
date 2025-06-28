---
title: "Rolling Back Huawei CSI on Kubernetes, OpenShift, and Tanzu"
linkTitle: "Rolling Back Huawei CSI on Kubernetes, OpenShift, and Tanzu"
description: 
weight: 1
---

## Prerequisites{#section12493103133711}

-   CSI has been updated using Helm 3.

## Procedure{#section1015846181614}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Go to the  **helm/esdk**  working directory. For the directory path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    cd helm/esdk
    ```

3.  <a name="li92161141175717"></a>Run the following command to query the historical versions of the CSI services deployed using Helm.

    ```
    helm history helm-huawei-csi -n huawei-csi 
    ```

    The following is an example of the command output.

    ```
    REVISION        UPDATED                         STATUS          CHART           APP VERSION     DESCRIPTION     
    1       	Mon Jan  8 04:15:40 2024	superseded	esdk-4.4.0	4.4.0      	Install complete
    2       	Mon Jan  8 04:16:12 2024	deployed  	esdk-4.8.0	4.8.0      	Upgrade complete
    ```

4.  Run the following command to roll back the CSI services to the specified version.

    In the preceding command,  _revision-number_  indicates a version number queried in  [3](#li92161141175717). For example, the version is  **1**.

    ```
    helm rollback helm-huawei-csi -n huawei-csi 1
    ```

    The following is an example of the command output. If  **Rollback was a success**  is displayed in the command output, the CSI services are successfully rolled back to the specified version.

    ```
    Rollback was a success! Happy Helming!
    ```

