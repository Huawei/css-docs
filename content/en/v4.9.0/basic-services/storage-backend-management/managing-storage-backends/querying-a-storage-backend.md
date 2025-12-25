---
title: "Querying a Storage Backend"
linkTitle: "Querying a Storage Backend"
description: 
weight: 1
---

-   Run the following command to obtain the help information about querying a backend.

    ```
    oceanctl get backend -h
    ```

-   Run the following command to query a single storage backend in the default namespace.

    ```
    oceanctl get backend <backend-name>
    ```

-   Run the following command to query all storage backends in the specified namespace.

    ```
    oceanctl get backend -n <namespace>
    ```

-   Run the following command to format the output. Currently,  **json**,  **yaml**, and  **wide**  are supported.

    ```
    oceanctl get backend <backend-name> -o json
    ```

