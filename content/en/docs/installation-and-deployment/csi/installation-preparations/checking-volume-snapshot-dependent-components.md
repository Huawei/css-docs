---
title: "Checking Volume Snapshot-Dependent Components"
linkTitle: "Checking Volume Snapshot-Dependent Components"
description: 
weight: 4
---

This section describes how to check the volume snapshot-dependent components in the cluster.

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>If Huawei CSI is deployed in a version earlier than Kubernetes v1.20, perform the following steps:

1.  Run the following command to check the Kubernetes version. The following uses Kubernetes v1.16.0 as an example.

    ```
    kubectl get node
    ```

    The following is an example of the command output.

    ```
    NAME          STATUS       ROLES     AGE    VERSION
    test-master   Ready        master    311d   v1.16.0
    test-node     Ready        <none>    311d   v1.16.0
    ```

2.  Copy the  **helm**  directory in the Kubernetes CSI component package to any directory on the master node. For details about the Helm tool path, see  [Table 1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).
3.  Go to the  **helm/esdk/crds/snapshot-crds**  directory and run the following command to delete the snapshot CRD installation file.

    ```
    rm -rf ./huawei-csi-snapshot-crd-v1.yaml
    ```

