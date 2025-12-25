---
title: "更新存储后端登陆认证模式"
linkTitle: "更新存储后端登陆认证模式"
description: 
weight: 2
---

## 更新后端登录认证类型为LDAP示例{#section29338116524}

1.  执行以下命令更新存储后端信息，其中backend-name为待更新后端名称。

    ```
    oceanctl update backend backend-name --password --authenticationMode=ldap
    ```

    根据提示输入用户名和新密码：

    ```
    Please enter this backend user name:admin
    Please enter this backend password:
    
    backend/backend-name updated
    ```

