---
title: "StorageClass Configuration Examples in Typical Manage Volume Provisioning Scenarios"
linkTitle: "StorageClass Configuration Examples in Typical Manage Volume Provisioning Scenarios"
description: 
weight: 1
---

For details about how to configure a StorageClass in typical Manage Volume Provisioning scenarios, see the following examples:

-   [Setting the Backend and Storage Pool in a StorageClass](#section114859014540)
-   [Setting the NFS Access Mode in a StorageClass](#section128347019144)
-   [Setting the Local File System Access Mode in a StorageClass](#section1155962772514)
-   [Setting the DPC Access Mode in a StorageClass](#section022191784519)
-   [Setting the Permission on a Mount Directory in a StorageClass](#section1356811882616)

## Setting the Backend and Storage Pool in a StorageClass{#section114859014540}

If multiple Huawei backends are configured in a Kubernetes cluster or a Huawei backend provides multiple storage pools, you are advised to configure the specified backend and storage pool information in the StorageClass. This prevents Huawei CSI from randomly selecting backends and storage pools and ensures that the storage device where the volume resides complies with the plan.

For details about how to set the backend and storage pool for SAN storage, see the following configuration example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
allowVolumeExpansion: true
parameters:
  backend: "iscsi-san-181"
  pool: "pool001"
  volumeType: lun
  allocType: thin
```

For details about how to set the backend and storage pool for NAS storage, see the following configuration example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
allowVolumeExpansion: true
parameters:
  backend: "iscsi-nas-181"
  pool: "pool001"
  volumeType: fs
  allocType: thin
  authClient: "*"
```

## Setting the NFS Access Mode in a StorageClass{#section128347019144}

When a container uses an NFS file system as a storage resource, refer to the following configuration example. In this example, NFS version 4.1 is specified for mounting.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-nas-181
  pool: pool001
  volumeType: fs
  allocType: thin
mountOptions:
  - nfsvers=4.1 # Specify the version 4.1 for NFS mounting.
```

## Setting the Local File System Access Mode in a StorageClass{#section1155962772514}

If a container uses a LUN of enterprise storage or distributed storage as a storage resource and a file system needs to be formatted as a local file system, refer to the following example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: iscsi-lun-181
  pool: pool001
  volumeType: lun
  allocType: thin
  fsType: xfs
```

## Setting the DPC Access Mode in a StorageClass{#section022191784519}

If a container uses OceanStor Pacific series storage and the storage supports DPC-based access, you can configure mounting parameters for DPC-based access in the StorageClass. In this example,  **acl**  is used as the authentication parameter for mounting, and  **cnflush**  is used to set the asynchronous disk flushing mode.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dpc-101
  pool: pool001
  volumeType: fs
  allocType: thin
  authClient: "*"
mountOptions:
  - acl # Set the authentication parameter.
  - cnflush # Set the asynchronous disk flushing mode.
```

## Setting the Permission on a Mount Directory in a StorageClass{#section1356811882616}

To modify the permission on a mount directory in a container, you can configure the directory permission in a StorageClass. The following is a configuration example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
allowVolumeExpansion: true
parameters:
  volumeType: fs
  allocType: thin
  authClient: "*"
  fsPermission: "777" # Set the directory permission.
```

After the StorageClass configuration is complete, perform the following steps to create a StorageClass.

1.  Run the following command to create a StorageClass based on the .yaml file.

    ```
    kubectl create -f mysc.yaml
    ```

2.  Run the following command to view the information about the created StorageClass.

    ```
    kubectl get sc
    ```

    The following is an example of the command output.

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           false                  34s
    ```

    After creating a StorageClass, you can use the StorageClass to create a PV or PVC.

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>In the Manage Volume Provisioning mode, pay attention to the following when using a StorageClass:
>-   Modifications to a StorageClass do not take effect on existing PVs. You need to delete these PVs and create them again using the modified StorageClass to apply the modified parameters.

