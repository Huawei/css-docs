---
title: "A Backend Fails to Be Created Using the oceanctl Tool and Error Message \"context deadline exceeded\" Is Displayed"
linkTitle: "A Backend Fails to Be Created Using the oceanctl Tool and Error Message \"context deadline exceeded\" Is Displayed"
description: 
weight: 2
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

A user fails to create a storage backend using the oceanctl tool, and "failed to call webhook: xxx :context deadline exceeded; error: exist status 1" is displayed on the console.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

When a storage backend is created, the webhook service provided by CSI is invoked to verify the connectivity with the storage management network and the storage account and password. The possible causes are as follows:

-   Huawei CSI fails to verify the connectivity of the storage management network.
-   The communication between kube-apiserver and CSI webhook is abnormal.

## Huawei CSI Fails to Verify the Connectivity of the Storage Management Network{#section17680127184319}

Perform the following steps to check whether Huawei CSI fails to verify the connectivity of the storage management network.

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  <a name="li1895283018493"></a>Run the following command to obtain CSI service information.  _huawei-csi_  indicates the namespace where the CSI services are deployed.

    ```
    kubectl get pod -n huawei-csi -owide
    ```

    The following is an example of the command output.

    ```
    NAME                        READY   STATUS    RESTARTS   AGE   IP         NODE       NOMINATED NODE   READINESS GATES
    huawei-csi-controller-xxx   9/9     Running   0          19h   host-ip1   host-1     <none>           <none>
    huawei-csi-node-mnqbz       3/3     Running   0          19h   host-ip1   host-1     <none>           <none>
    ```

3.  Log in to the node where huawei-csi-controller resides, for example,  **host-1**  in  [2](#li1895283018493).
4.  Go to the  **/var/log/huawei**  directory.

    ```yaml
    # cd /var/log/huawei
    ```

5.  View the  **storage-backend-controller**  log. The following uses the storage connection timeout as an example.

    ```
    tail -n 1000 storage-backend-controller
    ```

    The following is a log example.

    ```
    2024-01-01 06:30:44.280661 1 [INFO]: Try to login https://192.168.129.155:8088/deviceManager/rest
    2024-01-01 06:31:44.281626 1 [ERROR]: Send request method: POST, Url: https://192.168.129.155:8088/deviceManager/rest/xx/sessions, error: Post "https://192.168.129.155:8088/deviceManager/rest/xx/sessions": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
    2024-01-01 06:31:44.281793 1 [WARNING]: Login https://192.168.129.155:8088/deviceManager/rest error due to connection failure, gonna try another Url
    2024-01-01 06:31:44.291668 1 [INFO]: Finished validateCreate huawei-csi/backend-test.
    2024-01-01 06:31:44.291799 1 [ERROR]: Failed to validate StorageBackendClaim, error: unconnected
    ```

6.  If the log contains information about login timeout, login failure, or long request duration, check the connectivity between the host machine and the storage or the network status.
7.  If no request is recorded in the log, the communication between kube-apiserver and CSI webhook is abnormal.

## Abnormal Communication Between kube-apiserver and CSI Webhook{#section56891019204012}

Contact the Kubernetes platform administrator to check the network between kube-apiserver and CSI webhook. For example, if kube-apiserver has an HTTPS proxy, the CSI webhook service may fail to be accessed.

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>In the temporary workaround, the webhook resource will be deleted. This resource is used to check whether the entered account information is correct and whether the connection to the storage can be set up when a storage backend is created. Therefore, deleting this resource affects only the verification during backend creation and does not affect other functions. Pay attention to the following:
>-   Ensure that the host machine where the huawei-csi-controller service is located can properly communicate with the storage.
>-   Ensure that the entered account and password are correct.

1.  Run the following command to view CSI webhook information.

    ```
    kubectl get validatingwebhookconfiguration storage-backend-controller.xuanwu.huawei.io
    ```

    The following is an example of the command output.

    ```
    NAME                                          WEBHOOKS   AGE
    storage-backend-controller.xuanwu.huawei.io   1          4d22h
    ```

2.  Contact the Kubernetes platform administrator to check whether the communication between kube-apiserver and CSI webhook is abnormal.
3.  Perform the following temporary workaround: Run the following command to delete the webhook.

    ```
    kubectl delete validatingwebhookconfiguration storage-backend-controller.xuanwu.huawei.io
    ```

4.  Create a storage backend. For details, see  [Managing Storage Backends](/docs/storage-backend-management/managing-storage-backends).
5.  If the communication between kube-apiserver and CSI webhook is restored, you need to reconstruct the webhook. In this case, run the following command to restart CSI Controller and restore the number of CSI Controller copies by specifying  **--replicas=\***. In the following example, the number is restored to  **1**. Change it based on actual requirements.

    Change the number of copies to 0 first.

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=0 
    ```

    Then restore the number of copies to the original number.

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=1
    ```

