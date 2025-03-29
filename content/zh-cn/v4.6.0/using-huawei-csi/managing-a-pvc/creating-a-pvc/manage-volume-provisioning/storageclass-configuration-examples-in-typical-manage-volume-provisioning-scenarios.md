---
title: "纳管卷供应典型场景StorageClass配置示例"
linkTitle: "纳管卷供应典型场景StorageClass配置示例"
description: 
weight: 1
---

纳管卷供应典型场景下StorageClass配置请参考如下示例：

-   [StorageClass中设置后端和存储池](#section114859014540)
-   [StorageClass中设置NFS访问方式](#section128347019144)
-   [StorageClass中设置本地文件系统访问方式](#section1155962772514)
-   [StorageClass中设置DPC访问方式](#section022191784519)
-   [StorageClass中设置挂载目录权限](#section1356811882616)

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
  backend: "iscsi-san-181"
  pool: "pool001"
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
  backend: "iscsi-nas-181"
  pool: "pool001"
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
mountOptions:
  - nfsvers=4.1 # NFS挂载时指定版本为4.1
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

## StorageClass中设置挂载目录权限{#section1356811882616}

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
  fsPermission: "777" # 设置目录权限
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

    命令结果示例如下：

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           false                  34s
    ```

    创建StorageClass后，就可以使用该StorageClass进行创建PV或者PVC。

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>在纳管卷供应场景下，StorageClass的使用中请注意如下事项：
>-   **针对StorageClass进行的修改将不会在已经创建的PV上生效。您需要删除这些PV，并重新使用修改后的StorageClass创建才能应用修改的参数。**

