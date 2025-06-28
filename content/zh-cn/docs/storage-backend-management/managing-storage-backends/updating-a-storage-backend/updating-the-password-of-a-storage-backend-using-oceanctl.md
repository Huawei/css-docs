---
title: "oceanctl更新存储后端密码"
linkTitle: "oceanctl更新存储后端密码"
description: 
weight: 1
---

## 获取更新后端帮助信息{#section17783193220443}

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
    
      # Update backend account information with ldap authentication mode in default(huawei-csi) namespace
      oceanctl update backend <name> --password --authenticationMode=ldap
    
      # Update backend account information with local authentication mode in default(huawei-csi) namespace
      oceanctl update backend <name> --password --authenticationMode=local
    
      # Update backend account information with ldap authentication mode in specified namespace
      oceanctl update backend <name> -n namespace --password --authenticationMode=ldap
    
    Flags:
          --authenticationMode string   Specify authentication mode
      -h, --help                        help for backend
      -n, --namespace string            namespace of resources
          --password                    Update account password
    
    Global Flags:
          --log-dir string   Specify the directory for printing log files. (default "/var/log/huawei")
    ```

## 更新后端密码示例{#section1968753944018}

1.  执行以下命令更新存储后端信息，其中backend-name为待更新后端名称。

    ```
    oceanctl update backend backend-name --password
    ```

    根据提示输入用户名和新密码：

    ```
    Please enter this backend user name:admin
    Please enter this backend password:
    
    backend/backend-name updated
    ```

