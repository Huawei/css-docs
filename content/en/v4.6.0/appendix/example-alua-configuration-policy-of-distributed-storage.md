---
title: "Example ALUA Configuration Policy of Distributed Storage"
linkTitle: "Example ALUA Configuration Policy of Distributed Storage"
description: 
weight: 3
---

**Example 1:**  The configuration file content is as follows:

```yaml
parameters:
  ALUA:
    "*":
      switchoverMode: Enable_alua
      pathType: optimal_path
    node1:
      switchoverMode: Enable_alua
      pathType: non_optimal_path
```

If the host name is  **node1**, both of the preceding ALUA configuration sections can be used to configure initiators. According to the configuration policy rules in  [Configuring ALUA Parameters for a Distributed Storage Backend](/docs/advanced-features/configuring-alua/configuring-alua-using-helm/configuring-alua-parameters-for-a-distributed-storage-backend), the priority of the second configuration section \(where  **HostName**  is  **node1**\) is higher than that of the first configuration section \(where  **HostName**  is  **\***\).

**Example 2:**  The configuration file content is as follows:

```yaml
parameters:
  ALUA:
    node[0-9]:
      switchoverMode: Enable_alua
      pathType: optimal_path
    node[5-7]:
      switchoverMode: Enable_alua
      pathType: non_optimal_path
```

If the host name is  **node6**, both of the preceding ALUA configuration sections can be used to configure initiators. According to the configuration policy rules in  [Configuring ALUA Parameters for a Distributed Storage Backend](/docs/advanced-features/configuring-alua/configuring-alua-using-helm/configuring-alua-parameters-for-a-distributed-storage-backend), select the first ALUA configuration section to configure initiators.

**Example 3:**  The configuration file content is as follows:

```yaml
parameters:
  ALUA:
    node1$:
      switchoverMode: Enable_alua
      pathType: optimal_path
    node10$:
      switchoverMode: Enable_alua
      pathType: non_optimal_path
```

According to the configuration policy rules in  [Configuring ALUA Parameters for a Distributed Storage Backend](/docs/advanced-features/configuring-alua/configuring-alua-using-helm/configuring-alua-parameters-for-a-distributed-storage-backend): For host  **node1**, select the first ALUA configuration section to configure initiators. For host  **node10**, select the second ALUA configuration section to configure initiators.  **^**  matches the beginning of a character string, and  **$**  matches the end of a character string.

