---
title: "Managing Storage Backends Using kubectl"
linkTitle: "Managing Storage Backends Using kubectl"
description: 
weight: 11
---

CSI storage backends are implemented based on Kubernetes custom resources \(CRDs\). In addition to using the oceanctl tool, you can also run  **kubectl**  commands to manage storage backend resources. Storage backends involve the following two types of CRD resources:

-   **StorageBackendClaim**  \(sbc for short\): namespace-level resource, which indicates the user's claim to a storage backend. You can create this resource to trigger the CSI controller to automatically connect the storage backend.
-   **StorageBackendContent**  \(sbct for short\): cluster-level resource, which is automatically created by the CSI controller after a StorageBackendClaim is successfully bound. It indicates the actual storage backend instance in the cluster. You should not directly create or modify this resource.

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   Before using kubectl to manage storage backends, ensure that the CSI plug-in has been installed and the CRD has been correctly registered with the cluster.
>-   **StorageBackendContent**  is automatically managed by the controller. Do not directly create or manually modify it. Otherwise, the storage backend may be abnormal.
>-   Do not delete a storage backend when a volume management operation is being performed on it.






