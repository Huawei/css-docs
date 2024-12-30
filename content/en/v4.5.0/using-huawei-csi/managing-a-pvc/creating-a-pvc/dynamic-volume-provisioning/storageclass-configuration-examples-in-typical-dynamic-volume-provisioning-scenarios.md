---
title: "StorageClass Configuration Examples in Typical Dynamic Volume Provisioning Scenarios"
linkTitle: "StorageClass Configuration Examples in Typical Dynamic Volume Provisioning Scenarios"
description: 
weight: 1
---

A  [StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/)  provides administrators with methods to describe a storage "class". Different types may map to a different group of capability definitions. Kubernetes cluster users can dynamically provision volumes based on a StorageClass.

If SAN storage is used, refer to example file  **/examples/sc-lun.yaml**. If NAS storage is used, refer to example file  **/examples/sc-fs.yaml**.

For details about how to configure a StorageClass in typical scenarios, see the following examples:

-   [Setting the Backend and Storage Pool in a StorageClass](#section114859014540)
-   [Setting the NFS Access Mode in a StorageClass](#section128347019144)
-   [Setting a Dtree Type in a StorageClass](#section1642719478395)
-   [Setting the Local File System Access Mode in a StorageClass](#section1155962772514)
-   [Setting the DPC Access Mode in a StorageClass](#section022191784519)
-   [Setting an Application Type in a StorageClass](#section576688153313)
-   [Setting a Soft Quota in a StorageClass](#section73983205817)
-   [Setting HyperMetro in a StorageClass](#section12170214277)
-   [Setting the Permission on a Mount Directory in a StorageClass](#section156891316272)
-   [Setting QoS in a StorageClass](#section1016612587584)
-   [Configuring a StorageClass on the CCE or CCE Agile Platform](#section132301459161017)

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
  backend: "san-181" # Enter the storage backend name.
  pool: "pool001" # Enter the storage pool name
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
  backend: "san-181" # Enter the storage backend name.
  pool: "pool001" # Enter the storage pool name
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
  authClient: "192.168.0.10;192.168.0.0/24;myserver1.test"
mountOptions:
  - nfsvers=4.1 # Specify the version 4.1 for NFS mounting.
```

## Setting a Dtree Type in a StorageClass{#section1642719478395}

When a container uses a Dtree as a storage resource, refer to the following configuration example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dtree
  volumeType: dtree # Set the volume type to dtree.
  allocType: thin
  authClient: "*" 
mountOptions:
  - nfsvers=4.1
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

## Setting an Application Type in a StorageClass{#section576688153313}

When a container uses a LUN of OceanStor Dorado as the storage, if the default application type of the storage cannot meet the I/O model requirements of some services \(for example, the container provides the database OLAP service\), you can configure an application type in the StorageClass to improve storage performance. For details about the application types to be used, see the product documentation of the corresponding storage product.

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
  applicationType: Oracle_OLAP # Set the application type.
```

## Setting a Soft Quota in a StorageClass{#section73983205817}

If a container uses a file system of OceanStor Pacific series as the storage, you can configure a soft quota in the StorageClass. The following is a configuration example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-pacific-101
  pool: pool001
  volumeType: fs
  allocType: thin
  authClient: "*"
  storageQuota: '{"spaceQuota": "softQuota", "gracePeriod": 100}' # Configure the soft quota.
mountOptions:
  - nfsvers=3
```

## Setting QoS in a StorageClass{#section1016612587584}

When containers use enterprise storage or distributed storage as storage resources, you can set QoS for the storage resources used by containers to ensure that the storage read and write operations of these containers meet certain service levels.

Storage devices of different models or versions support different QoS settings. For details about how to find the configuration items of the corresponding storage devices, see  [Table 2](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/storageclass-parameters-for-dynamic-volume-provisioning#table74841513116). In this example, the backend is OceanStor Dorado. For other storage devices, refer to this example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: iscsi-qos-181
  pool: pool001
  volumeType: lun
  allocType: thin
  fsType: xfs
  qos: '{"IOTYPE": 2, "MINIOPS": 1000}' # Configure QoS.
```

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   vStore users of OceanStor V5 cannot configure QoS policies.
>-   The QoS configuration takes effect only on the newly created PVC. QoS cannot be added automatically for PVCs with the same StorageClass name that have been provisioned.

## Setting HyperMetro in a StorageClass{#section12170214277}

When a container uses an NFS HyperMetro file system as a storage resource, refer to the following configuration example. In this example, the used backend supports HyperMetro, and  **hyperMetro**  is set to  **true**.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-hypermetro-dorado-181
  pool: pool001
  volumeType: fs
  hyperMetro: "true" # Provision HyperMetro volumes.
  allocType: thin
  authClient: "*"
```

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   Before provisioning a NAS HyperMetro volume, you need to configure the HyperMetro relationship between two storage devices, including the remote device, HyperMetro domain, and the like. The HyperMetro domain of the file system can only work in HyperMetro active-active \(AA\) mode. For details about the configuration operation, see the product documentation of the corresponding storage model.
>-   If a storage device is faulty, the logical management port may fail over. In this case, you need to manually clear the corresponding storage resources after deleting the NAS HyperMetro volume.

## Setting the Permission on a Mount Directory in a StorageClass{#section156891316272}

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
  fsPermission: "777"
  rootSquash: "no_root_squash"  # Only NAS storage supports this parameter.
  allSquash: "no_all_squash"   # Only NAS storage supports this parameter.
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
>Pay attention to the following when using a StorageClass:
>-   Modifications to a StorageClass do not take effect on existing PVs. You need to delete these PVs and create them again using the modified StorageClass to apply the modified parameters.

## Configuring a StorageClass on the CCE or CCE Agile Platform{#section132301459161017}

Create a StorageClass of the NAS type on the CCE or CCE Agile platform. The following is a configuration example. The value of  **provisioner**  must be the same as that of  **driverName**  in the  **values.yaml**  file.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
  annotations:
    storageclass.kubernetes.io/storageType: file 
provisioner: csi.oceanstor.com  
allowVolumeExpansion: true
parameters:
  volumeType: fs
  allocType: thin
  authClient: "*"
```

Create a StorageClass of the Block type on the CCE or CCE Agile platform. The following is a configuration example. The value of  **provisioner**  must be the same as that of  **driverName**  in the  **values.yaml**  file.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
  annotations:
    storageclass.kubernetes.io/storageType: block 
provisioner: csi.oceanstor.com
allowVolumeExpansion: true
parameters:
  volumeType: lun
  allocType: thin
```

