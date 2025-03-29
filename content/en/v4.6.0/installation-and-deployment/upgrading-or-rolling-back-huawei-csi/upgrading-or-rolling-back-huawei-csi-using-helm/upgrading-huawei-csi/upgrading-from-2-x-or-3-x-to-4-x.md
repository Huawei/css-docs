---
title: "Upgrading from 2.x or 3.x to 4.x"
linkTitle: "Upgrading from 2.x or 3.x to 4.x"
description: 
weight: 1
---

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>In CSI 2._x_  or 3._x_, when block storage is used, the mapping with storage is set up in the huawei-csi-node service. Therefore, the huawei-csi-node service needs to communicate with the storage management network. Because the huawei-csi-node service is deployed as a DaemonSet, the huawei-csi-node service is deployed on each node in the cluster. As a result, in a large-scale cluster, each huawei-csi-node service sends requests to the storage and the number of storage connections may be fully occupied. Accordingly, huawei-csi-node cannot provide services properly.
>In CSI 4._x_, the deployment model is optimized. The setup of the mapping with storage is migrated to the huawei-csi-controller service and the huawei-csi-node service does not need to communicate with the storage management network. This reduces the networking complexity of Huawei CSI. In addition, the huawei-csi-controller service is deployed as a Deployment. The number of copies is set based on the customer's reliability requirements. Generally, the number of copies ranges from 1 to 3. Therefore, the number of connections between Huawei CSI and storage is greatly reduced, so that Huawei CSI can connect to a large-scale cluster.
>This change may cause a problem. That is, if a new mount process is generated after CSI is upgraded to 4._x_  but with workloads provisioned using 2._x_  or 3._x_  and the Container Orchestration \(CO\) system does not invoke the huawei-csi-controller service provided by Huawei CSI, the mounting will fail. For details, see  [A Pod Fails to Be Created and Message "publishInfo doesn't exist" Is Displayed in the Events Log](/docs/troubleshooting/pod-issues/a-pod-fails-to-be-created-and-message-publishinfo-doesn-t-exist-is-displayed-in-the-events-log).

## Backing Up Storage Backend Configurations{#section3200825558}

If you have evaluated the risks mentioned in the preceding notice and need to upgrade CSI from 2._x_  or 3._x_  to  4.6.0, perform the following steps to back up storage backend configurations:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to back up the backend information to the  **configmap.json**  file. For the OpenShift platform, replace  **kubectl**  with  **oc**.

    ```
    kubectl get cm huawei-csi-configmap -n huawei-csi -o json > configmap.json
    ```

## Upgrading Huawei CSI{#section1413511233612}

Perform the upgrade according to the procedure described in  [Upgrading Huawei CSI](/docs/installation-and-deployment/upgrading-or-rolling-back-huawei-csi/upgrading-or-rolling-back-huawei-csi-using-helm/upgrading-huawei-csi/upgrading-huawei-csi-on-kubernetes-openshift-and-tanzu#section6841317173013).

## Configuring the Storage Backend{#section496812169812}

Configure the storage backend by following the instructions in  [Managing Storage Backends](/docs/storage-backend-management/managing-storage-backends)  according to the backend information backed up in  [Backing Up Storage Backend Configurations](#section3200825558). After the storage backend is successfully configured, perform operations according to the risk handling methods described in the preceding notice to prevent problems during Pod failover.

