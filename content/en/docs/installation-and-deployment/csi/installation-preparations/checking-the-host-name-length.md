---
title: "Checking the Host Name Length"
linkTitle: "Checking the Host Name Length"
description: 
weight: 7
---

If Huawei CSI is used to connect to NAS storage, skip this step.

If Huawei CSI is used to connect to SAN storage, check the host name length of nodes in the cluster before installing Huawei CSI. The host name length must be less than or equal to 27 characters.

If the host name contains more than 27 characters, the extra part will be truncated when the host is created on the storage device. As a result, multiple nodes in the cluster may be mapped to the same host on the storage device.

