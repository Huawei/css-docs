---
title: "使用oceanctl工具管理后端时调用webhook失败"
linkTitle: "使用oceanctl工具管理后端时调用webhook失败"
description: 
weight: 1
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

当webhook的配置发生改变后，例如修改webhookPort参数值后，此时使用oceanctl工具对后端进行管理时调用webhook报错，如下：

![](/css-docs/figures/zh-cn_image_0000002084763809.png)

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

当webhook的配置发生改变后，导致validatingwebhookconfiguration资源失效。

## 解决措施或规避方法{#section1730118471221}

1.  执行以下命令，删除validatingwebhookconfiguration资源。

    ```
    kubectl delete validatingwebhookconfiguration storage-backend-controller.xuanwu.huawei.io
    ```

2.  执行以下命令，重启CSI Controller，请通过“**--replicas=\***”恢复CSI Controller的副本数，下例为恢复至1个，请根据实际情况修改。

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=0 
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=1
    ```

3.  执行以下命令，检查CSI Controller是否成功拉起。

    ```
    kubectl get pod -n huawei-csi
    ```

    命令结果示例如下，Pod状态为“Running“说明Controller成功拉起。

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-58d5b6b978-s2dsq   9/9     Running   0          19s
    huawei-csi-node-dt6nd                    3/3     Running   0          77m
    ```

