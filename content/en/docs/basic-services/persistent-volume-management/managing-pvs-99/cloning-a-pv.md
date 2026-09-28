---
title: "Cloning a PV"
linkTitle: "Cloning a PV"
description: 
weight: 2
---

This section describes how to clone a PVC.

When cloning a PVC, you need to specify the data source. The following is an example of cloning a PVC. In this example,  **mypvc**  is used as the data source and a PVC named  **myclone**  is created.

```yaml
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: myclone
spec:
  storageClassName: mysc
  dataSource:
    name: mypvc
    kind: PersistentVolumeClaim
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 2Gi
```

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   The specified  **storageClassName**  must be the same as the StorageClass of the source volume in  **dataSource**.
>-   The capacity of the clone volume must be greater than or equal to that of the source volume. Equal capacity is recommended.

## Prerequisites{#section349216304616}

The source PVC already exists in the system, and the backend where the source PVC resides supports cloning.  [Compatibility and Features](/docs/compatibility-and-features)  lists the storage that supports cloning, and  [Kubernetes Feature Matrix](/docs/appendix/kubernetes-feature-matrix)  lists the Kubernetes versions that support cloning.

## Procedure{#section153154508193}

1.  Run the following command to create a PVC based on the configuration file of the clone volume.

    ```
    kubectl create -f myclone.yaml
    ```

