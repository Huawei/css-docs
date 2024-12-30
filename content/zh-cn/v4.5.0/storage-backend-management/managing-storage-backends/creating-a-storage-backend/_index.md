---
title: "创建存储后端"
linkTitle: "创建存储后端"
description: 
weight: 1
---

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>1.  使用oceanctl创建存储后端时，输入的账号和秘钥信息保存在[Secret](https://kubernetes.io/zh-cn/docs/concepts/configuration/secret/)对象中，建议客户容器平台根据供应商或者K8s社区的建议自行对Secret进行加密。K8s社区对Secret加密可参考[启用静态加密](https://kubernetes.io/zh-cn/docs/tasks/administer-cluster/encrypt-data/)。
>2.  通过json文件创建后端时，旧版本的backend名称中可能存在大写字母或"\_"字符。如果出现这种情况，旧的名称将会被重映射为一个新的名称，映射过程自动发生，不会影响原有功能。例如“ABC\_123”将会被映射为“abc-123-fd68e”，具体映射规则如下：
>    -   大写字母转换成小写字母。
>    -   "\_"字符转换成“-”字符。
>    -   末尾追加5位Hash码。
>3.  当存储后端对接租户时，在存储后端创建完成后，不允许修改租户名称。

## 操作步骤{#section193534374443}

1.  参考[典型场景存储后端配置文件示例](/v4.5.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/examples-of-storage-backend-configuration-files-in-typical-scenarios)章节准备后端配置文件，如backend.yaml，若需创建多个后端，请使用'"---"分隔。

    ```
    storage: "oceanstor-san"
    name: "backend-1"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.157:8088"
    pools:
      - "StoragePool001"
    parameters:
      protocol: "roce"
      portals:
        - "10.10.30.20"
        - "10.10.30.21"
    maxClientThreads: "30"
    ---
    storage: "oceanstor-san"
    name: "backend-2"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.158:8088"
    pools:
      - "StoragePool001"
    parameters:
      protocol: "roce"
      portals:
        - "10.10.30.20"
        - "10.10.30.21"
    maxClientThreads: "30"
    ```

2.  执行以下命令创建存储后端。

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml
    ```

    命令结果示例如下：

    ```
    NUMBER  CONFIGURED    NAME        STORAGE              URLS                
    1       false         backend-1   oceanstor-san        https://192.168.129.157:8088 
    2       false         backend-2   oceanstor-san        https://192.168.129.158:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

3.  输入待创建后端序号，并输入账号密码。

    ```
    Please enter the backend number to configure (Enter 'exit' to exit):1
    Please enter this backend user name:admin
    Please enter this backend password:
    
    Backend backend-1 is configured
    NUMBER  CONFIGURED    NAME         STORAGE              URLS               
    1       true          backend-1    oceanstor-san        https://192.168.129.157:8088 
    2       false         backend-2    oceanstor-san        https://192.168.129.158:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

4.  检查存储后端创建结果。

    ```
    oceanctl get backend
    ```

    命令结果示例如下，后端状态为“Bound“则创建成功。

    ```
    NAMESPACE     NAME         PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-1    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    huawei-csi    backend-2    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.158:8088   
    ```



