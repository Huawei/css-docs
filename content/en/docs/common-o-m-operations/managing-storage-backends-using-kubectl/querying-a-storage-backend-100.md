---
title: "Querying a Storage Backend"
linkTitle: "Querying a Storage Backend"
description: 
weight: 2
---

## Querying StorageBackendClaim{#section169128734716}

1.  Run the following command to query all storage backend claims in the default namespace:

    ```
    kubectl get sbc -n huawei-csi
    ```

    The following is an example of the command output:

    ```
    NAME             STORAGEBACKENDCONTENTNAME      STATUS   AGE
    backend-demo     content-xxxxxxxxxxxx           Bound    53d
    ```

2.  Run the following command to view storage backend claims in YAML format:

    ```
    kubectl get sbc backend-demo -n huawei-csi -o yaml
    ```

## Querying StorageBackendContent{#section116041549115320}

1.  Run the following command to query all storage backend instances:

    ```
    kubectl get sbct
    ```

    The following is an example of the command output:

    ```
    NAME              CLAIM                       SN               VENDORNAME   PROVIDERVERSION   ONLINE   AGE
    content-xxxxxxx   huawei-csi/backend-demo     xxxxxxxxxxxxxx   Huawei       4.12.0            true     53d
    ```

2.  Run the following command to view storage backend instances in YAML format:

    ```
    kubectl get sbct content-xxxxxxx -o yaml
    ```

