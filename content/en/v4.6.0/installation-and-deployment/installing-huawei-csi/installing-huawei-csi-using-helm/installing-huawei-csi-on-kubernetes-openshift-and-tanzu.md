---
title: "Installing Huawei CSI on Kubernetes, OpenShift, and Tanzu"
linkTitle: "Installing Huawei CSI on Kubernetes, OpenShift, and Tanzu"
description: 
weight: 1
---

## Installation Procedure{#section9426125115349}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the cluster through the management IP address.
2.  Copy the  **helm**  directory in the Kubernetes CSI component package to any directory on the master node. For details about the Helm tool path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).
3.  Go to the  **helm/esdk**  working directory.

    ```
    cd helm/esdk
    ```

4.  Prepare the  **values.yaml**  file. Huawei CSI provides the  **values.yaml**  template file in the  **helm/esdk**  directory of the software package. You can also modify parameters according to  [Parameters in the values.yaml File of Helm](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm)  to customize Huawei CSI.
5.  Perform the following configuration before the installation:
    -   If the container platform is Kubernetes, skip this step.
    -   If the container platform is OpenShift, perform the configuration in  [Installation and Configuration on the OpenShift Platform](#section14977616204416).
    -   If the container platform is Tanzu, perform the configuration in  [Installation and Configuration on the Tanzu Platform](#section9291624164514).

6.  Run the following command to update the storage backend CRD.

    ```
    kubectl apply -f ./crds/backend/
    ```

7.  \(Optional\) Check snapshot-dependent components by following the instructions provided in  [Checking Volume Snapshot-Dependent Components](/docs/installation-and-deployment/installation-preparations/checking-volume-snapshot-dependent-components). After confirming that the components are correct, run the following command to update the snapshot CRD. If  **controller.snapshot.enabled**  is set to  **false**  or the Kubernetes version is earlier than v1.17, you can skip this step. For details, see  [Table 2](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table813124411459).

    ```
    kubectl apply -f ./crds/snapshot-crds/ --validate=false
    ```

8.  Run the following command to install Huawei CSI. In the preceding command,  _helm-huawei-csi_  indicates the custom Helm chart name,  **./**  indicates that the Helm project in the current directory is used, and  _huawei-csi_  indicates the custom Helm chart namespace.

    ```
    helm install helm-huawei-csi ./ -n huawei-csi --create-namespace
    ```

    The following is an example of the command output.

    ```yaml
    NAME: helm-huawei-csi
    LAST DEPLOYED: Wed Jun  8 11:50:28 2022
    NAMESPACE: huawei-csi
    STATUS: deployed
    REVISION: 1
    TEST SUITE: None
    ```

9.  After the huawei-csi service is deployed, run the following command to check whether the service is started.

    ```
    kubectl get pod -n huawei-csi
    ```

    The following is an example of the command output. If the Pod status is  **Running**, the installation is successful.

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   9/9     Running   0          24m
    huawei-csi-controller-6dfcc4b79f-csphc   9/9     Running   0          24m
    huawei-csi-node-g6f4k                    3/3     Running   0          20m
    huawei-csi-node-tqs87                    3/3     Running   0          20m
    ```

## Installation and Configuration on the OpenShift Platform{#section14977616204416}

For the OpenShift platform, run the following commands to create the  **SecurityContextConstraints**  resource.

1.  Run the following command to edit the  **helm\_scc.yaml**  file.

    ```
    vi helm_scc.yaml
    ```

2.  Modify the  **helm\_scc.yaml**  file. In the following command output,  **huawei-csi**  indicates the created namespace. Replace it based on the actual situation.

    ```yaml
    apiVersion: security.openshift.io/v1
    kind: SecurityContextConstraints
    metadata:
      name: helm-scc
    allowHostDirVolumePlugin: true
    allowHostIPC: true
    allowHostNetwork: true
    allowHostPID: true
    allowHostPorts: true
    allowPrivilegeEscalation: true
    allowPrivilegedContainer: true
    
    defaultAddCapabilities:
    - SYS_ADMIN
    runAsUser:
      type: RunAsAny
    seLinuxContext:
      type: RunAsAny
    fsGroup:
      type: RunAsAny
    users:
    - system:serviceaccount:huawei-csi:huawei-csi-controller
    - system:serviceaccount:huawei-csi:huawei-csi-node
    ```

3.  Run the following command to create a  **SecurityContextConstraints**  file.

    ```
    oc create -f helm_scc.yaml
    ```

## Installation and Configuration on the Tanzu Platform{#section9291624164514}

On the Tanzu platform, run the following command to configure the  **kubelet**  installation directory.

1.  Go to the  **helm/esdk**  directory in the installation package, run the following command to open the configuration file, modify the file, and save the file. For details about the installation package directory, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    vi values.yaml
    ```

2.  Modify the  **kubeletConfigDir**  parameter as follows:

    ```yaml
    # Specify kubelet config dir path.
    # kubernetes and openshift is usually /var/lib/kubelet
    # Tanzu is usually /var/vcap/data/kubelet
    # CCE is usually /mnt/paas/kubernetes/kubelet
    kubeletConfigDir: /var/vcap/data/kubelet
    ```

For TKGI 1.16 or earlier of the Tanzu platform, run the following commands to configure the RBAC permission.

1.  Run the following command to create a file named  **rbac.yaml**.

    ```
    vi rbac.yaml
    ```

2.  Copy the following content to the  **rbac.yaml**  file, save the file, and exit.

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

3.  Run the following command to create the RBAC permission.

    ```
    kubectl create -f rbac.yaml
    ```

