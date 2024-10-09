---
title: "Description of oceanctl Commands"
linkTitle: "Description of oceanctl Commands"
description: 
weight: 3
---

## Obtaining Help Information{#section1117411442508}

-   Obtain the oceanctl help information.

    ```
    oceanctl --help
    ```

-   Check the oceanctl version.

    ```
    oceanctl version
    ```

-   Specify the custom log file directory. The following example describes how to check the oceanctl version.

    ```
    oceanctl version --log-dir=/path/to/custom
    ```

## Creating a Storage Backend{#section68961238162410}

-   Run the following command to obtain the help information about creating a backend.

    ```
    oceanctl create backend -h
    ```

-   Run the following command to create a storage backend based on the specified yaml file.

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml
    ```

-   Run the following command to create a storage backend based on the specified json file. The  **huawei-csi-configmap**  file can be exported only in json format.

    ```
    oceanctl create backend -f /path/to/configmap.json -i json
    ```

-   Run the following command to create a storage backend in the specified namespace.

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml -n <namespace>
    ```

-   Run the following command to create a storage backend and ignore the storage backend name verification, for example, uppercase letters and underscores \(\_\). Do not run this command unless necessary.

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml --not-validate-name
    ```

-   Run the following command to create a storage backend and specify  **provisioner**.  **csi.oceanstor.com**  is the driver name specified during installation. For details, see  [4](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-the-cce-or-cce-agile-platform#li4307135252018).

    >![](/public_sys-resources/en/icon-note.gif)
    >This command is used only when a backend is created on the CCE or CCE Agile platform.

    ```
    oceanctl create backend -f /path/to/backend.yaml  -i yaml --provisioner=csi.oceanstor.com
    ```

## Querying a Storage Backend{#section1746114212110}

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

## Updating a Storage Backend{#section20491912142516}

-   Run the following command to obtain the help information about updating a backend.

    ```
    oceanctl update backend -h
    ```

-   Run the following command to update the specified storage backend in the default namespace.

    ```
    oceanctl update backend <backend-name> --password
    ```

-   Run the following command to update a storage backend in the specified namespace.

    ```
    oceanctl update backend <backend-name> -n <namespace> --password
    ```

## Deleting a Storage Backend{#section1473712371285}

-   Run the following command to obtain the help information about deleting a backend.

    ```
    oceanctl delete backend -h
    ```

-   Run the following command to delete the specified storage backend in the default namespace.

    ```
    oceanctl delete backend <backend-name> 
    ```

-   Run the following command to delete all storage backends in the default namespace.

    ```
    oceanctl delete backend  --all
    ```

-   Run the following command to delete a storage backend in the specified namespace.

    ```
    oceanctl delete backend <backend-name...> -n <namespace>
    ```

## Creating a Storage Backend Certificate{#section16801122125214}

-   Run the following command to obtain the help information about querying a certificate.

    ```
    oceanctl create cert -h
    ```

-   Run the following command to create a certificate for a single storage backend in the default namespace based on the specified .crt certificate file.

    ```
    oceanctl create cert <name> -f /path/to/cert.crt -b <backend-name> 
    ```

-   Run the following command to create a certificate for a single storage backend in the specified namespace based on the specified .crt certificate file.

    ```
    oceanctl create cert <name> -f /path/to/cert.crt -b <backend-name> -n <namespace>
    ```

-   Run the following command to create a certificate for a single storage backend in the specified namespace based on the specified .pem certificate file.

    ```
    oceanctl create cert <name> -f /path/to/cert.pem -b <backend-name> -n <namespace>
    ```

## Querying a Storage Backend Certificate{#section11544144412475}

-   Run the following command to obtain the help information about querying a certificate.

    ```
    oceanctl get cert -h
    ```

-   Run the following command to query the certificate of a specified storage backend in the default namespace.

    ```
    oceanctl get cert -b <backend-name>
    ```

-   Run the following command to query the certificate of a specified storage backend in the specified namespace.

    ```
    oceanctl get cert -b <backend-name> -n <namespace>
    ```

## Updating a Storage Backend Certificate{#section1215513912218}

-   Run the following command to obtain the help information about updating a certificate.

    ```
    oceanctl update cert -h
    ```

-   Run the following command to update a certificate for a specified storage backend in the default namespace based on the specified .crt certificate file.

    ```
    oceanctl update cert -b <backend-name> -f /path/to/cert.crt
    ```

-   Run the following command to update a certificate for a specified storage backend in the specified namespace based on the specified .crt certificate file.

    ```
    oceanctl update cert -b <backend-name> -n <namespace> -f /path/to/cert.crt
    ```

-   Run the following command to update a certificate for a specified storage backend in the specified namespace based on the specified .pem certificate file.

    ```
    oceanctl update cert -b <backend-name> -n <namespace> -f /path/to/cert.pem
    ```

## Deleting a Storage Backend Certificate{#section1394334712223}

-   Run the following command to obtain the help information about deleting a certificate.

    ```
    oceanctl delete cert -h
    ```

-   Run the following command to delete the certificate of a specified storage backend in the default namespace.

    ```
    oceanctl delete cert -b <backend-name> 
    ```

-   Run the following command to delete the certificate of a specified storage backend in the specified namespace.

    ```
    oceanctl delete cert -b <backend-name> -n <namespace>
    ```

