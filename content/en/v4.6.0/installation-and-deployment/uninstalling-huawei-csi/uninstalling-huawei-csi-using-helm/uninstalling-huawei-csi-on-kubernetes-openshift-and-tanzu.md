---
title: "Uninstalling Huawei CSI on Kubernetes, OpenShift, and Tanzu"
linkTitle: "Uninstalling Huawei CSI on Kubernetes, OpenShift, and Tanzu"
description: 
weight: 1
---

This section describes how to uninstall Huawei CSI on the Kubernetes, OpenShift, and Tanzu platforms.

## Procedure{#section9152125194710}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to uninstall Huawei CSI. In the command,  _helm-huawei-csi_  indicates the custom Helm chart name and  _huawei-csi_  indicates the namespace where the Helm chart resides. This command will uninstall the huawei-csi-controller, huawei-csi-node, and RBAC resources of Huawei CSI.

    ```
    helm uninstall helm-huawei-csi -n huawei-csi
    ```

    After the uninstallation command is executed, you need to check whether the uninstallation is successful. In the preceding command,  _huawei-csi_  indicates the namespace where the chart is located.

    ```
    helm list -n huawei-csi
    ```

    The following is an example of the command output. If the command output is empty, the service is successfully uninstalled.

    ```
    NAME NAMESPACE REVISION UPDATED STATUS CHART APP VERSION
    ```

3.  Uninstall the huawei-csi-host-info object. For details, see  [Uninstalling the huawei-csi-host-info Object](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section870813403017).
4.  Uninstall the webhook resource. For details, see  [Uninstalling a Webhook Resource](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section871155813014).
5.  \(Optional\) Uninstall the snapshot-dependent component service. For details, see  [Uninstalling the Snapshot-Dependent Component Service](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section48371491319).
6.  \(Optional\) Uninstall the Lease resource. For details, see  [Uninstalling a Lease Resource](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section263805014317).
7.  \(Optional\) Run the following command to delete the namespace where Huawei CSI is located. The default namespace  **huawei-csi**  is used as an example.

    ```
    kubectl delete ns huawei-csi
    ```

