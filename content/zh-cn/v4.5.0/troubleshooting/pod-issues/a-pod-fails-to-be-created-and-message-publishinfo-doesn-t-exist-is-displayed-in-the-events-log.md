---
title: "创建Pod失败，Events日志显示“publishInfo doesn't exist”"
linkTitle: "创建Pod失败，Events日志显示“publishInfo doesn't exist”"
description: 
weight: 6
---

## 现象描述{#section16564369537}

创建Pod时，Pod一直处于ContainerCreating状态，查看Pod中有打印告警事件：rpc error: code = Internal desc = publishInfo doesn't exist。

## 根因分析{#section135642617536}

按照CSI协议约定，工作负载要使用一个PV卷时，CO（Container Orchestration system，通过RPC请求与CSI插件通信）会调用CSI插件提供的[CSI协议](https://github.com/container-storage-interface/spec/blob/master/spec.md)中的“ControllerPublishVolume”接口（huawei-csi-controller服务提供）完成PV卷的映射，然后调用CSI插件提供的“NodeStageVolume”接口（huawei-csi-node服务提供）完成PV卷的挂载。导致出现“publishInfo doesn't exist”错误的原因是在一次完整的挂载时，仅huawei-csi-node服务收到了“NodeStageVolume”请求，而在此之前huawei-csi-controller服务未收到“ControllerPublishVolume”请求，导致huawei-csi-controller服务未完成PV卷的映射，没有把映射信息传递给huawei-csi-node服务。

## 解决措施{#section75642613539}

解决该问题，需要触发Kubernetes调用“ControllerPublishVolume”接口。

如果集群中所有旧版本创建的工作负载均触发了该操作，则后续将不会出现该问题。

## 操作步骤{#section1883055741114}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，获取工作负载所在节点信息。

    ```
    kubectl get pod error-pod -n error-pod-in-namespace -owide
    ```

    命令结果示例如下：

    ```
    NAME      READY   STATUS              RESTARTS   AGE   IP       NODE        NOMINATED NODE   READINESS GATES
    pod-nfs   0/1     ContainerCreating   0          3s    <none>   node-1      <none>           <none>
    ```

3.  将该工作负载漂移至其他节点。
4.  若在集群内无法完成漂移，可在原节点完成工作负载重建，即进行删除-新建操作。
5.  观察该工作负载是否成功拉起，如果拉起失败请联系华为工程师。

## 集群工作负载排查{#section96497192258}

Kubernetes调用CSI插件完成卷映射时，将使用VolumeAttachment资源保存映射信息，用于表示将指定的卷从指定的节点上附加或分离。由于该问题是由于publishInfo不存在导致，因此可通过查看VolumeAttachment资源信息排查集群中其他工作负载是否存在该问题。具体步骤如下：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  <a name="li18768174613266"></a>执行以下命令，获取VolumeAttachment信息，并保留ATTACHER字段为csi.huawei.com的资源，其中csi.huawei.com为华为CSI驱动名称，可在values.yaml文件中配置，配置项为csiDriver.driverName，配置项详情描述参考[表4](/v4.5.0/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table188162213437)。

    ```
    kubectl get volumeattachments.storage.k8s.io 
    ```

    命令结果示例如下：

    ```
    NAME          ATTACHER         PV       NODE     ATTACHED   AGE
    csi-47abxx   csi.huawei.com   pvc-1xx   node-1   true       12h
    ```

3.  <a name="li876824620267"></a>执行以下命令查看VolumeAttachment资源详情，其中csi-47abxx为[2](#li18768174613266)中查询到的资源名称。

    ```
    kubectl get volumeattachments.storage.k8s.io csi-47abxx -o yaml
    ```

    命令结果示例如下：

    ```
    kind: VolumeAttachment
    metadata:
      annotations:
        csi.alpha.kubernetes.io/node-id: '{"HostName":"node-1"}'
       finalizers:
      - external-attacher/csi-huawei-com
      name: csi-47abxxx
      uid: 0c87fa8a-c3d6-4623-acb8-71d6206d030d
    spec:
      attacher: csi.huawei.com
      nodeName: debian-node
      source:
        persistentVolumeName: pvc-1xx
    status:
      attached: true
      attachmentMetadata:
         publishInfo: '{<PUBLISH-INFO>}'
    ```

4.  <a name="li143811934379"></a>若[3](#li876824620267)中查询到的资源中存在status.attachmentMetadata.publishInfo，则证明node-1节点上使用pvc-1xx创建的若干工作负载不会存在本FAQ描述的错误，其中node-1和pvc-1xx为[2](#li18768174613266)中查询结果。若status.attachmentMetadata.publishInfo不存在，请参考[解决措施](#section75642613539)章节解决。
5.  存在多个VolumeAttachment资源时，重复执行[3](#li876824620267)\~[4](#li143811934379)。

