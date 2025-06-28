---
title: "After a Pod Fails to Be Created or kubelet Is Restarted, Logs Show That the Mount Point Already Exists"
linkTitle: "After a Pod Fails to Be Created or kubelet Is Restarted, Logs Show That the Mount Point Already Exists"
description: 
weight: 7
---

## Symptom{#section16564369537}

When a Pod is being created, the Pod is always in the  **ContainerCreating**  state. Alternatively, after kubelet is restarted, logs show that the mount point already exists. Check the log information of huawei-csi-node \(for details, see  [Viewing Huawei CSI Logs](/docs/common-operations/collecting-information/viewing-huawei-csi-logs)\). The error information is:  **The mount /var/lib/kubelet/pods/xxx/mount is already exist, but the source path is not /var/lib/kubelet/plugins/kubernetes.io/xxx/globalmount**

## Root Cause Analysis{#section135642617536}

The root cause of this problem is that Kubernetes performs repeated mounting operations.

## Solution or Workaround{#section75642613539}

Run the following command to unmount the existing path. In the command,  **/var/lib/kubelet/pods/xxx/mount**  indicates the existing mount path displayed in the logs.

```
umount /var/lib/kubelet/pods/xxx/mount
```

