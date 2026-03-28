---
title: "查询存储后端"
linkTitle: "查询存储后端"
description: 
weight: 1
---

-   执行以下命令获取查询后端帮助。

    ```
    oceanctl get backend -h
    ```

-   执行以下命令查询默认命名空间下单个存储后端。

    ```
    oceanctl get backend <backend-name>
    ```

-   执行以下命令查询指定命名空间下所有存储后端。

    ```
    oceanctl get backend -n <namespace>
    ```

-   执行以下命令格式化输出，当前支持json，yaml和wide。

    ```
    oceanctl get backend <backend-name> -o json
    ```

