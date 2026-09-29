---
title: "Managing Storage Backend Certificates"
linkTitle: "Managing Storage Backend Certificates"
description: 
weight: 4
---

CSI allows you to add a storage certificate to use the TLS/SSL protocol to encrypt data transmission channels, improving the security of communication with storage devices.

## Adding a Storage Certificate{#section1156241310541}

1.  Create a certificate. Take OceanStor Dorado as an example. For details about how to create a certificate,  [click here](https://support.huawei.com/hedex/hdx.do?docid=EDOC1100214756&id=EN-US_TOPIC_0000001595814228&lang=en).
2.  Run the following command to create a secret from the certificate file:

    ```
    kubectl create secret generic cert-1 --from-file=tls.crt=/path/to/cert.crt -n huawei-csi
    ```

3.  Run the following command to update the StorageBackendClaim, enable the certificate, and specify the certificate secret. The format of the certSecret field is  _<namespace\>_/_<secret-name\>_.

    ```
    kubectl patch sbc backend-demo -n huawei-csi --type merge -p '{"spec":{"useCert":true,"certSecret":"huawei-csi/cert-1"}}'
    ```

4.  Check the storage backend creation result.

    ```
    kubectl get StorageBackendContent
    ```

    The following is an example of the command output. If the online status of StorageBackendContent is  **true**, the update is successful.

    ```
    NAME              CLAIM                       SN               VENDORNAME   PROVIDERVERSION   ONLINE   AGE
    content-xxxxxxx   huawei-csi/backend-demo     xxxxxxxxxxxxxx   Huawei       4.13.0            true     53d
    ```

## Deleting a Storage Certificate{#section12785430175717}

1.  Delete the certificate configuration of StorageBackendClaim.

    ```
    kubectl patch sbc backend-demo -n huawei-csi --type merge -p '{"spec":{"useCert":false,"certSecret":""}}'
    ```

2.  Delete the certificate secret.

    ```
    kubectl delete secret cert-1 -n huawei-csi
    ```

