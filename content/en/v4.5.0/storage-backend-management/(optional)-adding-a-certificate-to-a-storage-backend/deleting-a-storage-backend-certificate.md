---
title: "Deleting a Storage Backend Certificate"
linkTitle: "Deleting a Storage Backend Certificate"
description: 
weight: 4
---

## Procedure{#section14609953142910}

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

2.  Run the following command to obtain information about the certificate of the specified storage backend.

    ```
    oceanctl get cert -b backend-1
    ```

    The following is an example of the command output.

    ```
    NAMESPACE   NAME    BOUNDBACKEND    
    huawei-csi  cert-1  backend-1  
    ```

3.  Run the following command to delete the certificate of the specified storage backend.

    ```
    oceanctl delete cert -b backend-1
    ```

4.  Check the deletion result.

    ```
    oceanctl get cert -b backend-1
    ```

    The following is an example of the command output. If  **no cert found**  is displayed, the deletion is successful.

    ```yaml
    Error from server (NotFound): no cert found on backend backend-1 in huawei-csi namespace
    ```

