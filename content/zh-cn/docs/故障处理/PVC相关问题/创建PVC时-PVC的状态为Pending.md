---
title: "创建PVC时， PVC的状态为Pending"
linkTitle: "创建PVC时， PVC的状态为Pending"
description: 
weight: 1
---

## 现象描述{#zh-cn_topic_0000001207958677_section1566717121452}

执行完成PVC的创建操作，一段时间后，PVC的状态仍然处于Pending。

## 根因分析{#zh-cn_topic_0000001207958677_section1425013451056}

原因1：由于没有提前创建指定名称的StorageClass，导致Kubernetes在创建PVC时无法找到指定StorageClass名称。

原因2：由于存储池能力和StorageClass能力不匹配，导致huawei-csi选择存储池失败。

原因3：由于存储RESTful接口执行返回具体错误码（例如：50331651），导致huawei-csi在执行创建PVC时失败。

原因4：由于存储在huawei-csi设定的超时时间内没有返回，huawei-csi向Kubernetes返回超时错误。

原因5：其他原因。

## 解决措施或规避方法{#zh-cn_topic_0000001207958677_section350653016492}

创建PVC时，如果PVC处于Pending状态，需要根据以下不同的原因采取不同的解决措施。

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，查看PVC的详细信息。

    ```
    kubectl describe pvc mypvc
    ```

3.  根据PVC详细信息中Events信息，执行相应操作。
    -   如果由原因1导致PVC处于Pending状态，执行以下步骤。

        ```yaml
        Events:
          Type     Reason              Age                  From                         Message
          ----     ------              ----                 ----                         -------
          Warning  ProvisioningFailed  0s (x15 over 3m24s)  persistentvolume-controller  storageclass.storage.k8s.io "mysc" not found
        ```

        1.  删除PVC。
        2.  创建StorageClass，可参考[动态卷供应典型场景StorageClass配置示例](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应典型场景StorageClass配置示例)。
        3.  创建新的PVC，可参考[动态卷供应PVC参数说明](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应PVC参数说明)。

    -   如果由原因2导致PVC处于Pending状态，执行以下步骤。

        ```
        Events:
          Type     Reason                Age                From                                                                                       Message
          ----     ------                ----               ----                                                                                       -------
          Normal   Provisioning          63s (x3 over 64s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  External provisioner is provisioning volume for claim "default/mypvc"
          Warning  ProvisioningFailed    63s (x3 over 64s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  failed to provision volume with StorageClass "mysc": rpc error: code = Internal desc = failed to select pool, the capability filter failed, error: failed to select pool, the final filter field: replication, parameters map[allocType:thin replication:True size:1099511627776 volumeType:lun]. please check your storage class
        ```

        1.  删除PVC。
        2.  删除StorageClass。
        3.  根据Events信息修改StorageClass.yaml文件。
        4.  创建StorageClass，详细请参考[动态卷供应典型场景StorageClass配置示例](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应典型场景StorageClass配置示例)。
        5.  创建新的PVC，详情请参考[动态卷供应PVC参数说明](/docs/使用华为CSI/PVC管理/创建PVC/动态卷供应/动态卷供应PVC参数说明)。

    -   如果由原因3导致PVC处于Pending状态，请联系华为工程师处理。

        ```
        Events:
          Type     Reason                Age                From                                                                                       Message
          ----     ------                ----               ----                                                                                       -------
          Normal   Provisioning          63s (x4 over 68s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  External provisioner is provisioning volume for claim "default/mypvc"
          Warning  ProvisioningFailed    62s (x4 over 68s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  failed to provision volume with StorageClass "mysc": rpc error: code = Internal desc = Create volume map[ALLOCTYPE:1 CAPACITY:20 DESCRIPTION:Created from Kubernetes CSI NAME:pvc-63ebfda5-4cf0-458e-83bd-ecc PARENTID:0] error: 50331651
        ```

    -   如果由原因4导致PVC处于Pending状态，执行以下步骤。

        ```
        Events:
          Type     Reason                Age                From                                                                                       Message
          ----     ------                ----               ----                                                                                       -------
          Normal   Provisioning          63s (x3 over 52s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  External provisioner is provisioning volume for claim "default/mypvc"
          Warning  ProvisioningFailed    63s (x3 over 52s)  csi.huawei.com_huawei-csi-controller-b59577886-qqzm8_58533e4a-884c-4c7f-92c3-6e8a7b327515  failed to provision volume with StorageClass "mysc": rpc error: code = Internal desc = context deadline exceeded (Client.Timeout exceeded while awaiting headers)
        ```

        1.  请先等待10分钟， 参考本章节再次检查PVC详细信息
        2.  如果还处于Pending状态，请联系华为工程师处理。

    -   如果由原因5导致PVC处于Pending状态，请联系华为工程师处理。

