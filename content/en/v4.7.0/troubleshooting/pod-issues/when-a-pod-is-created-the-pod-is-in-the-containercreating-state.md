---
title: "When a Pod Is Created, the Pod Is in the ContainerCreating State"
linkTitle: "When a Pod Is Created, the Pod Is in the ContainerCreating State"
description: 
weight: 2
---

## Symptom{#en-us_topic_0000001163875516_section1566717121452}

A Pod is created. After a period of time, the Pod is still in the  **ContainerCreating**  state. Check the log information \(for details, see  [Viewing Huawei CSI Logs](/docs/common-operations/collecting-information/viewing-huawei-csi-logs)\). The error message "Fibre Channel volume device not found" is displayed.

## Root Cause Analysis{#en-us_topic_0000001163875516_section1425013451056}

This problem occurs because residual disks exist on the host node. As a result, disks fail to be found when a Pod is created next time.

## Solution or Workaround{#en-us_topic_0000001163875516_section164471213145410}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  <a name="en-us_topic_0000001163875516_li134903196550"></a>Run the following command to query information about the node where the Pod resides.

    ```
    kubectl get pod -o wide
    ```

    The following is an example of the command output.

    ```
    NAME        READY   STATUS              RESTARTS   AGE     IP             NODE   NOMINATED NODE   READINESS GATES
    mypod       0/1     ContainerCreating   0          51s     10.244.1.224   node1  <none>           <none>
    ```

3.  Delete the Pod.
4.  Use a remote access tool, such as PuTTY, to log in to the  _node1_  node in the Kubernetes cluster through the management IP address.  _node1_  indicates the node queried in  [2](#en-us_topic_0000001163875516_li134903196550).
5.  Clear the residual drive letters. For details, see  [Solution or Workaround](/docs/troubleshooting/pod-issues/after-a-worker-node-in-the-cluster-breaks-down-and-recovers-pod-failover-is-complete-but-the-source#en-us_topic_0000001133091104_section350653016492).

