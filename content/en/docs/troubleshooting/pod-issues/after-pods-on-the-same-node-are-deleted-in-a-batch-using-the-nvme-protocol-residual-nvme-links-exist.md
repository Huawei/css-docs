---
title: "After Pods on the Same Node Are Deleted in a Batch Using the NVMe Protocol, Residual NVMe Links Exist on the Node"
linkTitle: "After Pods on the Same Node Are Deleted in a Batch Using the NVMe Protocol, Residual NVMe Links Exist on the Node"
description: 
weight: 12
---

## Symptom{#en-us_topic_0234872004_section1566717121452}

In the NVMe protocol scenario, when pods on the same node are deleted in a batch, the pods are successfully deleted, but the NVMe links on the node are not cleared.

```
# nvme list-subsys
nvme-subsys0 - NQN=nqn.xxx.nvme:nvm-subsystem-sn-xxxxxxx
\
 +- nvme0 tcp traddr=xxx.xxx.xxx.xxx,trsvcid=4420,src_addr=xxx.xxx.xxx.xxx live 
 +- nvme1 tcp traddr=xxx.xxx.xxx.xxx,trsvcid=4420,src_addr=xxx.xxx.xxx.xxx live 
```

## Root Cause Analysis{#en-us_topic_0234872004_section1425013451056}

If the NVMe protocol is used, the device paths on the host are cleared only after the host is unmapped from the storage resources. When multiple pods are mounted to the same volume and the pods are deleted in a batch, the CSI in the NodeUnstageVolume phase \(unmount phase\) cannot detect the device path cleanup in the subsequent ControllerUnpublishVolume phase \(unmap phase\). As a result, the NVMe links cannot be cleared in a timely manner.

## Solution or Workaround{#en-us_topic_0234872004_section350653016492}

1.  The residual NVMe links do not affect the CSI functions. However, the storage resources that are mounted subsequently scan for the corresponding device paths based on the residual links. If the number of links does not need to be reduced, you do not need to clear the residual links.
2.  If the number of links to be mounted later needs to be reduced, you can manually delete the residual links on the node. For example, to clear the links in the preceding symptom, run the following commands:

    ```
    nvme disconnect -d nvme0
    nvme disconnect -d nvme1
    ```

