---
title: "When a PVC Is Created, the PVC Is in the Pending State"
linkTitle: "When a PVC Is Created, the PVC Is in the Pending State"
description: 
weight: 1
---

## Symptom{#en-us_topic_0000001207958677_section1566717121452}

A PVC is created. After a period of time, the PVC is still in the  **Pending**  state.

## Root Cause Analysis{#en-us_topic_0000001207958677_section1425013451056}

Cause 1: A StorageClass with the specified name is not created in advance. As a result, Kubernetes cannot find the specified StorageClass name when a PVC is created.

Cause 2: The storage pool capability does not match the StorageClass capability. As a result, huawei-csi fails to select a storage pool.

Cause 3: An error code \(for example, 50331651\) is returned by a RESTful interface of the storage. As a result, huawei-csi fails to create a PVC.

Cause 4: The storage does not return a response within the timeout period set by huawei-csi. As a result, huawei-csi returns a timeout error to Kubernetes.

Cause 5: Other causes.

## Solution or Workaround{#en-us_topic_0000001207958677_section350653016492}

When a PVC is created, if the PVC is in the  **Pending**  state, you need to take different measures according to the following causes.

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to view details about the PVC.

    ```
    kubectl describe pvc mypvc
    ```

3.  Perform the corresponding operation according to the  **Events**  information in the detailed PVC information.
    -   If the PVC is in the  **Pending**  state due to cause 1, perform the following steps.

        ```yaml
        Events:
          Type     Reason              Age                  From                         Message
          ----     ------              ----                 ----                         -------
          Warning  ProvisioningFailed  0s (x15 over 3m24s)  persistentvolume-controller  storageclass.storage.k8s.io "mysc" not found
        ```

        1.  Delete the PVC.
        2.  Create a StorageClass. For details, see  [StorageClass Configuration Examples in Typical Dynamic Volume Provisioning Scenarios](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/storageclass-configuration-examples-in-typical-dynamic-volume-provisioning-scenarios).
        3.  Create a PVC. For details, see  [PVC Parameters for Dynamic Volume Provisioning](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning).

    -   If the PVC is in the  **Pending**  state due to cause 2, perform the following steps.

        ```
        Events:
          Type     Reason                Age                From                                                                                       Message
          ----     ------                ----               ----                                                                                       -------
          Normal   Provisioning          63s (x3 over 64s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  External provisioner is provisioning volume for claim "default/mypvc"
          Warning  ProvisioningFailed    63s (x3 over 64s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  failed to provision volume with StorageClass "mysc": rpc error: code = Internal desc = failed to select pool, the capability filter failed, error: failed to select pool, the final filter field: replication, parameters map[allocType:thin replication:True size:1099511627776 volumeType:lun]. please check your storage class
        ```

        1.  Delete the PVC.
        2.  Delete the StorageClass.
        3.  Modify the  **StorageClass.yaml**  file based on the  **Events**  information.
        4.  Create a StorageClass. For details, see  [StorageClass Configuration Examples in Typical Dynamic Volume Provisioning Scenarios](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/storageclass-configuration-examples-in-typical-dynamic-volume-provisioning-scenarios).
        5.  Create a PVC. For details, see  [PVC Parameters for Dynamic Volume Provisioning](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning).

    -   If the PVC is in the  **Pending**  state due to cause 3, contact Huawei engineers.

        ```
        Events:
          Type     Reason                Age                From                                                                                       Message
          ----     ------                ----               ----                                                                                       -------
          Normal   Provisioning          63s (x4 over 68s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  External provisioner is provisioning volume for claim "default/mypvc"
          Warning  ProvisioningFailed    62s (x4 over 68s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  failed to provision volume with StorageClass "mysc": rpc error: code = Internal desc = Create volume map[ALLOCTYPE:1 CAPACITY:20 DESCRIPTION:Created from Kubernetes CSI NAME:pvc-63ebfda5-4cf0-458e-83bd-ecc PARENTID:0] error: 50331651
        ```

    -   If the PVC is in the  **Pending**  state due to cause 4, perform the following steps.

        ```
        Events:
          Type     Reason                Age                From                                                                                       Message
          ----     ------                ----               ----                                                                                       -------
          Normal   Provisioning          63s (x3 over 52s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  External provisioner is provisioning volume for claim "default/mypvc"
          Warning  ProvisioningFailed    63s (x3 over 52s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  failed to provision volume with StorageClass "mysc": rpc error: code = Internal desc = context deadline exceeded (Client.Timeout exceeded while awaiting headers)
        ```

        1.  Wait for 10 minutes and check the PVC details again by referring to this section.
        2.  If it is still in the  **Pending**  state, contact Huawei engineers.

    -   If the PVC is in the  **Pending**  state due to cause 5, contact Huawei engineers.

