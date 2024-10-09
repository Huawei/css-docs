---
title: "动态卷供应典型场景StorageClass配置示例"
linkTitle: "动态卷供应典型场景StorageClass配置示例"
description: 
weight: 1
---

[存储类（StorageClass）](https://kubernetes.io/docs/concepts/storage/storage-classes/)为管理员提供了描述存储 "类" 的方法。 不同的类型可能会映射到一组不同的能力定义。Kubernetes集群用户可基于StorageClass进行动态卷制备。

使用SAN存储时可参考示例文件/examples/sc-lun.yaml，使用NAS存储时可参考示例文件/examples/sc-fs.yaml。

典型场景下StorageClass配置请参考如下示例：

-   [StorageClass中设置后端和存储池](#section114859014540)
-   [StorageClass中设置NFS访问方式](#section128347019144)
-   [StorageClass中设置Dtree类型](#section1642719478395)
-   [StorageClass中设置本地文件系统访问方式](#section1155962772514)
-   [StorageClass中设置DPC访问方式](#section022191784519)
-   [StorageClass中设置应用类型](#section576688153313)
-   [StorageClass中设置软配额](#section73983205817)
-   [StorageClass中设置双活](#section12170214277)
-   [StorageClass中设置挂载目录权限](#section156891316272)
-   [StorageClass中设置QoS](#section1016612587584)
-   [CCE / CCE Agile平台中配置StorageClass](#section132301459161017)

## StorageClass中设置后端和存储池{#section114859014540}

如果在一个Kubernetes集群中配置了多个华为后端，或者一个华为后端提供多个存储池，建议在StorageClass中配置指定的后端和存储池信息，避免华为CSI随机选择后端和存储池，导致卷所在的存储不符合规划。

SAN存储设置后端和存储池可以参考如下配置示例。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
allowVolumeExpansion: true
parameters:
  backend: "san-181" # 存储后端名称
  pool: "pool001" # 存储池名称
  volumeType: lun
  allocType: thin
```

NAS存储设置后端和存储池可以参考如下配置示例。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
allowVolumeExpansion: true
parameters:
  backend: "san-181" # 存储后端名称
  pool: "pool001" # 存储池名称
  volumeType: fs
  allocType: thin
  authClient: "*"
```

## StorageClass中设置NFS访问方式{#section128347019144}

容器使用NFS文件系统作为存储资源时，可以参考如下配置示例。该示例中，NFS挂载时指定版本为4.1。

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
  - nfsvers=4.1 # NFS挂载时指定版本为4.1
```

## StorageClass中设置Dtree类型{#section1642719478395}

容器使用Dtree作为存储资源时，可以参考如下配置示例。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dtree
  volumeType: dtree # 卷类型配置为 dtree
  allocType: thin
  authClient: "*" 
mountOptions:
  - nfsvers=4.1
```

## StorageClass中设置本地文件系统访问方式{#section1155962772514}

容器使用企业存储或者分布式存储的LUN作为存储资源时，且需要格式化文件系统为本地文件系统时，可以参考如下示例。

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

## StorageClass中设置DPC访问方式{#section022191784519}

当容器使用OceanStor Pacific系列存储，且存储支持DPC协议访问时，可以在StorageClass中配置DPC访问的挂载参数。本例中设置挂载时使用“**acl**”做鉴权参数，使用“**cnflush**”为设置异步刷盘模式。

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
  - acl # 鉴权参数
  - cnflush # 设置异步刷盘模式
```

## StorageClass中设置应用类型{#section576688153313}

当容器使用OceanStor Dorado存储的LUN作为存储时，如果使用存储默认的应用类型无法满足某些业务的I/O模型要求（如容器对外提供数据库OLAP服务），可以在StorageClass中配置应用类型，提升存储性能。具体需要使用的应用类型请参考对应存储产品的产品文档说明。

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
  applicationType: Oracle_OLAP # 配置应用类型
```

## StorageClass中设置软配额{#section73983205817}

当容器使用OceanStor Pacific系列存储的文件系统作为存储时，可以在StorageClass中配置软配额信息，可以参考如下配置示例。

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
  storageQuota: '{"spaceQuota": "softQuota", "gracePeriod": 100}' # 配置软配额
mountOptions:
  - nfsvers=3
```

## StorageClass中设置QoS{#section1016612587584}

容器使用企业存储或者分布式存储作为存储资源时，可以为容器使用的存储资源设置QoS，从而保证这些容器对存储读写满足一定的服务等级。

不同型号或版本的存储支持的QoS设置不同，请参考[表 支持的QoS配置](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应StorageClass参数说明#table74841513116)找到对应存储的配置项。本示例中的后端是OceanStor Dorado存储，其他存储可以参考本例设置。

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
  qos: '{"IOTYPE": 2, "MINIOPS": 1000}' # 配置QoS
```

>![](/public_sys-resources/zh/icon-note.gif) 
>-   OceanStor V5 租户用户不支持配置QoS策略。
>-   配置QoS后只能在新建的PVC上生效；对于同名StorageClass已经发放的PVC，不能自动添加QoS

## StorageClass中设置双活{#section12170214277}

容器使用NFS双活文件系统作为存储资源时，可以参考如下配置示例。该示例中，使用的后端是支持双活的后端，且配置“**hyperMetro**”参数为“true”。

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
  hyperMetro: "true" # 发放双活卷
  allocType: thin
  authClient: "*"
```

>![](/public_sys-resources/zh/icon-notice.gif)  
>-   发放NAS双活卷前，需要在两台存储设备之间配置双活关系，包含远端设备、双活域等，仅支持文件系统双活域工作模式为双活AA模式，配置操作请参考对应存储型号的产品文档。
>-   若存储发生故障，逻辑管理端口可能产生漂移，在漂移状态下删除NAS双活卷后，需手动清理对应的存储资源。

## StorageClass中设置挂载目录权限{#section156891316272}

当需要修改容器内挂载目录的权限时，可以在StorageClass中配置目录权限信息，可以参考如下配置示例。

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
  rootSquash: "no_root_squash"  # 该参数仅支持NAS存储
  allSquash: "no_all_squash"   # 该参数仅支持NAS存储
```

完成StorageClass配置后，进行如下步骤创建StorageClass。

1.  执行以下命令，基于该yaml文件创建StorageClass。

    ```
    kubectl create -f mysc.yaml
    ```

2.  执行以下命令，查看当前已经创建的StorageClass信息。

    ```
    kubectl get sc
    ```

    命令结果示例如下。

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           false                  34s
    ```

    创建StorageClass后，就可以使用该StorageClass进行创建PV或者PVC。

>![](/public_sys-resources/zh/icon-notice.gif)  
>在StorageClass的使用中请注意如下事项：
>-   **针对StorageClass进行的修改将不会在已经创建的PV上生效。您需要删除这些PV，并重新使用修改后的StorageClass创建才能应用修改的参数。**

## CCE / CCE Agile平台中配置StorageClass{#section132301459161017}

在CCE / CCE Agile平台中创建NAS类型StorageClass，可以参考如下配置示例。其中provisioner保持和values.yaml文件中driverName一致。

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

在CCE / CCE Agile平台中创建Block类型StorageClass，可以参考如下配置示例。其中provisioner保持和values.yaml文件中driverName一致。

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

