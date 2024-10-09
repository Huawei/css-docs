---
title: "Examples of Storage Backend Configuration Files in Typical Scenarios"
linkTitle: "Examples of Storage Backend Configuration Files in Typical Scenarios"
description: 
weight: 1
---

For details about the backend configuration in typical scenarios, see the following examples. For details about the parameter configuration, see  [Storage Backend Parameters](/docs/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters).

-   [Configuring a Storage Backend of the iSCSI Type](#section9560112218344)
-   [Configuring a Storage Backend of the FC Type](#section4385132433717)
-   [Configuring a Storage Backend of the NVMe over RoCE Type](#section887724419372)
-   [Configuring a Storage Backend of the NVMe over FC Type](#section11434793492)
-   [Configuring a Storage Backend of the NFS Type](#section13980125055717)
-   [Configuring a Storage Backend of the SCSI Type](#section51803398537)
-   [Configuring a Storage Backend of the DPC Type](#section1094123525411)
-   [Configuring Storage Backends of the Dtree Type](#section6768010203620)
-   [Configuring Storage Backends of the HyperMetro Type](#section175945335494)

## Configuring a Storage Backend of the iSCSI Type{#section9560112218344}

>![](/css-docs/public_sys-resources/en/icon-note.gif)
>If you want to use the iSCSI protocol, ensure that the iSCSI client has been installed on the host before installing Huawei CSI. You can check whether the client has been installed on the host by referring to  [Checking the Status of Host-Dependent Software](/docs/installation-and-deployment/installation-preparations/checking-the-status-of-host-dependent-software). If the iSCSI client is not installed, restart the huawei-csi-node service after installing the iSCSI client. During the restart, do not use Huawei CSI to create new resources or mount or unmount an existing PVC. The following command is used as an example:
>```
>kubectl delete pods -n huawei-csi -l app=huawei-csi-node
>```

The following is an example of the backend configuration file of the iSCSI type for enterprise storage:

```yaml
storage: "oceanstor-san"
name: "dorado-iscsi-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "iscsi"
  portals:
    - "192.168.128.120"                
    - "192.168.128.121"
maxClientThreads: "30"
```

The following is an example of the backend configuration file of the iSCSI type for distributed storage:

```yaml
storage: "fusionstorage-san"
name: "pacific-iscsi-125"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.125:8088"
  - "https://192.168.129.126:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "iscsi"
  portals:
    - "192.168.128.122"
    - "192.168.128.123"
maxClientThreads: "30"
```

## Configuring a Storage Backend of the FC Type{#section4385132433717}

>![](/css-docs/public_sys-resources/en/icon-note.gif)
>If you want to use the FC protocol, ensure that the FC network between the host and the storage device is connected before installing Huawei CSI. If the FC network is not connected, connect the FC network and then restart the huawei-csi-node service. During the restart, do not use Huawei CSI to create new resources or mount or unmount an existing PVC. The following command is used as an example:
>```
>kubectl delete pods -n huawei-csi -l app=huawei-csi-node
>```

The following is an example of the backend configuration file of the FC type for enterprise storage:

```yaml
storage: "oceanstor-san"
name: "fc-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "fc"
maxClientThreads: "30"
```

## Configuring a Storage Backend of the NVMe over RoCE Type{#section887724419372}

>![](/css-docs/public_sys-resources/en/icon-note.gif)
>If you want to use the NVMe over RoCE protocol, ensure that the NVMe over RoCE network between the host and the storage device is connected before installing Huawei CSI. If the NVMe over RoCE network is not connected, connect the NVMe over RoCE network and then restart the huawei-csi-node service. During the restart, do not use Huawei CSI to create new resources or mount or unmount an existing PVC. The following command is used as an example:
>```
>kubectl delete pods -n huawei-csi -l app=huawei-csi-node
>```

The following is an example of the backend configuration file of the NVMe over RoCE type for enterprise storage:

```yaml
storage: "oceanstor-san"
name: "roce-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "roce"
  portals:
    - "192.168.128.120"        
    - "192.168.128.121"
maxClientThreads: "30"
```

## Configuring a Storage Backend of the NVMe over FC Type{#section11434793492}

The following is an example of the backend configuration file of the NVMe over FC type for enterprise storage:

```yaml
storage: "oceanstor-san"
name: "fc-nvme-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "fc-nvme"
maxClientThreads: "30"
```

## Configuring a Storage Backend of the NFS Type{#section13980125055717}

The following is an example of the backend configuration file of the NFS type for enterprise storage:

```yaml
storage: "oceanstor-nas"
name: "nfs-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "nfs"
  portals:        
    - "192.168.128.155"
maxClientThreads: "30"
```

The following is an example of the backend configuration file of the NFS type for distributed storage:

```yaml
storage: "fusionstorage-nas"
name: "nfs-126"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.125:8088"
  - "https://192.168.129.126:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "nfs"
  portals:
    - "192.168.128.123"
maxClientThreads: "30"
```

## Configuring a Storage Backend of the SCSI Type{#section51803398537}

The following is an example of the backend configuration file of the SCSI type for distributed storage:

```yaml
storage: "fusionstorage-san"
name: "scsi-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "scsi"
  portals:
    - {"hostname01": "192.168.125.21","hostname02": "192.168.125.22"}
maxClientThreads: "30"
```

## Configuring a Storage Backend of the DPC Type{#section1094123525411}

The following is an example of the backend configuration file of the DPC type for distributed storage:

```yaml
storage: "fusionstorage-nas"
name: "dpc-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
parameters:      
  protocol: "dpc"
maxClientThreads: "30"
```

## Configuring Storage Backends of the Dtree Type{#section6768010203620}

The following is an example of the backend configuration file of the Dtree type for enterprise storage:

```yaml
storage: "oceanstor-dtree"
name: "nfs-dtree"
namespace: "huawei-csi"
urls:
- "https://192.168.129.155:8088"
parameters:
  protocol: "nfs"
  parentname: "parent-filesystem"  
  portals:
    - "192.168.128.155"
maxClientThreads: "30"
```

## Configuring Storage Backends of the HyperMetro Type{#section175945335494}

>![](/css-docs/public_sys-resources/en/icon-note.gif)
>-   Before configuring NAS HyperMetro, you need to configure the HyperMetro relationship between two storage devices, including the remote device, HyperMetro domain, and the like. The HyperMetro domain of the file system can only work in HyperMetro active-active \(AA\) mode. For details about the configuration operation, see the product documentation of the corresponding storage model.
>-   The accounts for connecting to NAS HyperMetro backends must be the administrator accounts of the storage vStores.
>-   Except NAS HyperMetro backends, the management URLs of other backends cannot be the URL of a logical management port of a vStore that has established the HyperMetro relationship.
>-   When a HyperMetro storage backend is used, do not provision common file systems. Otherwise, services may be interrupted in logical port failover scenarios.

CSI allows you to connect to OceanStor or OceanStor Dorado and provision HyperMetro volumes of the NFS type on the storage side. You need to configure storage backends that work in HyperMetro mode. The procedure is as follows: Create two configuration files and create backends one by one.

This example shows how to configure backends of the HyperMetro type for Huawei OceanStor or OceanStor Dorado. First, create local storage backend configuration file  **nfs-hypermetro-155.yaml**.

```yaml
storage: "oceanstor-nas"
name: "nfs-hypermetro-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
metrovStorePairID: "f09838237b93c000"
metroBackend: "nfs-hypermetro-157"
parameters:
  protocol: "nfs"
  portals:
    - "192.168.129.155"
maxClientThreads: "30"
```

After the local backend is created, create remote storage backend configuration file  **nfs-hypermetro-157.yaml**.

```yaml
storage: "oceanstor-nas"
name: "nfs-hypermetro-157"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.157:8088"
  - "https://192.168.129.158:8088"
pools:
  - "StoragePool001"
metrovStorePairID: "f09838237b93c000"
metroBackend: "nfs-hypermetro-155"
parameters:
  protocol: "nfs"
  portals:
    - "192.168.129.157"
maxClientThreads: "30"
```

