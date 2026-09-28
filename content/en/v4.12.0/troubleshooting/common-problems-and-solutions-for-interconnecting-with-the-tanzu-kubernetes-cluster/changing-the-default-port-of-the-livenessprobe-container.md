---
title: "Changing the Default Port of the livenessprobe Container"
linkTitle: "Changing the Default Port of the livenessprobe Container"
description: 
weight: 3
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

The livenessprobe container of the huawei-csi-controller component keeps restarting.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

The default port \(9808\) of the livenessprobe container of huawei-csi-controller conflicts with the existing vSphere CSI port of Tanzu.

## Solution or Workaround{#en-us_topic_0000001279996521_section164471213145410}

Change the default port of the livenessprobe container to an idle port.

1.  Go to the  **helm/esdk**  directory and run the  **vi values.yaml**  command to open the configuration file.

    ```
    vi values.yaml
    ```

2.  Change the default value  **9808**  of  **controller.livenessProbePort**  to an idle port, for example,  **9809**.

    ```yaml
    controller:
      livenessProbePort: 9809
    ```

3.  Update Huawei CSI using Helm. For details, see  [Upgrade Using Helm](/docs/installation-and-deployment/csi/upgrade/upgrade-using-helm).

