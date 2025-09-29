---
title: "Switching from IPv4 to IPv6 for Huawei CSI"
linkTitle: "Switching from IPv4 to IPv6 for Huawei CSI"
description: 
weight: 2
---

This section describes how to switch from IPv4 to IPv6 when updating Huawei CSI.

## Prerequisites{#section11013445374}

-   The host environment and Kubernetes cluster environment support IPv6. For details, see  [IPv4/IPv6 dual-stack of Kubernetes](https://kubernetes.io/docs/concepts/services-networking/dual-stack/).
-   Huawei CSI has been installed and services are running properly.

## Procedure{#section826141105010}

1.  <a name="li19355236151916"></a>Run the following command to obtain the original service configuration file.  **helm-huawei-csi**  indicates the Helm chart name specified during the installation of the earlier version, and  **huawei-csi**  indicates the Helm chart namespace specified during the installation of the earlier version.

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

2.  Run the  **vi update-values.yaml**  command to open the file obtained in  [1](#li19355236151916)  and modify the  **service.ipFamilyPolicy**  and  **service.ipFamilies**  configuration items. For details about the parameters, see  [Table 5](/docs/installation-and-deployment/csi/installation/installation-using-helm/parameters-in-the-values-yaml-file-of-helm#table258712427285).

    The following is an example:

    ```yaml
    service:
      ipFamilyPolicy: SingleStack
      ipFamilies:
        - IPv6
    ```

3.  Before switching to IPv6, run the following command to delete the service in the  **huawei-csi**  namespace.

    ```
    kubectl delete service -n huawei-csi --all
    ```

4.  Run the following command to upgrade Huawei CSI. In the following command,  **helm-huawei-csi**  indicates the specified Helm chart name,  **huawei-csi**  indicates the specified Helm chart namespace, and  **update-values.yaml**  indicates the file obtained in  [1](#li19355236151916).

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi -f ./values.yaml -f ./update-values.yaml
    ```

5.  Run the following command to query the  **ipFamilies**  parameter of the huawei-csi-controller service after the update.

    ```
    kubectl get svc -n huawei-csi huawei-csi-controller -o=jsonpath='{.spec.ipFamilies}'
    ```

    The expected output is as follows:

    ```
    ["IPv6"]
    ```

