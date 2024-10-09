---
title: "Deleting a Storage Backend"
linkTitle: "Deleting a Storage Backend"
description: 
weight: 4
---

>![](/public_sys-resources/en/icon-notice.gif) 
>Do not delete a storage backend when a volume management operation is being performed on it.

## Example of Deleting a Backend{#section20764568435}

1.  Run the following command to obtain information about a storage backend.

    ```
    oceanctl get backend 
    ```

    The following is an example of the command output.

    ```
    NAMESPACE     NAME         PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-1    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    huawei-csi    backend-2    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.158:8088  
    ```

2.  Run the following command to delete the specified storage backend.

    ```
    oceanctl delete backend backend-1
    ```

3.  Run the following command to check the deletion result.

    ```
    oceanctl get backend backend-1
    ```

    The following is an example of the command output. If  **not found**  is displayed, the deletion is successful.

    ```yaml
    Error from server (NotFound): backend "backend-1" not found
    ```

