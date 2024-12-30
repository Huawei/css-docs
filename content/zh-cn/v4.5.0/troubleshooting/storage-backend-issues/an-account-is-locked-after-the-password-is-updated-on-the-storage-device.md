---
title: "存储侧更新密码后账户被锁定"
linkTitle: "存储侧更新密码后账户被锁定"
description: 
weight: 3
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

用户在存储侧修改后端密码之后，该后端账号被锁定。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

CSI登录存储时使用存储后端配置的账户和密码，当存储侧修改了该账户密码之后，CSI登录失败后会重试。以OceanStor Dorado存储为例，默认的登录策略是密码校验失败3次后将会锁定账户，因此当CSI重试超过3次之后，该账户就会被锁定。

## 解决措施或规避方法{#section155945247573}

1.  如果后端配置的账户是admin，请执行以下命令，将huawei-csi-controller服务副本数置为0，如果使用的是非admin账户，忽略此步骤。

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=0
    ```

2.  使用admin账户登录存储，修改登录策略。以OceanStor Dorado存储为例，在DeviceManager管理界面，选择“设置 \> 用户与安全 \> 安全策略 \>登录策略 \>修改\>密码锁定”，取消密码锁定。
3.  如果如果后端配置的账户是admin，执行以下命令，通过“**--replicas=\***”恢复CSI Controller的副本数，下例为恢复至1个，请根据实际情况修改。如果使用的是非admin账户，忽略此步骤。

    ```
    kubectl scale deployment huawei-csi-controller -n huawei-csi --replicas=1
    ```

4.  使用oceanctl工具修改存储后端密码，修改后端密码请参考[更新存储后端](/v4.5.0/storage-backend-management/managing-storage-backends/updating-a-storage-backend)章节。
5.  使用admin账户登录存储，修改登录策略，以OceanStor Dorado存储为例，在DeviceManager管理界面，选择“设置 \> 用户与安全 \> 安全策略 \>登录策略 \>修改\>密码锁定”，恢复密码锁定。

