---
title: "Updating Storage Backend Authentication Information"
linkTitle: "Updating Storage Backend Authentication Information"
description: 
weight: 3
---

To prevent the storage backend from becoming temporarily unavailable when the existing secret is modified directly, you are advised to update the authentication information by creating a new secret, replacing the reference to the existing secret, and then deleting the old secret.

## Procedure{#section051012213157}

1.  Prepare a new secret configuration file, for example,  **backend-secret-new.yaml**.

    ```yaml
    apiVersion: v1
    kind: Secret
    metadata:
      name: backend-demo-new
      namespace: huawei-csi
    type: Opaque
    stringData:
      user: "admin"
      password: "******"
      authenticationMode: "0"
    ```

2.  Create a secret.

    ```
    kubectl apply -f backend-secret-new.yaml
    ```

3.  Update StorageBackendClaim and update secretMeta to reference the new secret. CSI automatically synchronizes the new secret to StorageBackendContent and uses the new authentication information to log in to the storage device again.

    ```
    kubectl patch sbc backend-demo -n huawei-csi --type merge -p '{"spec":{"secretMeta":"huawei-csi/backend-demo-new"}}'
    ```

4.  Check the storage backend creation result.

    ```
    kubectl get StorageBackendContent
    ```

    The following is an example of the command output. If the online status of StorageBackendContent is  **true**, the update is successful.

    ```
    NAME              CLAIM                       SN               VENDORNAME   PROVIDERVERSION   ONLINE   AGE
    content-xxxxxxx   huawei-csi/backend-demo     xxxxxxxxxxxxxx   Huawei       4.12.0            true     53d
    ```

5.  Delete the old secret.

    ```
    kubectl delete secret backend-demo -n huawei-csi
    ```

