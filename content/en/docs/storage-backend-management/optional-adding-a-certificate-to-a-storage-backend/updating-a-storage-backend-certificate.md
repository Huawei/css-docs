---
title: "Updating a Storage Backend Certificate"
linkTitle: "Updating a Storage Backend Certificate"
description: 
weight: 3
---

Before updating a certificate, prepare a new certificate file and update the storage backend certificate by following the instructions provided in this section. If the certificate is no longer used, delete the certificate from the storage backend by referring to  [Deleting a Storage Backend Certificate](/docs/storage-backend-management/optional-adding-a-certificate-to-a-storage-backend/deleting-a-storage-backend-certificate).

## Procedure{#section127643118416}

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

2.  Run the following command to check whether the specified storage backend has a certificate.

    ```
    oceanctl get cert -b backend-1
    ```

    The following is an example of the command output.

    ```
    NAMESPACE   NAME    BOUNDBACKEND    
    huawei-csi  cert-1  backend-1  
    ```

3.  Run the following command to update the certificate of the specified storage backend.

    ```
    oceanctl update cert -b backend-1 -f /path/to/cert.crt
    ```

