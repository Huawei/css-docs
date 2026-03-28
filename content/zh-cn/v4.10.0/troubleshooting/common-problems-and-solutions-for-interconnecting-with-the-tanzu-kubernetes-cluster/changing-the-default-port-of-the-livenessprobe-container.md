---
title: "修改livenessprobe容器的默认端口"
linkTitle: "修改livenessprobe容器的默认端口"
description: 
weight: 3
---

## 现象描述{#zh-cn_topic_0000001279996521_section1566717121452}

huawei-csi-controller组件中livenessprobe容器一直重启。

## 根因分析{#zh-cn_topic_0000001279996521_section1425013451056}

huawei-csi-controller的livenessprobe容器的默认端口（9808）与已有的Tanzu的vSphere CSI端口冲突。

## 解决措施或规避方法{#zh-cn_topic_0000001279996521_section164471213145410}

将livenessprobe容器的默认端口修改为未占用端口。

1.  进入“helm/esdk”目录，执行**vi values.yaml**命令打开配置文件。

    ```
    vi values.yaml
    ```

2.  将controller.livenessProbePort默认值9808修改为其他未占用端口，例如改为9809。

    ```yaml
    controller:
      livenessProbePort: 9809
    ```

3.  使用Helm更新华为CSI，具体信息请参考[使用Helm升级](/docs/installation-and-deployment/csi/upgrade/upgrade-using-helm)。

