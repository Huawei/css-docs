---
title: "Uninstalling CSI-Dependent Component Services"
linkTitle: "Uninstalling CSI-Dependent Component Services"
description: 
weight: 3
---

This section describes how to uninstall the CSI-dependent component services.

## Uninstalling the huawei-csi-host-info Object{#section870813403017}

Secret object  **huawei-csi-host-info**  stores the initiator information about each node in the cluster, for example, iSCSI initiators. When you run the  **helm uninstall**  command, the resource will not be uninstalled. To uninstall the resource, perform the following steps:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to delete the Secret object.  _huawei-csi-host-info_  is the name of the Secret object, and  _huawei-csi_  is the namespace where the Secret object is located.

    ```
    kubectl delete secret huawei-csi-host-info -n huawei-csi
    ```

3.  Run the following command to check whether the Secret object is successfully uninstalled.

    ```
    kubectl get secret huawei-csi-host-info -n huawei-csi 
    ```

    The following is an example of the command output. If  **NotFound**  is displayed in the command output, the  **huawei-csi-host-info**  object is successfully uninstalled.

    ```yaml
    Error from server (NotFound): secrets "huawei-csi-host-info" not found
    ```

## Uninstalling a Webhook Resource{#section871155813014}

The webhook resource named  **storage-backend-controller.xuanwu.huawei.io**  is used to verify the backend key information and connectivity with the storage. When you run the  **helm uninstall**  command, the resource will not be uninstalled. To uninstall the resource, perform the following steps:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to query the webhook-dependent component service.

    ```
    kubectl get validatingwebhookconfigurations.admissionregistration.k8s.io storage-backend-controller.xuanwu.huawei.io
    ```

    The following is an example of the command output.

    ```
    NAME                                          WEBHOOKS   AGE
    storage-backend-controller.xuanwu.huawei.io   1          12d
    ```

3.  Run the following command to uninstall the webhook-dependent component service.

    ```
    kubectl delete validatingwebhookconfigurations.admissionregistration.k8s.io storage-backend-controller.xuanwu.huawei.io
    ```

4.  Run the following command to check whether the service is successfully uninstalled. If the command output is empty, the uninstallation is successful.

    ```
    kubectl get validatingwebhookconfigurations.admissionregistration.k8s.io storage-backend-controller.xuanwu.huawei.io
    ```

## Uninstalling the Snapshot-Dependent Component Service{#section48371491319}

>![](/css-docs/public_sys-resources/en/icon-notice.gif) 
>-   Do not uninstall the snapshot-dependent component service when snapshots exist. Otherwise, Kubernetes will automatically delete all user snapshots and they cannot be restored. Exercise caution when performing this operation. For details, see  [Delete a CustomResourceDefinition](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/#delete-a-customresourcedefinition).
>-   Do not uninstall the snapshot-dependent component service during the CSI upgrade.

**Scenario Description**

-   Currently, Huawei CSI uses the snapshot feature.
-   Currently, only Huawei CSI is available in the Kubernetes cluster, and Huawei CSI is no longer used.
-   Before the uninstallation, ensure that no VolumeSnapshot resource managed by Huawei CSI exists in the Kubernetes cluster.

**Procedure**

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to uninstall the snapshot-dependent component service.

    ```
    kubectl delete crd volumesnapshotclasses.snapshot.storage.k8s.io volumesnapshotcontents.snapshot.storage.k8s.io volumesnapshots.snapshot.storage.k8s.io
    ```

3.  Run the following command to check whether the service is successfully uninstalled. If the command output is empty, the uninstallation is successful.

    ```
    kubectl get crd | grep snapshot.storage.k8s.io
    ```

## Uninstalling a Lease Resource{#section263805014317}

If the value of the  **controller.controllerCount**  configuration item in the  **values.yaml**  file is greater than 1, huawei-csi-controller will be deployed in multi-copy mode. The multiple copies of huawei-csi-controller are implemented using the LeaderElection mechanism of Kubernetes. This mechanism creates a Lease object to store the current Holder information. When you run the  **helm uninstall**  command, the resource will not be uninstalled. To uninstall the resource, perform the following steps. If the value of  **controller.controllerCount**  is  **1**, you can skip the following steps. For details about the configuration item, see  [Table 2](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table813124411459).

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to query the Lease information.

    ```
    kubectl get lease -n huawei-csi
    ```

    The following is an example of the command output.

    ```
    NAME                                         HOLDER    AGE
    csi-huawei-com                               node-1    24d
    external-attacher-leader-csi-huawei-com      node-1    24d
    external-resizer-csi-huawei-com              node-1    24d
    external-snapshotter-leader-csi-huawei-com   node-1    24d
    snapshot-controller-leader                   node-1    24d
    storage-backend-controller                   node-1    24d
    huawei-csi-extender                          node-1    24d
    ```

3.  Run the following command to uninstall the Lease resource.

    ```
    kubectl delete lease -n huawei-csi csi-huawei-com external-attacher-leader-csi-huawei-com external-resizer-csi-huawei-com external-snapshotter-leader-csi-
    ```

4.  Run the following command to check whether the uninstallation is successful.

    ```
    kubectl get lease -n huawei-csi
    ```

    The following is an example of the command output. If the command output is empty, the uninstallation is successful.

    ```
    No resources found in huawei-csi namespace.
    ```

