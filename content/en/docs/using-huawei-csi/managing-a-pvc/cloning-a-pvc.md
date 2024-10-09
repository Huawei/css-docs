---
title: "Cloning a PVC"
linkTitle: "Cloning a PVC"
description: 
weight: 3
---

This section describes how to clone a PVC.

When cloning a PVC, you need to specify the data source. The following is a simple example of cloning a PVC. In this example,  **mypvc**  is used as the data source and a PVC named  **myclone**  is created.

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

>![](/public_sys-resources/en/icon-notice.gif) 
>-   The specified  **storageClassName**  must be the same as the StorageClass of the source volume in  **dataSource**.
>-   The capacity of the clone volume must be greater than or equal to that of the source volume. Equal capacity is recommended.

## Prerequisites{#section349216304616}

The source PVC already exists in the system, and the backend where the source PVC resides supports cloning. For details about the storage devices that support cloning, see  [Table 2](/docs/compatibility-and-features/compatibility-with-huawei-enterprise-storage#table14995183994515)  and  [Table 2](/docs/compatibility-and-features/compatibility-with-huawei-distributed-storage#table175022559255). For details about the Kubernetes versions that support cloning, see  [Kubernetes Feature Matrix](/docs/compatibility-and-features/kubernetes-feature-matrix).

## Procedure{#en-us_topic_0254212544_section319012981414}

1.  Run the following command to create a PVC based on the configuration file of the clone volume.

    ```
    kubectl create -f myclone.yaml
    ```

