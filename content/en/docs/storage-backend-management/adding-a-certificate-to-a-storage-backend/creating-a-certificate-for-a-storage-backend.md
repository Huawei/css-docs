---
title: "Creating a Certificate for a Storage Backend"
linkTitle: "Creating a Certificate for a Storage Backend"
description: 
weight: 1
---

## Prerequisites{#section414814741510}

A certificate has been created. Take OceanStor Dorado as an example. For details about how to create a certificate,  [click here](https://support.huawei.com/hedex/hdx.do?docid=EDOC1100214756&id=EN-US_TOPIC_0000001595814228&lang=en).

## Example of Creating a Certificate{#section1393413618152}

1.  Prepare a certificate file in advance, for example,  **cert.crt**.
2.  Run the following command to obtain information about a storage backend.

    ```
    oceanctl get backend  
    ```

    The following is an example of the command output.

    ```
    NAMESPACE     NAME         PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-1    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    huawei-csi    backend-2    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.158:8088  
    ```

3.  Run the following command to create a certificate for the specified storage backend.

    ```
    oceanctl create cert cert-1 -b backend-1 -f /path/to/cert.crt
    ```

4.  Check the certificate creation result.

    ```
    oceanctl get cert -b backend-1
    ```

    The following is an example of the command output.

    ```
    NAMESPACE    NAME    BOUNDBACKEND   
    huawei-csi   cert-1  backend-1 
    ```

