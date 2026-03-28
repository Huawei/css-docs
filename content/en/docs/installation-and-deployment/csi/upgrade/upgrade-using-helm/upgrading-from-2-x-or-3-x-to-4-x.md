---
title: "Upgrading from 2.x or 3.x to 4.x"
linkTitle: "Upgrading from 2.x or 3.x to 4.x"
description: 
weight: 1
---

## Backing Up Storage Backend Configurations{#section3200825558}

If you have evaluated the risks mentioned in the preceding notice and need to upgrade CSI from 2._x_  or 3._x_  to  4.11.0, perform the following steps to back up storage backend configurations:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to back up the backend information to the  **configmap.json**  file. For the OpenShift platform, replace  **kubectl**  with  **oc**.

    ```
    kubectl get cm huawei-csi-configmap -n huawei-csi -o json > configmap.json
    ```

## Upgrading Huawei CSI{#section1413511233612}

Perform the upgrade according to the procedure described in  [Upgrading Huawei CSI](/docs/installation-and-deployment/csi/upgrade/upgrade-using-helm/upgrading-huawei-csi-on-kubernetes-openshift-and-tanzu#section6841317173013).

## Configuring the Storage Backend{#section496812169812}

1.  Configure the storage backend based on the backend information backed up in  [Backing Up Storage Backend Configurations](#section3200825558)  according to  [Storage Backend Management](/docs/basic-services/storage-backend-management). The command for configuring the storage backend based on the backup backend information is as follows:

    ```
    oceanctl create backend -f configmap.json -i json -n huawei-csi
    ```

