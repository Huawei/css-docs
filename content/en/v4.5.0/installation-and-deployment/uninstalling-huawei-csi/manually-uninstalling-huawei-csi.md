---
title: "Manually Uninstalling Huawei CSI"
linkTitle: "Manually Uninstalling Huawei CSI"
description: 
weight: 2
---

This section describes how to manually uninstall Huawei CSI.

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>If you do not uninstall Huawei CSI for the purpose of an upgrade, ensure that all resources \(such as PV, PVC, snapshot, and storage backend resources\) provisioned by Huawei CSI have been cleared on your container platform before uninstalling Huawei CSI. Otherwise, once you uninstall Huawei CSI, these resources cannot be automatically scheduled, managed, or cleared.

## Uninstalling the huawei-csi-node Service{#section1012817231386}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to uninstall the huawei-csi-node service. Replace  _huawei-csi_  with the namespace where Huawei CSI is located.

    ```
    kubectl delete daemonset huawei-csi-node -n huawei-csi
    ```

3.  Run the following command to check whether the service is successfully uninstalled. If  **NotFound**  is displayed, the service is successfully uninstalled.

    ```
    kubectl get daemonset huawei-csi-node -n huawei-csi
    ```

## Uninstalling the huawei-csi-controller Service{#section34281930180}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to uninstall the huawei-csi-controller service. Replace  _huawei-csi_  with the namespace where Huawei CSI is located.

    ```
    kubectl delete deployment huawei-csi-controller -n huawei-csi
    ```

3.  Run the following command to check whether the service is successfully uninstalled. If  **NotFound**  is displayed, the service is successfully uninstalled.

    ```
    kubectl get deployment huawei-csi-controller -n huawei-csi
    ```

## Uninstalling the csidriver Object{#section4229471288}

If  [the CSIDriver feature is not used during installation](/docs/installation-and-deployment/installing-huawei-csi/manually-installing-huawei-csi#li395973220487), you can skip the following steps.

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to uninstall the csidriver object.

    ```
    kubectl delete csidriver csi.huawei.com
    ```

3.  Run the following command to check whether the service is successfully uninstalled. If  **NotFound**  is displayed, the service is successfully uninstalled.

    ```
    kubectl get csidriver csi.huawei.com
    ```

## Deleting the RBAC Permission{#section111616512911}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Delete the RBAC permission.

    ```
    kubectl -n huawei-csi -l provisioner=csi.huawei.com delete ServiceAccount,Service,role,rolebinding,ClusterRole,ClusterRoleBinding
    ```

## Uninstalling Other Resources{#section1370361019919}

1.  Uninstall the huawei-csi-host-info object. For details, see  [Uninstalling the huawei-csi-host-info Object](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section870813403017).
2.  Uninstall the webhook resource. For details, see  [Uninstalling a Webhook Resource](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section871155813014).
3.  \(Optional\) Uninstall the snapshot-dependent component service. For details, see  [Uninstalling the Snapshot-Dependent Component Service](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section48371491319).
4.  \(Optional\) Uninstall the Lease resource. For details, see  [Uninstalling a Lease Resource](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section263805014317).

