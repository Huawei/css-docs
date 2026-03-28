---
title: "Creating a PV Using a VolumeSnapshot"
linkTitle: "Creating a PV Using a VolumeSnapshot"
description: 
weight: 2
---

## Prerequisites{#en-us_topic_0254212585_section0772716133710}

-   [Compatibility and Features](/docs/compatibility-and-features)  lists storage that support PVC creation using a VolumeSnapshot. You need to search by the storage type and service type.
-   [Kubernetes Feature Matrix](/docs/appendix/kubernetes-feature-matrix)  lists the Kubernetes versions that support PVC creation using a VolumeSnapshot.
-   A VolumeSnapshot exists, and the backend where the VolumeSnapshot resides supports cloning.

When creating a PVC, you need to specify a VolumeSnapshot as the data source. The following is an example of creating a PVC using a VolumeSnapshot. In this example,  **mysnapshot**  is used as the data source and a PVC named  **myrestore**  is created.

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: myrestore
spec:
  storageClassName: mysc
  dataSource:
    name: mysnapshot
    kind: VolumeSnapshot
    apiGroup: snapshot.storage.k8s.io
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 100Gi
```

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   The specified  **storageClassName**  must be the same as the StorageClass of the snapshot source volume in  **dataSource**.
>-   The capacity of the clone volume must be greater than or equal to that of the snapshot. Equal capacity is recommended.

## Procedure{#section145015152569}

1.  Run the following command to create a PVC based on the configuration file for creating a volume using a snapshot.

    ```
    kubectl create -f myrestore.yaml
    ```

