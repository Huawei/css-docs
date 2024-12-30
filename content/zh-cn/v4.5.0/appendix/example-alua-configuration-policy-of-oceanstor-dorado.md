---
title: "OceanStor Dorado ALUA特性配置策略样例"
linkTitle: "OceanStor Dorado ALUA特性配置策略样例"
description: 
weight: 2
---

**例1**.配置文件如下：

```
parameters:
  ALUA:
    "*":
     accessMode: 1
     hyperMetroPathOptimized: 1
   node1:
      accessMode: 1
      hyperMetroPathOptimized: 0
```

对于主机名为“node1”，上述ALUA配置段都能用于配置启动器。根据[配置华为企业存储后端的ALUA参数](/v4.5.0/advanced-features/configuring-alua/configuring-alua-using-helm/configuring-alua-parameters-for-a-huawei-enterprise-storage-backend)中的配置策略规则，优先级顺序为第2条配置段（HostName为"node1"）高于第1条配置段（HostName为"\*"）。

**例2**.配置文件如下：

```yaml
parameters:
  ALUA:
   node[0-9]:
     accessMode: 1
     hyperMetroPathOptimized: 1
   node[5-7]:
     accessMode: 1
     hyperMetroPathOptimized: 0
```

对于主机名为“node6”的主机，上述ALUA配置段都能用于配置启动器。根据[配置华为企业存储后端的ALUA参数](/v4.5.0/advanced-features/configuring-alua/configuring-alua-using-helm/configuring-alua-parameters-for-a-huawei-enterprise-storage-backend)中的配置策略规则，选择第一条ALUA配置段来配置启动器。

**例3**.配置文件如下：

```yaml
parameters:
  node1$:
    node[0-9]:
    accessMode: 1
    hyperMetroPathOptimized: 1
  node10$:
    accessMode: 1
    hyperMetroPathOptimized: 0
```

根据[配置华为企业存储后端的ALUA参数](/v4.5.0/advanced-features/configuring-alua/configuring-alua-using-helm/configuring-alua-parameters-for-a-huawei-enterprise-storage-backend)中的配置策略规则，对于主机名为“node1”的主机，选择第一条ALUA配置段来配置启动器；对于主机名为“node10”的主机，选择第二条ALUA配置段来配置启动器。^表示匹配字符串的开头，$表示匹配字符串的结尾。

