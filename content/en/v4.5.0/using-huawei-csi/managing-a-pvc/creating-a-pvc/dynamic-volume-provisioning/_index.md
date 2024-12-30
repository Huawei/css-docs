---
title: "Dynamic Volume Provisioning"
linkTitle: "Dynamic Volume Provisioning"
description: 
weight: 1
---

Dynamic volume provisioning allows storage volumes to be created on demand. Dynamic volume provisioning depends on the StorageClass objects. The cluster administrator can define multiple StorageClass objects as required and specify a StorageClass that meets service requirements when declaring a PV or PVC. When applying for resources from Huawei storage devices, Huawei CSI creates storage resources that meet service requirements based on the preset StorageClass.

To implement dynamic volume provisioning, perform the following steps:

-   Configuring a StorageClass
-   Configuring a PVC

## Configuring a StorageClass{#section176901147144516}

1.  Create a StorageClass configuration file, for example,  **mysc.yaml**, based on service requirements by referring to  [StorageClass Configuration Examples in Typical Dynamic Volume Provisioning Scenarios](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/storageclass-configuration-examples-in-typical-dynamic-volume-provisioning-scenarios)  and  [StorageClass Parameters for Dynamic Volume Provisioning](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/storageclass-parameters-for-dynamic-volume-provisioning).
2.  Run the following command to create a StorageClass using the configuration file.

    ```
    kubectl apply -f mysc.yaml
    ```

3.  Run the following command to view the information about the created StorageClass.

    ```
    kubectl get sc mysc
    ```

    The following is an example of the command output.

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           true                   8s
    ```

## Configuring a PVC{#section17522101915500}

1.  Based on service requirements, modify specific parameters by referring to the description in this section and the PVC configuration file example to generate the PVC configuration file to be created, for example, the  **mypvc.yaml**  file in this example.

    ```yaml
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: mypvc
    spec:
      accessModes:
        - ReadWriteOnce
      volumeMode: Filesystem
      storageClassName: mysc
      resources:
        requests:
          storage: 100Gi
    ```

2.  Run the following command to create a PVC using the configuration file.

    ```
    kubectl create -f mypvc.yaml
    ```

3.  After a period of time, run the following command to view the information about the created PVC.

    ```
    kubectl get pvc mypvc
    ```

    The following is an example of the command output. If the PVC status is  **Bound**, the PVC has been created and can be used by a Pod.

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO            mysc           12s
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
    >-   After the PVC is created, if the PVC is in the  **Pending**  state after a long time \(for example, one minute\), refer to  [When a PVC Is Created, the PVC Is in the Pending State](/docs/troubleshooting/pvc-issues/when-a-pvc-is-created-the-pvc-is-in-the-pending-state).
    >-   You are advised to create or delete a maximum of 100 PVCs in a batch.

## Using a PVC{#section8172141413917}

After a PVC is created, you can use the PVC to create a Pod. The following is a simple example of using a PVC. In this example, the created Pod uses the newly created  _mypvc_.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers: 
      - image: nginx:alpine
        name: container-0 
        volumeMounts: 
        - mountPath: /tmp
          name: pvc-mypvc 
      restartPolicy: Always 
      volumes: 
      - name: pvc-mypvc 
        persistentVolumeClaim: 
          claimName:  mypvc  # name of PVC
```




