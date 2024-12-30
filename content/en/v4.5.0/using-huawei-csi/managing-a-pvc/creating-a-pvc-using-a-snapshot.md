---
title: "Creating a PVC Using a Snapshot"
linkTitle: "Creating a PVC Using a Snapshot"
description: 
weight: 4
---

This section describes how to create a PVC using a snapshot.

When creating a PVC, you need to specify the data source. The following is a simple example of creating a PVC using a snapshot. In this example,  **mysnapshot**  is used as the data source and a PVC named  **myrestore**  is created.

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

## Prerequisites{#en-us_topic_0254212585_section0772716133710}

A snapshot already exists in the system, and the backend where the snapshot resides supports cloning. For details about the storage devices that support PVC creation using a snapshot, see  [Table 2](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage#table14995183994515)  and  [Table 2](/docs/compatibility-and-features/compatibility-with-huawei-distributed-storage#table175022559255). For details about the Kubernetes versions that support PVC creation using a snapshot, see  [Kubernetes Feature Matrix](/docs/compatibility-and-features/kubernetes-feature-matrix).

## Procedure{#en-us_topic_0254212585_section1882544631619}

1.  Run the following command to create a PVC based on the configuration file for creating a volume using a snapshot.

    ```
    kubectl create -f myrestore.yaml
    ```

