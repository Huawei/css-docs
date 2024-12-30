---
title: "Manually Installing Huawei CSI"
linkTitle: "Manually Installing Huawei CSI"
description: 
weight: 2
---

This section describes how to manually install Huawei CSI.

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>Currently, only the Kubernetes platform supports manual installation of Huawei CSI.

## Procedure{#section113761618183018}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the cluster through the management IP address.
2.  Copy the  **manual**  directory in the Kubernetes CSI component package to any directory on the master node.
3.  Run the following command to create a namespace.

    ```
    kubectl create ns huawei-csi
    ```

4.  Go to the  **manual/esdk**  working directory. For details about the path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    cd manual/esdk
    ```

5.  Run the following command to update the storage backend CRD.

    ```
    kubectl apply -f ./crds/backend/
    ```

6.  \(Optional\) Check snapshot-dependent components by following the instructions provided in  [Checking Volume Snapshot-Dependent Components](/docs/installation-and-deployment/installation-preparations/checking-volume-snapshot-dependent-components). After confirming that the components are correct, run the following command to update the snapshot CRD. If the Kubernetes version is earlier than v1.17, skip this step.

    ```
    kubectl apply -f ./crds/snapshot-crds/ --validate=false
    ```

7.  \(Optional\) Run the following command to install CSIDriver. If the CSIDriver feature is not used, you can skip this step. For details, see the  [CSIDriver](https://kubernetes-csi.github.io/docs/csi-driver-object.html)  feature.

    ```
    kubectl apply -f ./deploy/csidriver.yaml 
    ```

8.  Run the following command to install the huawei-csi-controller service.

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >If the Kubernetes version is earlier than v1.17, modify the  _./deploy/huawei-csi-controller.yaml_  file as follows:
    >-   If the Kubernetes version is earlier than v1.17, the snapshot feature is not supported. In this case, delete the snapshot-related container configurations items  **csi-snapshotter**  and  **snapshot-controller**.
    >-   If the Kubernetes version is earlier than v1.17, the csi-provisioner sidecar image provided by the Kubernetes community does not support the  **--leader-election**  parameter. Therefore, the  **leader-election**  parameter of the csi-provisioner container is deleted and only single-copy deployment is supported.
    >-   Modify the dependent image version based on the version requirements in  [Checking the Images on Which CSI Depends](/docs/installation-and-deployment/installation-preparations/checking-the-images-on-which-csi-depends).

    ```
    kubectl apply -f ./deploy/huawei-csi-controller.yaml
    ```

9.  Run the following command to install the huawei-csi-node service.

    ```
    kubectl apply -f ./deploy/huawei-csi-node.yaml 
    ```

10. Run the following command to check whether the services are started.

    ```
    kubectl get pod -n huawei-csi
    ```

    The following is an example of the command output. If the Pod status is  **Running**, the installation is successful.

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-68745d489c-v5xkj   9/9     Running   0          13m
    huawei-csi-node-4hbqp                    3/3     Running   0          13m
    huawei-csi-node-f7dkf                    3/3     Running   0          13m
    huawei-csi-node-xrntc                    3/3     Running   0          13m
    ```

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>In the multi-copy controller deployment scenario, you can modify the  **spec.replica**  field of the Deployment resource in the  _./deploy/huawei-csi-controller.yaml_  file to specify the number of copies. After the modification, run the following command for the modification to take effect.
>```
>kubectl apply -f ./deploy/huawei-csi-controller.yaml
>```

