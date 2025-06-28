---
title: "Configuring IPv6 During the Initial Installation of Huawei CSI"
linkTitle: "Configuring IPv6 During the Initial Installation of Huawei CSI"
description: 
weight: 1
---

This section describes how to specify IPv6 during the initial installation of Huawei CSI.

## Prerequisites{#section11013445374}

-   IPv6 can be configured only when the storage backend type is  **oceanstor-nas**,  **oceanstor-san**, or  **oceanstor-dtree**.
-   The host environment and Kubernetes cluster environment support IPv6. For details, see  [IPv4/IPv6 dual-stack of Kubernetes](https://kubernetes.io/docs/concepts/services-networking/dual-stack/).

## Procedure{#section147071119142913}

1.  Install the CSI-dependent components by following the instructions in  [1](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#en-us_topic_0000001324610777_li9582123242310)  to  [7](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#li1759104413237)  in  [Installation Procedure](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#section9426125115349).
2.  Run the  **vi values.yaml**  command to open the configuration file and modify the  **service.ipFamilyPolicy**  and  **service.ipFamilies**  configuration items. For details about the parameters, see  [Table 5](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table258712427285).

    The following is an example:

    ```yaml
    service:
      ipFamilyPolicy: SingleStack
      ipFamilies:
        - IPv6
    ```

3.  Install and deploy Huawei CSI by following the instructions in  [8](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#en-us_topic_0000001324610777_li888917271326)  to  [9](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#en-us_topic_0000001324610777_li108160349154)  in  [Installation Procedure](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-kubernetes-openshift-and-tanzu#section9426125115349).
4.  Run the following command to check the status of the service in the  **huawei-csi**  namespace.

    ```
    kubectl get service -n huawei-csi
    ```

    The following is an example of the command output.

    ```
    NAME                    TYPE        CLUSTER-IP         EXTERNAL-IP   PORT(S)    AGE
    huawei-csi-controller   ClusterIP   fd00:10:96::8136   <none>        4433/TCP   19m
    ```

5.  Run the following command to check the value of  **ipFamilies**  for the huawei-csi-controller service.

    ```
    kubectl get svc -n huawei-csi huawei-csi-controller -o=jsonpath='{.spec.ipFamilies}'
    ```

    The following is an example of the command output.

    ```
    ["IPv6"]
    ```

6.  Run the following command to check the value of  **ipFamilyPolicy**  for the huawei-csi-controller service.

    ```
    kubectl get svc -n huawei-csi huawei-csi-controller -o=jsonpath='{.spec.ipFamilyPolicy}'
    ```

    The following is an example of the command output.

    ```
    SingleStack
    ```

