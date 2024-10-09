---
title: "配置VolumeSnapshotClass"
linkTitle: "配置VolumeSnapshotClass"
description: 
weight: 2
---

[卷快照类（VolumeSnapshotClass）](https://kubernetes.io/docs/concepts/storage/volume-snapshot-classes/)提供了一种在配置VolumeSnapshot时描述存储“类”的方法。每个VolumeSnapshotClass都包含“driver”、“deletionPolicy” 和“parameters”字段， 在需要动态配置属于该类的VolumeSnapshot时使用。

VolumeSnapshotClass对象的名称很重要，是用户可以请求特定类的方式。 管理员在首次创建VolumeSnapshotClass对象时设置类的名称和其他参数， 对象一旦创建就无法更新。

华为CSI使用的VolumeSnapshotClass示例如下：

-   如果您的环境中api-versions支持v1，请使用以下示例：

    ```yaml
    apiVersion: snapshot.storage.k8s.io/v1
    kind: VolumeSnapshotClass
    metadata:
      name: mysnapclass
    driver: csi.huawei.com
    deletionPolicy: Delete
    ```

-   如果您的环境中api-versions支持v1beta1，请使用以下示例：

    ```yaml
    apiVersion: snapshot.storage.k8s.io/v1beta1
    kind: VolumeSnapshotClass
    metadata:
      name: mysnapclass
    driver: csi.huawei.com
    deletionPolicy: Delete
    ```

-   如果您的环境中api-versions同时支持v1和v1beta1，我们推荐您使用v1版本。

实际参数可以参考[表 VolumeSnapshotClass参数说明](#zh-cn_topic_0254162578_table189495491346)中的说明修改。由于当前华为CSI还不支持在VolumeSnapshotClass中设置自定义参数（parameters），因此建议只创建一个VolumeSnapshotClass，供所有快照使用。

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
<td class="cellrowborder" valign="top" width="55.1%" headers="mcps1.2.4.1.3 "><a name="ul925601066"></a><a name="ul925601066"></a><ul id="ul925601066"><li><span>如果删除策略是 </span>Delete<span>，那么存储设备上的快照会和VolumeSnapshotContent对象一起删除</span></li><li><span>如果删除策略是</span>Retain<span>，那么存储设备上的快照和VolumeSnapshotContent对象都会被保留。</span></li></ul>
</td>
</tr>
</tbody>
</table>

## 前提条件{#section549623219322}

华为CSI支持快照且运行所依赖的卷快照组件CRD已经安装。具体CRD信息请参考[检查卷快照依赖组件](/docs/安装部署/安装前准备/检查卷快照依赖组件)章节说明，支持创建VolumeSnapshot的Kubernetes版本请参考[表 Kubernetes版本与支持的特性](/docs/兼容性和特性/Kubernetes特性矩阵#table134589135522)。

## 操作步骤{#section187667882011}

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

