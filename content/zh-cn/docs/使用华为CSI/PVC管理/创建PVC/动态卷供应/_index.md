---
title: "动态卷供应"
linkTitle: "动态卷供应"
description: 
weight: 1
---

动态卷供应（Dynamic Volume Provisioning）允许按需创建存储卷。动态卷供应依赖StorageClass对象。 集群管理员可以根据需要定义多个StorageClass对象，在声明PV或者PVC时，指定满足业务要求的StorageClass。华为CSI在从华为存储设备上申请资源时，会根据StorageClass的预置定义，创建满足业务要求的存储资源。

为了完成动态卷供应，需要完成如下两步：

-   配置StorageClass
-   配置PVC

## 配置StorageClass{#section176901147144516}

1.  根据业务需要，参考[动态卷供应典型场景StorageClass配置示例](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应典型场景StorageClass配置示例)和[动态卷供应StorageClass参数说明](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应StorageClass参数说明)，创建StorageClass配置文件，如本例从的mysc.yaml文件。
2.  执行命令，使用配置文件创建StorageClass。

    ```
    kubectl apply -f mysc.yaml
    ```

3.  执行命令，查看已创建的StorageClass信息。

    ```
    kubectl get sc mysc
    ```

    命令结果示例如下：

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           true                   8s
    ```

## 配置PVC{#section17522101915500}

1.  根据业务需要，参考本节描述和PVC配置文件示例，修改具体参数，生成本次需要创建的PVC配置文件，如本例中mypvc.yaml文件。

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

2.  执行命令，使用配置文件创建PVC。

    ```
    kubectl create -f mypvc.yaml
    ```

3.  等待一段时间后，执行以下命令，查看已经创建的PVC信息。

    ```
    kubectl get pvc mypvc
    ```

    命令结果示例如下，如果PVC的状态是“Bound”时，则说明该PVC已经创建成功，后续可以被Pod使用。

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO            mysc           12s
    ```

    >![](/public_sys-resources/zh/icon-notice.gif)  
    >-   完成创建PVC操作后，如果长时间后（如一分钟后）PVC的状态是Pending，请参考[创建PVC时， PVC的状态为Pending](/docs/故障处理/PVC相关问题/创建PVC时-PVC的状态为Pending)。
    >-   建议每批次最多批量创建/删除100个PVC。

## 使用PVC{#section8172141413917}

在完成PVC创建后，就可以使用PVC来创建Pod。如下示例是一个简单的使用PVC示例，在该示例中，创建的Pod使用了刚刚创建的 _mypvc_。

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




