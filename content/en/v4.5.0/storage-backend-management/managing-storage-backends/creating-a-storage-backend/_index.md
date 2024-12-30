---
title: "Creating a Storage Backend"
linkTitle: "Creating a Storage Backend"
description: 
weight: 1
---

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>1.  When oceanctl is used to create a storage backend, the entered account and key information is stored in the  [Secret](https://kubernetes.io/docs/concepts/configuration/secret/)  object. It is recommended that the customer container platform encrypt the Secret object based on the suggestions of the supplier or K8s community. For details about how to encrypt the Secret object in the K8s community, see  [Enable Encryption at Rest](https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/).
>2.  When a backend is created using a .json file, the backend name of an earlier version may contain uppercase letters or underscores \(\_\). In this case, the old name is remapped to a new name. The mapping process automatically occurs and does not affect the original functions. For example,  **ABC\_123**  is mapped to  **abc-123-fd68e**. The mapping rules are as follows:
>    -   Uppercase letters are converted to lowercase letters.
>    -   An underscore \(\_\) is converted to a hyphen \(-\).
>    -   A 5-digit hash code is added to the end.
>3.  If a storage backend is connected to a vStore, the vStore name cannot be changed after the storage backend is created.

## Procedure{#section193534374443}

1.  Prepare the backend configuration file, for example,  **backend.yaml**. For details, see  [Examples of Storage Backend Configuration Files in Typical Scenarios](/docs/storage-backend-management/managing-storage-backends/creating-a-storage-backend/examples-of-storage-backend-configuration-files-in-typical-scenarios). To create multiple backends, separate them with  **---**.

    ```
    storage: "oceanstor-san"
    name: "backend-1"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.157:8088"
    pools:
      - "StoragePool001"
    parameters:
      protocol: "roce"
      portals:
        - "10.10.30.20"
        - "10.10.30.21"
    maxClientThreads: "30"
    ---
    storage: "oceanstor-san"
    name: "backend-2"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.158:8088"
    pools:
      - "StoragePool001"
    parameters:
      protocol: "roce"
      portals:
        - "10.10.30.20"
        - "10.10.30.21"
    maxClientThreads: "30"
    ```

2.  Run the following command to create a storage backend.

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml
    ```

    The following is an example of the command output.

    ```
    NUMBER  CONFIGURED    NAME        STORAGE              URLS                
    1       false         backend-1   oceanstor-san        https://192.168.129.157:8088 
    2       false         backend-2   oceanstor-san        https://192.168.129.158:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

3.  Enter the serial number of the backend to be created and enter the account and password.

    ```
    Please enter the backend number to configure (Enter 'exit' to exit):1
    Please enter this backend user name:admin
    Please enter this backend password:
    
    Backend backend-1 is configured
    NUMBER  CONFIGURED    NAME         STORAGE              URLS               
    1       true          backend-1    oceanstor-san        https://192.168.129.157:8088 
    2       false         backend-2    oceanstor-san        https://192.168.129.158:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

4.  Check the storage backend creation result.

    ```
    oceanctl get backend
    ```

    The following is an example of the command output. If the backend status is  **Bound**, the creation is successful.

    ```
    NAMESPACE     NAME         PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-1    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    huawei-csi    backend-2    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.158:8088   
    ```



