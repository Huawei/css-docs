---
title: "A webhook Fails to Be Called When the oceanctl Tool Is Used to Manage Backends"
linkTitle: "A webhook Fails to Be Called When the oceanctl Tool Is Used to Manage Backends"
description: 
weight: 1
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

After the webhook configuration is changed, for example, the value of the  **webhookPort**  parameter is changed, an error is reported indicating that a webhook fails to be called when the oceanctl tool is used to manage backends, as shown in the following figure.

![](/css-docs/figures/en-us_image_0000001996023254.png)

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

After the webhook configuration changes, the  **validatingwebhookconfiguration**  resource becomes invalid.

## Solution or Workaround{#section1730118471221}

1.  Run the following command to delete the  **validatingwebhookconfiguration**  resource.

    ```
    kubectl delete validatingwebhookconfiguration storage-backend-controller.xuanwu.huawei.io
    ```

2.  Run the following command to restart CSI Controller. Run the  **--replicas=**_\*_  command to set the number of CSI Controller copies to be restored. In the following example, the number of copies to be restored is 1. Change it based on site requirements.

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=0 
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=1
    ```

3.  Run the following command to check whether CSI Controller is successfully started.

    ```
    kubectl get pod -n huawei-csi
    ```

    The following is an example of the command output. If the Pod status is  **Running**, Controller is successfully started.

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-58d5b6b978-s2dsq   9/9     Running   0          19s
    huawei-csi-node-dt6nd                    3/3     Running   0          77m
    ```

