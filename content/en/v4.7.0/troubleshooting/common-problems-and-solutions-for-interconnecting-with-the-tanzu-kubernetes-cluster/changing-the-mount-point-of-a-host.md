---
title: "Changing the Mount Point of a Host"
linkTitle: "Changing the Mount Point of a Host"
description: 
weight: 2
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

A Pod fails to be created, and error message "mount point does not exist" is recorded in Huawei CSI logs.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

The native Kubernetes cluster in the  **pods-dir**  directory of huawei-csi-node is inconsistent with the Tanzu Kubernetes cluster.

## Solution or Workaround{#en-us_topic_0000001279996521_section164471213145410}

1.  Go to the  **helm/esdk/**  directory and run the  **vi values.yaml**  command to open the configuration file.

    ```
    vi values.yaml
    ```

2.  Change the value of  **kubeletConfigDir**  to the actual installation directory of kubelet.

    ```yaml
    # Specify kubelet config dir path.
    # kubernetes and openshift is usually /var/lib/kubelet
    # Tanzu is usually /var/vcap/data/kubelet
    kubeletConfigDir: /var/vcap/data/kubelet
    ```

