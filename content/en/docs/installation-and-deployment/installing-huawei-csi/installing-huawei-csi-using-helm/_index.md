---
title: "Installing Huawei CSI Using Helm"
linkTitle: "Installing Huawei CSI Using Helm"
description: 
weight: 1
---

## Helm Installation Description{#section16991437124819}

This section describes how to install Huawei CSI using Helm 3.

>![](/css-docs/public_sys-resources/en/icon-notice.gif) 
>-   Huawei CSI can be installed as the root user or a non-root user. When installing Huawei CSI as a non-root user, ensure that the current user can access the API Server of the Kubernetes cluster. For details about how to configure access to the Kubernetes cluster as a non-root user, see  [Configuring Access to the Kubernetes Cluster as a Non-root User](/docs/common-operations/configuring-access-to-the-kubernetes-cluster-as-a-non-root-user).
>-   Huawei CSI must be run as the root user.

Helm is a software package management tool in the Kubernetes ecosystem. Similar to Ubuntu APT, CentOS YUM, or Python pip, Helm manages Kubernetes application resources.

You can use Helm to package, distribute, install, upgrade, and roll back Kubernetes applications in a unified manner.

-   For details about how to obtain and install Helm, see  [https://helm.sh/docs/intro/install/](https://helm.sh/docs/intro/install/).
-   For details about the mapping between Helm and Kubernetes versions, see  [https://helm.sh/docs/topics/version\_skew/](https://helm.sh/docs/topics/version_skew/).

When installing huawei-csi-controller, Helm deploys the following components in the workloads of the Deployment type in the specified namespace:

-   huawei-csi-driver: Huawei CSI driver.
-   storage-backend-controller: Huawei backend management controller, used to manage storageBackendClaim resources.
-   storage-backend-sidecar: used to manage storageBackendContent resources.
-   Kubernetes External Provisioner: used to provide or delete volumes.
-   Kubernetes External Attacher: used to attach or detach volumes.
-   Kubernetes External Resizer: used to expand the capacity of volumes.
-   Kubernetes External liveness-probe: used to determine the health status of a Pod.
-   \(Optional\) huawei-csi-extender: Huawei CSI extender.
-   \(Optional\) Kubernetes External Snapshotter: used to provide snapshot support \(installed as CRD\).
-   \(Optional\) Kubernetes External Snapshot Controller: used to control volume snapshots.

When installing huawei-csi-node, Helm deploys the following components in the workloads of the DaemonSet type in the specified namespace:

-   huawei-csi-driver: Huawei CSI driver.
-   Kubernetes Node Registrar: used to process driver registration.
-   liveness-probe: used to determine the health status of a Pod.




