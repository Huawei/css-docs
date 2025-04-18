---
title: "典型场景存储后端配置文件示例"
linkTitle: "典型场景存储后端配置文件示例"
description: 
weight: 1
---

典型场景的backend配置请参考下列示例，详细的参数配置请参考[存储后端配置项说明](/docs/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters)。

-   [配置iSCSI协议类型的存储后端](#section9560112218344)
-   [配置FC协议类型的存储后端](#section4385132433717)
-   [配置NVMe over RoCE协议类型的存储后端](#section887724419372)
-   [配置NVMe over FC协议类型的存储后端](#section11434793492)
-   [配置NFS协议类型的存储后端](#section13980125055717)
-   [配置NFS+协议类型的存储后端](#section1890151345820)
-   [配置SCSI协议类型的存储后端](#section51803398537)
-   [配置DPC协议类型的存储后端](#section1094123525411)
-   [配置Dtree类型的存储后端](#section6768010203620)
-   [配置双活类型的存储后端](#section175945335494)

## 配置iSCSI协议类型的存储后端{#section9560112218344}

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>如果要使用iSCSI协议类型，请确保在安装华为CSI前，主机上已安装iSCSI客户端，可通过[检查主机依赖软件状态](/docs/installation-and-deployment/installation-preparations/checking-the-status-of-host-dependent-software)章节检查。如未安装iSCSI客户端，请在安装iSCSI客户端之后重启huawei-csi-node服务，重启期间，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。参考命令如下：
>```
>kubectl delete pods -n huawei-csi -l app=huawei-csi-node
>```

企业存储配置iSCSI协议类型的后端配置文件示例如下：

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

分布式存储配置iSCSI协议类型的后端配置文件示例如下：

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

OceanDisk存储配置iSCSI协议类型的后端配置文件示例如下：

```yaml
storage: "oceandisk-san"
name: "oceandisk-iscsi-125"
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

## 配置FC协议类型的存储后端{#section4385132433717}

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>如果要使用FC协议类型，请确保在安装华为CSI前，主机和存储的FC网络已联通，如未FC网络未打通，请在打通FC网络之后重启huawei-csi-node服务，重启期间，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。参考命令如下：
>```
>kubectl delete pods -n huawei-csi -l app=huawei-csi-node
>```

企业存储配置FC协议类型的后端配置文件示例如下：

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

OceanDisk存储配置FC协议类型的后端配置文件示例如下：

```yaml
storage: "oceandisk-san"
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

## 配置NVMe over RoCE协议类型的存储后端{#section887724419372}

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>如果要使用NVMe over RoCE协议类型，请确保在安装华为CSI前，主机和存储的NVMe over RoCE网络已联通，如未NVMe over RoCE网络未打通，请在打通NVMe over RoCE网络之后重启huawei-csi-node服务，重启期间，不能使用华为CSI创建新的资源，或者对已有的PVC做挂载/卸载操作。参考命令如下：
>```
>kubectl delete pods -n huawei-csi -l app=huawei-csi-node
>```

企业存储配置NVMe over RoCE协议类型的后端配置文件示例如下：

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

OceanDisk存储配置NVMe over RoCE协议类型的后端配置文件示例如下：

```yaml
storage: "oceandisk-san"
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

## 配置NVMe over FC协议类型的存储后端{#section11434793492}

企业存储配置NVMe over FC协议类型的后端配置文件示例如下：

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

## 配置NFS协议类型的存储后端{#section13980125055717}

企业存储配置NFS协议类型的后端配置文件示例如下：

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

分布式存储配置NFS协议类型的后端配置文件示例如下：

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

## 配置NFS+协议类型的存储后端{#section1890151345820}

企业存储配置NFS+协议类型的后端配置文件示例如下：

```yaml
storage: "oceanstor-nas"
name: "nfs-plus-155"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "nfs+"
  portals:        
    - "192.168.128.155"
    - "192.168.128.156"
maxClientThreads: "30"
```

## 配置SCSI协议类型的存储后端{#section51803398537}

分布式存储配置SCSI协议类型的后端配置文件示例如下：

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

## 配置DPC协议类型的存储后端{#section1094123525411}

分布式NAS存储配置DPC协议类型的后端配置文件示例如下：

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

分布式DTree存储配置DPC协议类型的后端配置文件示例如下：

```yaml
storage: "fusionstorage-dtree"
name: "dpc-dtree"
namespace: "huawei-csi"
urls:
  - "https://192.168.129.155:8088"
parameters:      
  protocol: "dpc"
  parentname: "parent-filesystem" # 可选字段，可选择在StorageClass中配置
maxClientThreads: "30"
```

## 配置Dtree类型的存储后端{#section6768010203620}

企业存储配置Dtree类型后端配置文件示例如下：

```yaml
storage: "oceanstor-dtree"
name: "nfs-dtree"
namespace: "huawei-csi"
urls:
- "https://192.168.129.155:8088"
parameters:
  protocol: "nfs"
  parentname: "parent-filesystem" # 可选字段，可选择在StorageClass中配置
  portals:
    - "192.168.128.155"
maxClientThreads: "30"
```

分布式存储配置Dtree类型后端配置文件示例如下：

```yaml
storage: "fusionstorage-dtree"
name: "nfs-dtree"
namespace: "huawei-csi"
urls:
- "https://192.168.129.155:8088"
parameters:
  protocol: "nfs"
  parentname: "parent-filesystem" # 可选字段，可选择在StorageClass中配置
  portals:
    - "192.168.128.155"
maxClientThreads: "30"
```

## 配置双活类型的存储后端{#section175945335494}

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>-   配置NAS双活前，需要在两台存储设备之间配置双活关系，包含远端设备、双活域等，仅支持文件系统双活域工作模式为双活AA模式，配置操作请参考对应存储型号的产品文档。
>-   对接NAS双活后端的账号必须为存储租户的租户管理员账号。
>-   除NAS双活后端外，其他后端的管理URL不能配置为在已建立双活关系的租户的逻辑管理端口的URL。
>-   使用双活类型的存储后端时，请勿发放普通文件系统。否则，在逻辑端口漂移场景下，有业务中断的风险。

CSI支持在对接OceanStor或OceanStor Dorado，并在存储侧发放NFS类型的双活卷时。需要配置互为双活的存储后端，具体操作为分别创建两个配置文件，逐一创建后端。

本示例展示了如何为华为OceanStor或OceanStor Dorado存储配置双活类型的后端。首先创建本端的存储后端配置文件nfs-hypermetro-155.yaml：

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

创建本端后端完成后，创建远端的存储后端配置文件nfs-hypermetro-157.yaml：

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

