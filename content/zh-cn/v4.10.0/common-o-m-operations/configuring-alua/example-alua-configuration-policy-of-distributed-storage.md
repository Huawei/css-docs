---
title: "分布式存储ALUA特性配置策略样例"
linkTitle: "分布式存储ALUA特性配置策略样例"
description: 
weight: 5
---

**例1**.配置文件如下：

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

对于主机名为“node1”，上述ALUA配置段都能用于配置启动器。根据[配置分布式存储后端的ALUA参数](/docs/common-o-m-operations/configuring-alua/configuring-alua-parameters-for-a-distributed-storage-backend)中的配置策略规则，优先级顺序为第2条配置段（HostName为"node1"）高于第1条配置段（HostName为"\*"）。

**例2**.配置文件如下：

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

对于主机名为“node6”的主机，上述ALUA配置段都能用于配置启动器。根据[配置分布式存储后端的ALUA参数](/docs/common-o-m-operations/configuring-alua/configuring-alua-parameters-for-a-distributed-storage-backend)中的配置策略规则，选择第一条ALUA配置段来配置启动器。

**例3**.配置文件如下：

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

根据[配置分布式存储后端的ALUA参数](/docs/common-o-m-operations/configuring-alua/configuring-alua-parameters-for-a-distributed-storage-backend)中的配置策略规则，对于主机名为“node1”的主机，选择第一条ALUA配置段来配置启动器；对于主机名为“node10”的主机，选择第二条ALUA配置段来配置启动器。^表示匹配字符串的开头，$表示匹配字符串的结尾。

