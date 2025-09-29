---
title: "A Pod Is in the ContainerCreating State for a Long Time When It Is Being Created"
linkTitle: "A Pod Is in the ContainerCreating State for a Long Time When It Is Being Created"
description: 
weight: 3
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

When a Pod is being created, the Pod is in the  **ContainerCreating**  state for a long time. Check the huawei-csi-node log \(for details, see  [Viewing Huawei CSI Logs](/docs/common-o-m-operations/collecting-information/viewing-huawei-csi-logs)\). No Pod creation information is recorded in the huawei-csi-node log. After the  **kubectl get volumeattachment**  command is executed, the name of the PV used by the Pod is not displayed in the  **PV**  column. After a long period of time \(more than ten minutes\), the Pod is normally created and the Pod status changes to  **Running**.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

The kube-controller-manager component of Kubernetes is abnormal.

## Solution or Workaround{#en-us_topic_0000001279996521_section164471213145410}

Contact container platform engineers to rectify the fault.

