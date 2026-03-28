---
title: "Example ALUA Configuration Policy of OceanStor V5 Series"
linkTitle: "Example ALUA Configuration Policy of OceanStor V5 Series"
description: 
weight: 3
---

**Example 1:**  The configuration file content is as follows:

```yaml
parameters:
  ALUA:
    "*":
      MULTIPATHTYPE: 1
      FAILOVERMODE: 3
      SPECIALMODETYPE: 0
      PATHTYPE: 0
    node1:
      MULTIPATHTYPE: 1
      FAILOVERMODE: 3
      SPECIALMODETYPE: 0
      PATHTYPE: 1
```

If the host name is  **node1**, both of the preceding ALUA configuration sections can be used to configure initiators. According to the configuration policy rules in  [Configuring ALUA Parameters for a Huawei Enterprise Storage Backend](/docs/common-o-m-operations/configuring-alua/configuring-alua-parameters-for-a-huawei-enterprise-storage-backend), the priority of the second configuration section \(where  **HostName**  is  **node1**\) is higher than that of the first configuration section \(where  **HostName**  is  **\***\).

**Example 2:**  The configuration file content is as follows:

```yaml
parameters:
  ALUA:
    node[0-9]:
      MULTIPATHTYPE: 1
      FAILOVERMODE: 3
      SPECIALMODETYPE: 0
      PATHTYPE: 0
    node[5-7]:
      MULTIPATHTYPE: 1
      FAILOVERMODE: 3
      SPECIALMODETYPE: 0
      PATHTYPE: 1
```

If the host name is  **node6**, both of the preceding ALUA configuration sections can be used to configure initiators. According to the configuration policy rules in  [Configuring ALUA Parameters for a Huawei Enterprise Storage Backend](/docs/common-o-m-operations/configuring-alua/configuring-alua-parameters-for-a-huawei-enterprise-storage-backend), select the first ALUA configuration section to configure initiators.

**Example 3:**  The configuration file content is as follows:

```yaml
parameters:
  ALUA:
   node$:
      MULTIPATHTYPE: 1
      FAILOVERMODE: 3
      SPECIALMODETYPE: 0
      PATHTYPE: 0
   node10$:
      MULTIPATHTYPE: 1
      FAILOVERMODE: 3
      SPECIALMODETYPE: 0
      PATHTYPE: 1
```

According to the configuration policy rules in  [Configuring ALUA Parameters for a Huawei Enterprise Storage Backend](/docs/common-o-m-operations/configuring-alua/configuring-alua-parameters-for-a-huawei-enterprise-storage-backend): For host  **node1**, select the first ALUA configuration section to configure initiators. For host  **node10**, select the second ALUA configuration section to configure initiators.  **^**  matches the beginning of a character string, and  **$**  matches the end of a character string.

