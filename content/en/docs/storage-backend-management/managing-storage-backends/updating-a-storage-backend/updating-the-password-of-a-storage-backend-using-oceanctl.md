---
title: "Updating the Password of a Storage Backend Using oceanctl"
linkTitle: "Updating the Password of a Storage Backend Using oceanctl"
description: 
weight: 1
---

## Example of Updating a Backend{#section1968753944018}

1.  Run the following command to obtain the help information about updating a storage backend.

    ```
    oceanctl update backend -h
    ```

    The following is an example of the command output.

    ```
    Update a backend for Ocean Storage in Kubernetes
    
    Usage:
      oceanctl update backend <name> [flags]
    
    Examples:
      # Update backend account information in default(huawei-csi) namespace
      oceanctl update backend <name>  --password
    
      # Update backend account information in specified namespace
      oceanctl update backend <name> -n namespace --password
    
    Flags:
      -h, --help               help for backend
      -n, --namespace string   namespace of resources
          --password           Update account password
    ```

2.  Run the following command to update a storage backend.

    ```
    oceanctl update backend backend-1 --password
    ```

    Enter the user name and new password as prompted:

    ```
    Please enter this backend user name:admin
    Please enter this backend password:
    
    backend/backend-1 updated
    ```

