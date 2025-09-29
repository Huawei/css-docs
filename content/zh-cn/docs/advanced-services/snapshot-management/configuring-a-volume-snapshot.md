---
title: "配置卷快照"
linkTitle: "配置卷快照"
description: 
weight: 1
---

## 创建卷快照类{#section1925544124114}

[卷快照类（VolumeSnapshotClass）](https://kubernetes.io/docs/concepts/storage/volume-snapshot-classes/)提供了一种在配置VolumeSnapshot时描述存储“类”的方法。每个VolumeSnapshotClass都包含“driver”、“deletionPolicy” 和“parameters”字段， 在需要动态配置属于该类的VolumeSnapshot时使用。

VolumeSnapshotClass对象的名称很重要，是用户可以请求特定类的方式。 管理员在首次创建VolumeSnapshotClass对象时设置类的名称和其他参数， 对象一旦创建就无法更新。

华为CSI使用的VolumeSnapshotClass示例如下：

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshotClass
metadata:
  name: mysnapclass
driver: csi.huawei.com
deletionPolicy: Delete
```

实际参数可以参考[表1](#zh-cn_topic_0254162578_table189495491346)中的说明修改。由于当前华为CSI还不支持在VolumeSnapshotClass中设置自定义参数（parameters），因此建议只创建一个VolumeSnapshotClass，供所有快照使用。

**表 1**  VolumeSnapshotClass参数说明

<a name="zh-cn_topic_0254162578_table189495491346"></a>
<table><thead align="left"><tr id="zh-cn_topic_0254162578_row694915491241"><th class="cellrowborder" valign="top" width="17.91%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0254162578_p1094915491049"><a name="zh-cn_topic_0254162578_p1094915491049"></a><a name="zh-cn_topic_0254162578_p1094915491049"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="26.99%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0254162578_p14949149841"><a name="zh-cn_topic_0254162578_p14949149841"></a><a name="zh-cn_topic_0254162578_p14949149841"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="55.1%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0254162578_p1894916491142"><a name="zh-cn_topic_0254162578_p1894916491142"></a><a name="zh-cn_topic_0254162578_p1894916491142"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0254162578_row694916498411"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162578_p179494491042"><a name="zh-cn_topic_0254162578_p179494491042"></a><a name="zh-cn_topic_0254162578_p179494491042"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0254162578_p594918493417"><a name="zh-cn_topic_0254162578_p594918493417"></a><a name="zh-cn_topic_0254162578_p594918493417"></a>自定义的VolumeSnapshotClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0254162578_p179301591191"><a name="zh-cn_topic_0254162578_p179301591191"></a><a name="zh-cn_topic_0254162578_p179301591191"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字字符开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0254162578_row17949349643"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162578_p294913495410"><a name="zh-cn_topic_0254162578_p294913495410"></a><a name="zh-cn_topic_0254162578_p294913495410"></a>driver</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0254162578_p189491549542"><a name="zh-cn_topic_0254162578_p189491549542"></a><a name="zh-cn_topic_0254162578_p189491549542"></a>driver标识。必填参数。</p>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0254162578_p119491249043"><a name="zh-cn_topic_0254162578_p119491249043"></a><a name="zh-cn_topic_0254162578_p119491249043"></a>该字段需要指定为安装华为CSI时设置的驱动名。默认的驱动名为“csi.huawei.com”。</p>
</td>
</tr>
<tr id="zh-cn_topic_0254162578_row19949449547"><td class="cellrowborder" valign="top" width="17.91%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162578_p5949749144"><a name="zh-cn_topic_0254162578_p5949749144"></a><a name="zh-cn_topic_0254162578_p5949749144"></a>deletionPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="26.99%" headers="mcps1.2.4.1.2 "><p id="p19594192418394"><a name="p19594192418394"></a><a name="p19594192418394"></a>快照删除策略。必填参数。可选值为：</p>
<a name="ul1034113525514"></a><a name="ul1034113525514"></a><ul id="ul1034113525514"><li>Delete</li><li>Retain</li></ul>
</td>
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><a name="ul925601066"></a><a name="ul925601066"></a><ul id="ul925601066"><li><span>如果删除策略是 </span>Delete<span>，那么存储设备上的快照会和VolumeSnapshotContent对象一起删除</span>。</li><li><span>如果删除策略是</span>Retain<span>，那么存储设备上的快照和VolumeSnapshotContent对象都会被保留。</span></li></ul>
</td>
</tr>
</tbody>
</table>

## 操作步骤{#section133215312424}

1.  执行以下命令，使用已经创建的VolumeSnapshotClass配置文件创建VolumeSnapshotClass。

    ```
    kubectl create -f mysnapclass.yaml
    ```

2.  执行以下命令，查看已创建的VolumeSnapshotClass信息。

    ```
    kubectl get volumesnapshotclass
    ```

    命令结果示例如下：

    ```
    NAME          DRIVER           DELETIONPOLICY   AGE
    mysnapclass   csi.huawei.com   Delete           25s
    ```

## 创建卷快照{#section11071242458}

VolumeSnapshot可以通过两种方式进行制备：[预制备或动态制备](https://kubernetes.io/zh-cn/docs/concepts/storage/volume-snapshots/#provisioning-volume-snapshot)。华为CSI当前仅支持动态制备。本章节将说明如何使用华为CSI动态制备VolumeSnapshot。VolumeSnapshot的配置文件示例如下：

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

实际参数可以参考[表2](#zh-cn_topic_0254162579_table14111735169)中的说明修改。

**表 2**  VolumeSnapshot参数说明

<a name="zh-cn_topic_0254162579_table14111735169"></a>
<table><thead align="left"><tr id="zh-cn_topic_0254162579_row74136313166"><th class="cellrowborder" valign="top" width="31.5%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0254162579_p741313171613"><a name="zh-cn_topic_0254162579_p741313171613"></a><a name="zh-cn_topic_0254162579_p741313171613"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="26.479999999999997%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0254162579_p6416123101617"><a name="zh-cn_topic_0254162579_p6416123101617"></a><a name="zh-cn_topic_0254162579_p6416123101617"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="42.02%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0254162579_p82453211342"><a name="zh-cn_topic_0254162579_p82453211342"></a><a name="zh-cn_topic_0254162579_p82453211342"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0254162579_row1328513213318"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162579_p1428717212036"><a name="zh-cn_topic_0254162579_p1428717212036"></a><a name="zh-cn_topic_0254162579_p1428717212036"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0254162579_p19287172112316"><a name="zh-cn_topic_0254162579_p19287172112316"></a><a name="zh-cn_topic_0254162579_p19287172112316"></a>自定义的<span>VolumeSnapshot</span>对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0254162579_p179301591191"><a name="zh-cn_topic_0254162579_p179301591191"></a><a name="zh-cn_topic_0254162579_p179301591191"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字字符开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0254162579_row94166341618"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162579_p1241612311619"><a name="zh-cn_topic_0254162579_p1241612311619"></a><a name="zh-cn_topic_0254162579_p1241612311619"></a>spec.volumeSnapshotClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0254162579_p198887586399"><a name="zh-cn_topic_0254162579_p198887586399"></a><a name="zh-cn_topic_0254162579_p198887586399"></a>VolumeSnapshotClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0254162579_p17304111921116"><a name="zh-cn_topic_0254162579_p17304111921116"></a><a name="zh-cn_topic_0254162579_p17304111921116"></a>--</p>
</td>
</tr>
<tr id="zh-cn_topic_0254162579_row1241623171612"><td class="cellrowborder" valign="top" width="31.5%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0254162579_p11416143151617"><a name="zh-cn_topic_0254162579_p11416143151617"></a><a name="zh-cn_topic_0254162579_p11416143151617"></a>spec.source.persistentVolumeClaimName</p>
</td>
<td class="cellrowborder" valign="top" width="26.479999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0254162579_p174161381612"><a name="zh-cn_topic_0254162579_p174161381612"></a><a name="zh-cn_topic_0254162579_p174161381612"></a>源PVC对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="42.02%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0254162579_p1324203293410"><a name="zh-cn_topic_0254162579_p1324203293410"></a><a name="zh-cn_topic_0254162579_p1324203293410"></a>快照源PVC对应的名称</p>
</td>
</tr>
</tbody>
</table>

## 操作步骤{#section17556404720}

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

