---
title: "Updating the Login Authentication Mode of a Storage Backend"
linkTitle: "Updating the Login Authentication Mode of a Storage Backend"
description: 
weight: 2
---

## Example of Updating the Backend Login Authentication Type to LDAP{#section29338116524}

1.  Run the following command to update a storage backend. In the command,  _backend-name_  indicates the name of the storage backend to be updated.

    ```
    oceanctl update backend backend-name --password --authenticationMode=ldap
    ```

    Enter the user name and new password as prompted:

    ```
    Please enter this backend user name:admin
    Please enter this backend password:
    
    backend/backend-name updated
    ```

