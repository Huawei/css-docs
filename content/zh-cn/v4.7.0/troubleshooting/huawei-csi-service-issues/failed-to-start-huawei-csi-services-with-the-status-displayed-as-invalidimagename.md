---
title: "启动huawei-csi服务时，服务启动异常， 状态显示InvalidImageName"
linkTitle: "启动huawei-csi服务时，服务启动异常， 状态显示InvalidImageName"
description: 
weight: 3
---

## 现象描述{#zh-cn_topic_0000001205368783_section1566717121452}

启动huawei-csi时，无法启动huawei-csi服务（huawei-csi-controller服务或者huawei-csi-node服务），使用kubectl get pod -A | grep huawei命令查看，显示状态为InvalidImageName

```
kubectl get pod -A | grep huawei
```

命令结果示例如下：

```
huawei-csi     huawei-csi-controller-fd5f97768-qlldc     6/9     InvalidImageName     0          16s
huawei-csi     huawei-csi-node-25txd                     2/3     InvalidImageName     0          15s
```

## 根因分析{#zh-cn_topic_0000001205368783_section1425013451056}

controller和node的yaml配置文件中，配置Huawei CSI的镜像版本号错误。例如：

```
        ...
        - name: huawei-csi-driver
          image: huawei-csi:4.7.0
        ...
```

## 解决措施或规避方法{#zh-cn_topic_0000001205368783_section350653016492}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，修改huawei-csi-node服务的配置文件。按**I**或**Insert**进入编辑状态，修改相关参数。修改完成后，按**Esc**，并输入  **:wq!**，保存修改。

    ```
    kubectl edit daemonset huawei-csi-node -o yaml -n=huawei-csi
    ```

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >-   示例yaml文件中huawei-csi-driver的参数image配置项，修改华为CSI镜像huawei-csi:4.7.0。
    >    ```
    >    containers:
    >      ...
    >      - name: huawei-csi-driver
    >        image: huawei-csi:4.7.0
    >    ```

3.  执行以下命令，修改huawei-csi-controller服务的配置文件。按**I**或**Insert**进入编辑状态，修改相关参数。修改完成后，按**Esc**，并输入  **:wq!**  ，保存修改。

    ```
    kubectl edit deployment huawei-csi-controller -o yaml -n=huawei-csi
    ```

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >-   示例yaml文件中huawei-csi-driver的参数image配置项，修改华为CSI镜像huawei-csi:4.7.0。
    >    ```
    >    containers:
    >      ...
    >      - name: huawei-csi-driver
    >        image: huawei-csi:4.7.0
    >    ```

4.  等待huawei-csi-node和huawei-csi-controller服务启动。
5.  执行以下命令，查看huawei csi服务是否启动。

    ```
    kubectl get pod -A  | grep huawei
    ```

    命令结果示例如下，Pod状态为“Running“说明服务启动成功。

    ```
    huawei-csi   huawei-csi-controller-58799449cf-zvhmv   9/9     Running       0          2m29s
    huawei-csi   huawei-csi-node-7fxh6                    3/3     Running       0          12m
    ```

