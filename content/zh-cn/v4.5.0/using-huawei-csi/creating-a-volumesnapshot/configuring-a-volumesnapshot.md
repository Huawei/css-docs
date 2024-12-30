---
title: "配置VolumeSnapshot"
linkTitle: "配置VolumeSnapshot"
description: 
weight: 3
---

VolumeSnapshot可以通过两种方式进行制备：预制备或动态制备。华为CSI当前仅支持动态制备。本章节将说明如何使用华为CSI动态制备VolumeSnapshot。

VolumeSnapshot的配置文件示例如下：

-   如果您的环境中api-versions支持v1，请使用以下示例：

    ```yaml
    apiVersion: snapshot.storage.k8s.io/v1
    kind: VolumeSnapshot
    metadata:
      name: mysnapshot
    spec:
      volumeSnapshotClassName: mysnapclass
      source:
        persistentVolumeClaimName: mypvc
    ```

-   如果您的环境中api-versions支持v1beta1，请使用以下示例：

    ```yaml
    apiVersion: snapshot.storage.k8s.io/v1beta1
    kind: VolumeSnapshot
    metadata:
      name: mysnapshot
    spec:
      volumeSnapshotClassName: mysnapclass
      source:
        persistentVolumeClaimName: mypvc
    ```

-   VolumeSnapshot中api-versions信息，请和创建VolumeSnapshotClass使用的版本保持一致。

实际参数可以参考[表1](#zh-cn_topic_0254162579_table14111735169)中的说明修改。

**表 1**  VolumeSnapshot参数说明

<a name="zh-cn_topic_0254162579_table14111735169"></a>
<table><thead align="left"><tr id="zh-cn_topic_0254162579_row74136313166"><th class="cellrowborder" valign="top" width="31.75%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0254162579_p741313171613"><a name="zh-cn_topic_0254162579_p741313171613"></a><a name="zh-cn_topic_0254162579_p741313171613"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="26.229999999999997%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0254162579_p6416123101617"><a name="zh-cn_topic_0254162579_p6416123101617"></a><a name="zh-cn_topic_0254162579_p6416123101617"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="42.02%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0254162579_p82453211342"><a name="zh-cn_topic_0254162579_p82453211342"></a><a name="zh-cn_topic_0254162579_p82453211342"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0254162579_row1328513213318"><td class="cellrowborder" valign="top" width="31.75%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162579_p1428717212036"><a name="zh-cn_topic_0254162579_p1428717212036"></a><a name="zh-cn_topic_0254162579_p1428717212036"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.229999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0254162579_p19287172112316"><a name="zh-cn_topic_0254162579_p19287172112316"></a><a name="zh-cn_topic_0254162579_p19287172112316"></a>自定义的<span>VolumeSnapshot</span>对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0254162579_p179301591191"><a name="zh-cn_topic_0254162579_p179301591191"></a><a name="zh-cn_topic_0254162579_p179301591191"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字字符开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0254162579_row94166341618"><td class="cellrowborder" valign="top" width="31.75%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162579_p1241612311619"><a name="zh-cn_topic_0254162579_p1241612311619"></a><a name="zh-cn_topic_0254162579_p1241612311619"></a>spec.volumeSnapshotClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26.229999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0254162579_p198887586399"><a name="zh-cn_topic_0254162579_p198887586399"></a><a name="zh-cn_topic_0254162579_p198887586399"></a>VolumeSnapshotClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0254162579_p17304111921116"><a name="zh-cn_topic_0254162579_p17304111921116"></a><a name="zh-cn_topic_0254162579_p17304111921116"></a>--</p>
</td>
</tr>
<tr id="zh-cn_topic_0254162579_row1241623171612"><td class="cellrowborder" valign="top" width="31.75%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162579_p11416143151617"><a name="zh-cn_topic_0254162579_p11416143151617"></a><a name="zh-cn_topic_0254162579_p11416143151617"></a>spec.source.persistentVolumeClaimName</p>
</td>
<td class="cellrowborder" valign="top" width="26.229999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0254162579_p174161381612"><a name="zh-cn_topic_0254162579_p174161381612"></a><a name="zh-cn_topic_0254162579_p174161381612"></a>源PVC对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0254162579_p1324203293410"><a name="zh-cn_topic_0254162579_p1324203293410"></a><a name="zh-cn_topic_0254162579_p1324203293410"></a>快照源PVC对应的名称</p>
</td>
</tr>
</tbody>
</table>

## 前提条件{#section1236201420471}

-   源PVC存在，且PVC所在的backend存在支持创建VolumeSnapshot。支持创建VolumeSnapshot的存储请参考[表2](/v4.5.0/compatibility-and-features/compatibility-with-huawei-enterprise-storage#table14995183994515)和[表2](/v4.5.0/compatibility-and-features/compatibility-with-huawei-distributed-storage#table175022559255)，支持创建VolumeSnapshot的Kubernetes版本请参考[表1](/v4.5.0/compatibility-and-features/kubernetes-feature-matrix#table134589135522)。
-   华为CSI运行所依赖的卷快照组件CRD已经安装。具体信息请参考[检查卷快照依赖组件](/v4.5.0/installation-and-deployment/installation-preparations/checking-volume-snapshot-dependent-components)章节说明。
-   系统中已经存在使用华为CSI的VolumeSnapshotClass。

## 操作步骤{#section1678012285209}

1.  执行以下命令，使用已经创建的VolumeSnapshot配置文件创建VolumeSnapshot。

    ```
    kubectl create -f mysnapshot.yaml
    ```

2.  执行以下命令，查看已创建的VolumeSnapshot信息。

    ```
    kubectl get volumesnapshot
    ```

    命令结果示例如下：

    ```
    NAME         READYTOUSE   SOURCEPVC   SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS   SNAPSHOTCONTENT                                    CREATIONTIME   AGE
    mysnapshot   true         mypvc                               100Gi         mysnapclass     snapcontent-1009af0a-24c2-4435-861c-516224503f2d   <invalid>      78s
    ```

