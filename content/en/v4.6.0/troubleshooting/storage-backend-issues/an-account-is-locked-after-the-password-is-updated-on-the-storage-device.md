---
title: "An Account Is Locked After the Password Is Updated on the Storage Device"
linkTitle: "An Account Is Locked After the Password Is Updated on the Storage Device"
description: 
weight: 3
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

After a user changes the password on the storage device, the account is locked.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

CSI uses the account and password configured on the storage device to log in to the storage device. After the account password is changed on the storage device, CSI attempts to log in to the storage device again after the login fails. Take OceanStor Dorado as an example. The default login policy is that an account will be locked after three consecutive password verification failures. Therefore, when CSI retries for more than three times, the account will be locked.

## Solution or Workaround{#section155945247573}

1.  If the backend account is  **admin**, run the following command to set the number of huawei-csi-controller service copies to 0. If an account other than  **admin**  is used, skip this step.

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=0
    ```

2.  Log in to the storage device as user  **admin**  and modify the login policy. Take OceanStor Dorado as an example. On DeviceManager, choose  **Settings**  \>  **User and Security**  \>  **Security Policies**  \>  **Login Policy**, click  **Modify**, and disable  **Account Lockout**.
3.  If the backend account is  **admin**, run the following command to restore the number of CSI Controller copies using  **--replicas=**_\*_. In the following example, the number of copies is restored to  **1**. Change it based on site requirements. If an account other than  **admin**  is used, skip this step.

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=1
    ```

4.  Use the oceanctl tool to change the storage backend password. For details about how to change the backend password, see  [Updating a Storage Backend](/docs/storage-backend-management/managing-storage-backends/updating-a-storage-backend).
5.  Log in to the storage device as user admin and modify the login policy. Take OceanStor Dorado as an example. On DeviceManager, choose  **Settings**  \>  **User and Security**  \>  **Security Policies**  \>  **Login Policy**, click  **Modify**, and enable  **Account Lockout**.

