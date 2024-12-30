---
title: "A Pod Fails to Be Created and Message \"publishInfo doesn't exist\" Is Displayed in the Events Log"
linkTitle: "A Pod Fails to Be Created and Message \"publishInfo doesn't exist\" Is Displayed in the Events Log"
description: 
weight: 6
---

## Symptom{#section16564369537}

When a Pod is being created, the Pod keeps in the  **ContainerCreating**  state. It is found that the following alarm event is printed for the Pod:  **rpc error: code = Internal desc = publishInfo doesn't exist**

## Root Cause Analysis{#section135642617536}

As required by CSI, when a workload needs to use a PV, the Container Orchestration system \(CO system, communicating with the CSI plug-in using RPC requests\) invokes the ControllerPublishVolume interface \(provided by huawei-csi-controller\) in the  [CSI protocol](https://github.com/container-storage-interface/spec/blob/master/spec.md)  provided by the CSI plug-in to map the PV, and then invokes the NodeStageVolume interface \(provided by huawei-csi-node\) provided by the CSI plug-in to mount the PV. During a complete mounting operation, only the huawei-csi-node service receives the NodeStageVolume request. Before that, the huawei-csi-controller service does not receive the ControllerPublishVolume request. As a result, the huawei-csi-controller service does not map the PV volume and does not send the mapping information to the huawei-csi-node service. Therefore, error message  **publishInfo doesn't exist**  is reported.

## Solution{#section75642613539}

To solve this problem, Kubernetes needs to invoke the ControllerPublishVolume interface.

If this operation is triggered by all workloads created by earlier versions in the cluster, this problem will not occur.

## Procedure{#section1883055741114}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to obtain the information about the node where a workload is located.

    ```
    kubectl get pod error-pod -n error-pod-in-namespace -owide
    ```

    The following is an example of the command output.

    ```
    NAME      READY   STATUS              RESTARTS   AGE   IP       NODE        NOMINATED NODE   READINESS GATES
    pod-nfs   0/1     ContainerCreating   0          3s    <none>   node-1      <none>           <none>
    ```

3.  Fail over the workload to another node.
4.  If the failover cannot be completed in the cluster, you can delete the workload and create a new one on the original node.
5.  Check whether the workload is successfully started. If it fails to be started, contact Huawei technical support engineers.

## Checking Cluster Workloads{#section96497192258}

When Kubernetes invokes the CSI plug-in to complete volume mapping, the VolumeAttachment resource is used to save the mapping information, indicating that a specified volume is attached to or detached from a specified node. This problem occurs because publishInfo does not exist. You can view the VolumeAttachment resource information to check whether this problem is also involved in other workloads in the cluster. The procedure is as follows:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  <a name="li18768174613266"></a>Run the following command to obtain the VolumeAttachment information and retain resources whose  **ATTACHER**  field is  **csi.huawei.com**.  **csi.huawei.com**  indicates the Huawei CSI driver name and can be configured in the  **values.yaml**  file. The corresponding configuration item is  **csiDriver.driverName**. For details about the configuration item, see  [Table 4](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table188162213437).

    ```
    kubectl get volumeattachments.storage.k8s.io 
    ```

    The following is an example of the command output.

    ```
    NAME          ATTACHER         PV       NODE     ATTACHED   AGE
    csi-47abxx   csi.huawei.com   pvc-1xx   node-1   true       12h
    ```

3.  <a name="li876824620267"></a>Run the following command to view the VolumeAttachment resource details. In the following information,  **csi-47abxx**  is the resource name obtained in  [2](#li18768174613266).

    ```
    kubectl get volumeattachments.storage.k8s.io csi-47abxx -o yaml
    ```

    The following is an example of the command output.

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

4.  <a name="li143811934379"></a>If  **status.attachmentMetadata.publishInfo**  exists in the resource obtained in  [3](#li876824620267), the problem described in this FAQ is not involved in the workloads created using  **pvc-1xx**  on the  **node-1**  node.  **node-1**  and  **pvc-1xx**  are the query results in  [2](#li18768174613266). If  **status.attachmentMetadata.publishInfo**  does not exist, rectify the fault by referring to  [Solution](#section75642613539).
5.  If multiple VolumeAttachment resources exist, repeat  [3](#li876824620267)  to  [4](#li143811934379).

