---
title: "A Pod Cannot Be Created Because the PSP Permission Is Not Created"
linkTitle: "A Pod Cannot Be Created Because the PSP Permission Is Not Created"
description: 
weight: 1
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

When huawei-csi-controller and huawei-csi-node are created, only the Deployment and DaemonSet resources are successfully created, and no Pod is created for the controller and node.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

The service account used for creating resources does not have the "use" permission of the PSP policy.

## Solution or Workaround{#en-us_topic_0000001279996521_section164471213145410}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the  **vi** _psp-use.yaml_  command to create a file named  **psp-use.yaml**

    ```
    vi psp-use.yaml
    ```

3.  Configure the  **psp-use.yaml**  file.

    ```
    apiVersion: rbac.authorization.k8s.io/v1
    kind: ClusterRole
    metadata:
      name: huawei-csi-psp-role
    rules:
    - apiGroups: ['policy']
      resources: ['podsecuritypolicies']
      verbs: ['use']
    ---
    apiVersion: rbac.authorization.k8s.io/v1
    kind: ClusterRoleBinding
    metadata:
      name: huawei-csi-psp-role-cfg
    roleRef:
      kind: ClusterRole
      name: huawei-csi-psp-role
      apiGroup: rbac.authorization.k8s.io
    subjects:
    - kind: Group
      apiGroup: rbac.authorization.k8s.io
      name: system:serviceaccounts:huawei-csi
    - kind: Group
      apiGroup: rbac.authorization.k8s.io
      name: system:serviceaccounts:default
    
    ```

4.  Run the following command to create the PSP permission.

    ```
    kubectl create -f psp-use.yaml
    ```

