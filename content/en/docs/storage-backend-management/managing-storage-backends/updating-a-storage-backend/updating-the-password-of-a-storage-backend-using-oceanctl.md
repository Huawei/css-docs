---
title: "Updating the Password of a Storage Backend Using oceanctl"
linkTitle: "Updating the Password of a Storage Backend Using oceanctl"
description: 
weight: 1
---

## Obtaining the Help Information About Updating a Backend{#section17783193220443}

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
    
      # Update backend account information with ldap authentication mode in default(huawei-csi) namespace
      oceanctl update backend <name> --password --authenticationMode=ldap
    
      # Update backend account information with local authentication mode in default(huawei-csi) namespace
      oceanctl update backend <name> --password --authenticationMode=local
    
      # Update backend account information with ldap authentication mode in specified namespace
      oceanctl update backend <name> -n namespace --password --authenticationMode=ldap
    
    Flags:
          --authenticationMode string   Specify authentication mode
      -h, --help                        help for backend
      -n, --namespace string            namespace of resources
          --password                    Update account password
    
    Global Flags:
          --log-dir string   Specify the directory for printing log files. (default "/var/log/huawei")
    ```

## Example of Updating the Password of a Backend{#section1968753944018}

1.  Run the following command to update a storage backend. In the command,  _backend-name_  indicates the name of the storage backend to be updated.

    ```
    oceanctl update backend backend-name --password
    ```

    Enter the user name and new password as prompted:

    ```
    Please enter this backend user name:admin
    Please enter this backend password:
    
    backend/backend-name updated
    ```

