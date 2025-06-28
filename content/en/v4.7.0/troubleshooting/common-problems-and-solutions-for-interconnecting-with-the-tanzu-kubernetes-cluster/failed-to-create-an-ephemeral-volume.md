---
title: "Failed to Create an Ephemeral Volume"
linkTitle: "Failed to Create an Ephemeral Volume"
description: 
weight: 4
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

A  [generic ephemeral volume](https://kubernetes.io/docs/concepts/storage/ephemeral-volumes/#generic-ephemeral-volumes)  fails to be created, and the error message  **PodSecurityPolicy: unable to admit pod: \[spec.volumes\[0\]: Invalid value: "ephemeral": ephemeral volumes are not allowed to be used spec.volumes\[0\]**  is displayed.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

The current PSP policy does not contain the permission to use ephemeral volumes.

## Solution or Workaround{#en-us_topic_0000001279996521_section164471213145410}

Add the permission to use ephemeral volumes to the default PSP  **pks-privileged**  and  **pks-restricted**. The following is an example of modifying  **pks-privileged**:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to modify the  **pks-privileged**  configuration.

    ```
    kubectl edit psp pks-privileged
    ```

3.  Add  **ephemeral**  to  **spec.volumes**. The following is an example.

    ```yaml
    # Please edit the object below. Lines beginning with a '#' will be ignored,
    # and an empty file will abort the edit. If an error occurs while saving this file will be
    # reopened with the relevant failures.
    #
    apiVersion: policy/v1beta1
    kind: PodSecurityPolicy
    metadata:
      annotations:
        apparmor.security.beta.kubernetes.io/allowedProfileName: '*'
        seccomp.security.alpha.kubernetes.io/allowedProfileNames: '*'
      creationTimestamp: "2022-10-11T08:07:00Z"
      name: pks-privileged
      resourceVersion: "1227763"
      uid: 2f39c44a-2ce7-49fd-87ca-2c5dc3bfc0c6
    spec:
      allowPrivilegeEscalation: true
      allowedCapabilities:
      - '*'
      supplementalGroups:
        rule: RunAsAny
      volumes:
      - glusterfs
      - hostPath
      - iscsi
      - nfs
      - persistentVolumeClaim
      - ephemeral
    ```

4.  Run the following command to check whether the addition is successful.

    ```
    kubectl get psp pks-privileged -o yaml
    ```

