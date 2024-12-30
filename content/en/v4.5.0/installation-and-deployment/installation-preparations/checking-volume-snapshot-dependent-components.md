---
title: "Checking Volume Snapshot-Dependent Components"
linkTitle: "Checking Volume Snapshot-Dependent Components"
description: 
weight: 4
---

This section describes how to check the volume snapshot-dependent components in the cluster.

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>Kubernetes earlier than v1.17.0 does not support the snapshot function. If the snapshot CRD is deployed, the cluster may be faulty. Therefore, if Huawei CSI is deployed on Kubernetes earlier than v1.17.0, perform the check according to  [Kubernetes Earlier Than v1.17.0](#section6894165917369).

## Kubernetes Earlier Than v1.17.0{#section6894165917369}

If the Kubernetes version is earlier than v1.17.0, the cluster may be faulty during snapshot deployment. Perform the following steps to delete the snapshot CRD installation file.

1.  Run the following command to check the Kubernetes version. In the following example, the Kubernetes version is v1.16.0.

    ```
    kubectl get node
    ```

    The following is an example of the command output.

    ```
    NAME          STATUS       ROLES     AGE    VERSION
    test-master   Ready        master    311d   v1.16.0
    test-node     Ready        <none>    311d   v1.16.0
    ```

2.  Go to the  **/helm/esdk/crds/snapshot-crds**  directory and run the following command to delete the snapshot CRD installation file. For details about the component package path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    rm -rf ./huawei-csi-snapshot-crd-v1.yaml
    ```

