---
title: "oceanctl更新存储后端密码"
linkTitle: "oceanctl更新存储后端密码"
description: 
weight: 1
---

## 更新后端示例{#section1968753944018}

1.  执行以下命令获取更新存储后端帮助。

    ```
    oceanctl update backend -h
    ```

    命令结果示例如下：

    ```
    Update a backend for Ocean Storage in Kubernetes
    
    Usage:
      oceanctl update backend <name> [flags]
    
    Examples:
      # Update backend account information in default(huawei-csi) namespace
      oceanctl update backend <name>  --password
    
      # Update backend account information in specified namespace
      oceanctl update backend <name> -n namespace --password
    
    Flags:
      -h, --help               help for backend
      -n, --namespace string   namespace of resources
          --password           Update account password
    ```

2.  执行以下命令更新存储后端信息。

    ```
    oceanctl update backend backend-1 --password
    ```

    根据提示输入用户名和新密码：

    ```
    Please enter this backend user name:admin
    Please enter this backend password:
    
    backend/backend-1 updated
    ```

