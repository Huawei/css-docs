---
title: "Failed to Start the huawei-csi-node Service with Error Message /var/lib/iscsi is not a directory Reported"
linkTitle: "Failed to Start the huawei-csi-node Service with Error Message /var/lib/iscsi is not a directory Reported"
description: 
weight: 1
---

## Symptom{#en-us_topic_0000001086137838_section1566717121452}

The huawei-csi-node service cannot be started. When you run the  **kubectl describe daemonset huawei-csi-node -n huawei-csi**  command, error message "/var/lib/iscsi is not a directory" is reported.

## Root Cause Analysis{#en-us_topic_0000001086137838_section1425013451056}

The  **/var/lib/iscsi**  directory does not exist in the huawei-csi-node container.

## Solution or Workaround{#en-us_topic_0000001086137838_section350653016492}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Go to the directory where the Helm project is located. If the previous Helm project cannot be found, copy the  **helm**  directory in the component package to any directory on the master node. For details about the component package path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).
3.  Go to the  **templates**  directory and find the  **huawei-csi-node.yaml**  file.

    ```
    cd /templates
    ```

4.  Run the following command to set  **path**  in  **huawei-csi-node.yaml**  \>  **volumes**  \>  **iscsi-dir**  \>  **hostPath**  to  **/var/lib/iscsi**, save the file, and exit.

    ```
    vi huawei-csi-node.yaml
    ```

5.  Run the following command to upgrade the Helm chart. The upgrade command will update the Deployment, DaemonSet, and RBAC resources. In the preceding command,  _helm-huawei-csi_  indicates the custom chart name and  _huawei-csi_  indicates the custom namespace.

    ```
    helm upgrade helm-huawei-csi ./  -n huawei-csi -f values.yaml
    ```

    The following is an example of the command output.

    ```
    Release "helm-huawei-csi" has been upgraded. Happy Helming!
    NAME: helm-huawei-csi
    LAST DEPLOYED: Thu Jun  9 07:58:15 2022
    NAMESPACE: huawei-csi
    STATUS: deployed
    REVISION: 2
    TEST SUITE: None
    ```

