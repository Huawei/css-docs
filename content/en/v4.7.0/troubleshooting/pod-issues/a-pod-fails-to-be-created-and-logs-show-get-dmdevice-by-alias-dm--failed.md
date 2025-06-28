---
title: "A Pod Fails to Be Created and Logs Show \"Get DMDevice by alias: dm-* failed\""
linkTitle: "A Pod Fails to Be Created and Logs Show \"Get DMDevice by alias: dm-* failed\""
description: 
weight: 11
---

## Symptom{#en-us_topic_0234872004_section1566717121452}

When a Pod is created, the Pod is in the  **ContainerCreating**  status for a long time. In addition, the following error message is reported in the logs of huawei-csi-node \(for details, see  [Viewing Huawei CSI Logs](/docs/common-operations/collecting-information/viewing-huawei-csi-logs)\):

```
check device: dm-16 is a partition device failed. error: Get DMDevice by alias:dm-* failed. error: Can not get DMDevice by alias: dm-*
```

## Root Cause Analysis{#en-us_topic_0234872004_section1425013451056}

In the DM-Multipath configuration file, the  **user\_friendly\_names**  parameter is not set to  **yes**.

## Solution or Workaround{#en-us_topic_0234872004_section350653016492}

1.  Check whether the worker node where the Pod is running has volumes in use. If the node has volumes in use, migrate the Pod in use to another node.
2.  Configure the  **/etc/multipath.con**  file by following the instructions in  [Checking the Host Multipathing Configuration](/docs/installation-and-deployment/installation-preparations/checking-the-host-multipathing-configuration).
3.  Run the following command to restart the multipathing software.

    ```
    systemctl reload multipathd.service
    systemctl restart multipathd
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
    >Restarting the multipathing software may cause I/O interruption. Ensure that the worker node where the Pod is running has no volume in use before restarting the multipathing software.

