---
title: "Failed to Create a Pod Because the iscsi\_tcp Service Is Not Started Properly When the Kubernetes Platform Is Set Up for the First Time"
linkTitle: "Failed to Create a Pod Because the iscsi\_tcp Service Is Not Started Properly When the Kubernetes Platform Is Set Up for the First Time"
description: 
weight: 9
---

## Symptom{#en-us_topic_0234872004_section1566717121452}

When you create a Pod, error  **Cannot connect ISCSI portal \*.\*.\*.\*: libkmod: kmod\_module\_insert\_module: could not find module by name='iscsi\_tcp'**  is reported in the  **/var/log/huawei-csi-node**  log.

## Root Cause Analysis{#en-us_topic_0234872004_section1425013451056}

The iscsi\_tcp service may be stopped after the Kubernetes platform is set up and the iSCSI service is installed. You can run the following command to check whether the service is stopped.

```
lsmod | grep iscsi | grep iscsi_tcp
```

The following is an example of the command output.

```
iscsi_tcp              18333  6 
libiscsi_tcp           25146  1 iscsi_tcp
libiscsi               57233  2 libiscsi_tcp,iscsi_tcp
scsi_transport_iscsi    99909  3 iscsi_tcp,libiscsi
```

## Solution or Workaround{#en-us_topic_0234872004_section350653016492}

Run the following command to manually load the iscsi\_tcp service.

```
modprobe iscsi_tcp
lsmod | grep iscsi | grep iscsi_tcp
```

