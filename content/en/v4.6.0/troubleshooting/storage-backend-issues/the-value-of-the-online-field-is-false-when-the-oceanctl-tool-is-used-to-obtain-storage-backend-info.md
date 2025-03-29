---
title: "The Value of the ONLINE Field Is \"false\" When the oceanctl Tool Is Used to Obtain Storage Backend Information"
linkTitle: "The Value of the ONLINE Field Is \"false\" When the oceanctl Tool Is Used to Obtain Storage Backend Information"
description: 
weight: 2
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

The following command is executed to check storage backend status:

```
oceanctl get backend
```

The value of the  **ONLINE**  field of the storage backend is  **false**:

```
NAMESPACE    NAME                  PROTOCOL   STORAGETYPE     SN                     STATUS   ONLINE   Url
huawei-csi   backend-201-nas-nfs   nfs        oceanstor-nas   XXXXXXXXXXXXXX000006   Bound    false    https://192.168.129.157:8088
```

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

When CSI uses the account and password entered during storage backend creation to log in to the storage backend, if the login fails due to either of the following reasons, the  **ONLINE**  field will be set to  **false**.

1.  Incorrect account password: The possible cause is that the password is changed on the storage backend but not updated in the Kubernetes cluster. For details about how to solve this problem, see  [Solution or Workaround](#section155945247573).
2.  Locked account. For details about how to solve this problem, see  [An Account Is Locked After the Password Is Updated on the Storage Device](/docs/troubleshooting/storage-backend-issues/an-account-is-locked-after-the-password-is-updated-on-the-storage-device).

## Solution or Workaround{#section155945247573}

1.  Obtain the latest account password.
2.  Update the storage backend password by following the instructions in  [Updating the Password of a Storage Backend Using oceanctl](/docs/storage-backend-management/managing-storage-backends/updating-a-storage-backend/updating-the-password-of-a-storage-backend-using-oceanctl).

