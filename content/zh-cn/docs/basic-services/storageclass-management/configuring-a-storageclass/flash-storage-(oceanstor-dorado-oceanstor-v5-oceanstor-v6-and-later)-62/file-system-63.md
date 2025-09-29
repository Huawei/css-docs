---
title: "文件系统"
linkTitle: "文件系统"
description: 
weight: 1
---

## 创建存储类{#section15343162123719}

1.  准备存储类配置文件，如本例中的mysc.yaml文件，存储类配置请参考下方示例文件。
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

## NFS协议配置示例{#section1053116812255}

容器使用NFS协议对接文件系统资源时，可以参考如下存储类配置示例。该示例中，NFS挂载时指定版本为4.1。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-nas-181
  pool: StoragePool001
  volumeType: fs
  allocType: thin
  authClient: "*"
mountOptions:
  - nfsvers=4.1 # NFS挂载时指定版本为4.1
```

## NFS+协议配置示例{#section420824715129}

容器使用NFS+协议对接文件系统资源时，可以参考如下存储类配置示例。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-nas-181
  pool: StoragePool001
  volumeType: fs
  allocType: thin
  authClient: "*"
```

## 双活文件系统配置示例{#section1132049113716}

容器使用NFS双活文件系统作为存储资源时，可以参考如下配置示例。该示例中，使用的后端是支持双活的后端，且配置“**hyperMetro**”参数为“true”。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-hypermetro-dorado-181
  pool: pool001
  volumeType: fs
  hyperMetro: "true" # 发放双活卷
  allocType: thin
  authClient: "*"
```

>![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
>-   发放NAS双活卷前，需要在两台存储设备之间配置双活关系，包含远端设备、双活域等，仅支持文件系统双活域工作模式为双活AA模式，配置操作请参考对应存储型号的产品文档。
>-   若存储发生故障，逻辑管理端口可能产生漂移，在漂移状态下删除NAS双活卷后，需手动清理对应的存储资源。

## 文件系统支持的存储类参数详细说明{#section1758842912252}

**表 1**  StorageClass配置参数说明

<a name="zh-cn_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="18.481557577536446%" id="mcps1.2.7.1.1"><p id="zh-cn_topic_0000001162111564_p875071122919"><a name="zh-cn_topic_0000001162111564_p875071122919"></a><a name="zh-cn_topic_0000001162111564_p875071122919"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="23.089717248801485%" id="mcps1.2.7.1.2"><p id="zh-cn_topic_0000001162111564_p17750131113295"><a name="zh-cn_topic_0000001162111564_p17750131113295"></a><a name="zh-cn_topic_0000001162111564_p17750131113295"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="6.692104490754329%" id="mcps1.2.7.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="8.609725075824283%" id="mcps1.2.7.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="7.35740142843166%" id="mcps1.2.7.1.5"><p id="p1113325565918"><a name="p1113325565918"></a><a name="p1113325565918"></a>纳管卷是否生效</p>
</th>
<th class="cellrowborder" valign="top" width="35.7694941786518%" id="mcps1.2.7.1.6"><p id="zh-cn_topic_0000001162111564_p075011113295"><a name="zh-cn_topic_0000001162111564_p075011113295"></a><a name="zh-cn_topic_0000001162111564_p075011113295"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p4750141111292"><a name="zh-cn_topic_0000001162111564_p4750141111292"></a><a name="zh-cn_topic_0000001162111564_p4750141111292"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="zh-cn_topic_0000001162111564_p475091120296"><a name="zh-cn_topic_0000001162111564_p475091120296"></a><a name="zh-cn_topic_0000001162111564_p475091120296"></a>自定义的StorageClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p16133655135913"><a name="p16133655135913"></a><a name="p16133655135913"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="zh-cn_topic_0000001162111564_p861713973915"><a name="zh-cn_topic_0000001162111564_p861713973915"></a><a name="zh-cn_topic_0000001162111564_p861713973915"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p8750161119299"><a name="zh-cn_topic_0000001162111564_p8750161119299"></a><a name="zh-cn_topic_0000001162111564_p8750161119299"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="zh-cn_topic_0000001162111564_p15750201119295"><a name="zh-cn_topic_0000001162111564_p15750201119295"></a><a name="zh-cn_topic_0000001162111564_p15750201119295"></a>制备器名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p0133955185920"><a name="p0133955185920"></a><a name="p0133955185920"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>该字段需要指定为安装华为CSI时设置的驱动名称。</p>
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>取值和values.yaml文件中driverName一致。</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p119108535312"><a name="p119108535312"></a><a name="p119108535312"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p16910135393118"><a name="p16910135393118"></a><a name="p16910135393118"></a>回收策略。支持如下类型：</p>
<a name="ul5209917195517"></a><a name="ul5209917195517"></a><ul id="ul5209917195517"><li>Delete：自动回收资源。</li><li>Retain：<span>手动回收资源</span>。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p11332055125915"><a name="p11332055125915"></a><a name="p11332055125915"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li>Delete：删除PV/PVC时会关联删除存储上的资源。</li><li>Retain：删除PV/PVC时不会删除存储上的资源。</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p192771821155012"><a name="p192771821155012"></a><a name="p192771821155012"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p8277132112501"><a name="p8277132112501"></a><a name="p8277132112501"></a>是否允许卷扩展。参数设置为true 时，使用该StorageClass的PV可以进行扩容操作。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1613325519595"><a name="p1613325519595"></a><a name="p1613325519595"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p13923171118495"><a name="p13923171118495"></a><a name="p13923171118495"></a>此功能仅可用于扩容PV，不能用于缩容PV。</p>
</td>
</tr>
<tr id="row63343268297"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p13432132752911"><a name="p13432132752911"></a><a name="p13432132752911"></a>mountOptions</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p134321427192916"><a name="p134321427192916"></a><a name="p134321427192916"></a>挂载参数列表，可用于指定主机执行mount命令时-o选项的参数。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p2432227172910"><a name="p2432227172910"></a><a name="p2432227172910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p1432112762919"><a name="p1432112762919"></a><a name="p1432112762919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1613355555915"><a name="p1613355555915"></a><a name="p1613355555915"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p15432162772912"><a name="p15432162772912"></a><a name="p15432162772912"></a>常见的mountOptions参数参考<a href="#table65545557506">表2</a>。</p>
<p id="p104322027152920"><a name="p104322027152920"></a><a name="p104322027152920"></a>也可自行指定其他挂载参数。</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>待创建资源所在的后端名称。如果设置parameters.pool，则必须设置本字段。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p413315519590"><a name="p413315519590"></a><a name="p413315519590"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>如果不设置，华为CSI随机选择一个满足容量要求的后端创建资源。</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>建议指定后端，确保创建的资源在预期的后端上。</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p395711171674"><a name="p395711171674"></a><a name="p395711171674"></a>parameters.pool</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p119571517771"><a name="p119571517771"></a><a name="p119571517771"></a>待创建资源所在的存储资源池名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p43701077524"><a name="p43701077524"></a><a name="p43701077524"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p12398310135213"><a name="p12398310135213"></a><a name="p12398310135213"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p91331855155916"><a name="p91331855155916"></a><a name="p91331855155916"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p99571317978"><a name="p99571317978"></a><a name="p99571317978"></a>如果不设置，华为CSI会在所选后端上随机选择一个满足容量要求的存储池创建资源。建议指定存储池，确保创建的资源在预期的存储池上。</p>
</td>
</tr>
<tr id="row12968565337"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p19968166163320"><a name="p19968166163320"></a><a name="p19968166163320"></a>parameters.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p270mcpsimp"><a name="p270mcpsimp"></a><a name="p270mcpsimp"></a>指定动态卷供应创建的存储资源名称。</p>
<p id="p271mcpsimp"><a name="p271mcpsimp"></a><a name="p271mcpsimp"></a>支持配置占位符对存储资源名称进行自定义，支持的占位符如下：</p>
<a name="ul277mcpsimp"></a><a name="ul277mcpsimp"></a><ul id="ul277mcpsimp"><li>PVC命名空间：{{ .PVCNamespace }}</li><li>PVC名称：{{ .PVCName }}</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p49687693314"><a name="p49687693314"></a><a name="p49687693314"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p096819643312"><a name="p096819643312"></a><a name="p096819643312"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p0133205515597"><a name="p0133205515597"></a><a name="p0133205515597"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul165061538173414"></a><a name="ul165061538173414"></a><ul id="ul165061538173414"><li>支持配置字母、数字、"-"、"_"、"."，不能配置为空，且将占位符展开后的长度范围是1-255。</li><li>必须同时配置PVC命名空间和PVC名称。</li><li>为了避免资源名称重复，会将PVC UID作为唯一标识符默认添加到名称末尾。</li></ul>
<p id="p3486174714359"><a name="p3486174714359"></a><a name="p3486174714359"></a></p>
<p id="p292mcpsimp"><a name="p292mcpsimp"></a><a name="p292mcpsimp"></a>配置示例：</p>
<p id="p293mcpsimp"><a name="p293mcpsimp"></a><a name="p293mcpsimp"></a>PVC命名空间为："namespace"，PVC名称为："pvc-1"，PVC UID："c2fd3f46-bf17-4a7d-b88e-2e3232bae434"。</p>
<p id="p301mcpsimp"><a name="p301mcpsimp"></a><a name="p301mcpsimp"></a>volumeName配置为: "prefix-{{ .PVCNamespace }}_{{ .PVCName }}"。</p>
<p id="p302mcpsimp"><a name="p302mcpsimp"></a><a name="p302mcpsimp"></a>最终存储资源名称为："prefix-namespace_pvc-1-c2fd3f46bf174a7db88e2e3232bae434"。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p1775061119292"><a name="zh-cn_topic_0000001162111564_p1775061119292"></a><a name="zh-cn_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="zh-cn_topic_0000001162111564_p975011122920"><a name="zh-cn_topic_0000001162111564_p975011122920"></a><a name="zh-cn_topic_0000001162111564_p975011122920"></a>待创建卷类型。支持如下类型：</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li>lun：存储侧发放的资源是LUN。</li><li>fs：存储侧发放的资源是文件系统。</li><li>dtree：存储侧发放的资源是Dtree类型的卷</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1913415525920"><a name="p1913415525920"></a><a name="p1913415525920"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p159151023181412"><a name="p159151023181412"></a><a name="p159151023181412"></a>此处固定配置为fs。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p13750171110290"><a name="zh-cn_topic_0000001162111564_p13750171110290"></a><a name="zh-cn_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="zh-cn_topic_0000001162111564_p67501211102911"><a name="zh-cn_topic_0000001162111564_p67501211102911"></a><a name="zh-cn_topic_0000001162111564_p67501211102911"></a>待创建卷的分配类型。支持如下类型：</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li>thin：创建时不会分配所有需要的空间，而是根据使用情况动态分配。</li><li>thick：创建时分配所有需要的空间。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>thin</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1134955145917"><a name="p1134955145917"></a><a name="p1134955145917"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="zh-cn_topic_0000001162111564_p57502011142910"><a name="zh-cn_topic_0000001162111564_p57502011142910"></a><a name="zh-cn_topic_0000001162111564_p57502011142910"></a>配置为thin时，创建卷不会立即分配所有需要的空间，而是根据使用情况动态分配。</p>
<p id="p371813715289"><a name="p371813715289"></a><a name="p371813715289"></a>OceanStor Dorado不支持thick</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p499022713590"><a name="p499022713590"></a><a name="p499022713590"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p552215442213"><a name="p552215442213"></a><a name="p552215442213"></a>可访问该卷的NFS客户端IP地址信息。</p>
<p id="p914297103211"><a name="p914297103211"></a><a name="p914297103211"></a>支持输入客户端主机名称（建议使用全称域名）、客户端IP地址、客户端IP地址段。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p1637013765210"><a name="p1637013765210"></a><a name="p1637013765210"></a>必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p113981010185211"><a name="p113981010185211"></a><a name="p113981010185211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p16134125519590"><a name="p16134125519590"></a><a name="p16134125519590"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p466615315578"><a name="p466615315578"></a><a name="p466615315578"></a>可以使用“*”表示任意客户端。当您不确定访问客户端IP信息时，建议使用“*”防止客户端访问被存储拒绝。</p>
<p id="p164521752175617"><a name="p164521752175617"></a><a name="p164521752175617"></a>当使用客户端主机名称时建议使用全称域名。</p>
<p id="p20828214135714"><a name="p20828214135714"></a><a name="p20828214135714"></a>IP地址支持IPv4、IPv6地址或两者的混合IP地址。</p>
<p id="p208641555185710"><a name="p208641555185710"></a><a name="p208641555185710"></a>可以同时输入多个主机名称、IP地址或IP地址段，以英文分号隔开。如示例："192.168.0.10;192.168.0.0/24;myserver1.test"</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row475081162913"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p187501311122918"><a name="zh-cn_topic_0000001162111564_p187501311122918"></a><a name="zh-cn_topic_0000001162111564_p187501311122918"></a>parameters.cloneSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="zh-cn_topic_0000001162111564_p77501911192918"><a name="zh-cn_topic_0000001162111564_p77501911192918"></a><a name="zh-cn_topic_0000001162111564_p77501911192918"></a>克隆速度。支持配置为1~4。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p20370157155213"><a name="p20370157155213"></a><a name="p20370157155213"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p2398810105211"><a name="p2398810105211"></a><a name="p2398810105211"></a>3</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p213412554593"><a name="p213412554593"></a><a name="p213412554593"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="zh-cn_topic_0000001162111564_p1775091110298"><a name="zh-cn_topic_0000001162111564_p1775091110298"></a><a name="zh-cn_topic_0000001162111564_p1775091110298"></a>4速度最快。配置克隆持久卷或从快照创建持久卷时生效。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750161119295"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p133711471387"><a name="p133711471387"></a><a name="p133711471387"></a>parameters.applicationType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p153378472388"><a name="p153378472388"></a><a name="p153378472388"></a>指定创建文件系统时的应用类型名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p193700711523"><a name="p193700711523"></a><a name="p193700711523"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p8398201010524"><a name="p8398201010524"></a><a name="p8398201010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p113415510596"><a name="p113415510596"></a><a name="p113415510596"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1795516502165"><a name="p1795516502165"></a><a name="p1795516502165"></a>在DeviceManager管理界面，选择“服务 &gt; 文件服务 &gt; 文件系统 &gt; 创建 &gt; 应用类型”，获取应用类型名称。</p>
</td>
</tr>
<tr id="row15478113119190"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p18478163131914"><a name="p18478163131914"></a><a name="p18478163131914"></a>parameters.qos</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15525175120211"><a name="p15525175120211"></a><a name="p15525175120211"></a>PV在存储侧的文件系统的QoS设置。</p>
<p id="p12218174732111"><a name="p12218174732111"></a><a name="p12218174732111"></a>配置项值是字典格式的JSON字符串（字符串两边由单引号修饰，字典key由双引号修饰）。如：'{"maxMBPS": 999, "maxIOPS": 999}'</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p03704715211"><a name="p03704715211"></a><a name="p03704715211"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p1439818100526"><a name="p1439818100526"></a><a name="p1439818100526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p813405513593"><a name="p813405513593"></a><a name="p813405513593"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p24789316192"><a name="p24789316192"></a><a name="p24789316192"></a>支持的QoS配置请参考<a href="#table1315616262719">表3</a>说明。</p>
</td>
</tr>
<tr id="row87671018115219"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p74248684617"><a name="p74248684617"></a><a name="p74248684617"></a>parameters.hyperMetro</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p84244684616"><a name="p84244684616"></a><a name="p84244684616"></a>是否创建双活卷。当使用的后端是双活类型的后端需要配置。</p>
<a name="ul196431227165817"></a><a name="ul196431227165817"></a><ul id="ul196431227165817"><li>"true"：创建的卷为双活卷。对接存储后端为双活后端时，该值必须为true。</li><li>"false"：创建的卷为普通卷。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p03705765218"><a name="p03705765218"></a><a name="p03705765218"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p12398101013527"><a name="p12398101013527"></a><a name="p12398101013527"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p12134125513598"><a name="p12134125513598"></a><a name="p12134125513598"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p5697340175314"><a name="p5697340175314"></a><a name="p5697340175314"></a>当使用的后端是双活类型的后端，且需要发放双活卷时，设置该参数为"true"，若设置为"false"，在后端对接的逻辑管理端口漂移的场景下，有业务中断的风险。</p>
</td>
</tr>
<tr id="row5571122410231"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p13571162414233"><a name="p13571162414233"></a><a name="p13571162414233"></a>parameters.metroPairSyncSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p85711524172312"><a name="p85711524172312"></a><a name="p85711524172312"></a>双活Pair同步速率。支持配置为1~4。</p>
<p id="p34101616202511"><a name="p34101616202511"></a><a name="p34101616202511"></a>可选值：</p>
<a name="ul15591625182515"></a><a name="ul15591625182515"></a><ul id="ul15591625182515"><li>1：低</li><li>2：中</li><li>3：高</li><li>4：最高</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p15716241239"><a name="p15716241239"></a><a name="p15716241239"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p1957172422315"><a name="p1957172422315"></a><a name="p1957172422315"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1513485519597"><a name="p1513485519597"></a><a name="p1513485519597"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1557114243237"><a name="p1557114243237"></a><a name="p1557114243237"></a>配置创建双活卷时生效。</p>
<p id="p688744685818"><a name="p688744685818"></a><a name="p688744685818"></a>注意：</p>
<a name="ul35821048175812"></a><a name="ul35821048175812"></a><ul id="ul35821048175812"><li>未配置该参数时，双活Pair存储速率由存储决定。</li><li>最高速率同步时可能导致主机时延增大。</li></ul>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>挂载到容器内的目录权限。</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p101341755105914"><a name="p101341755105914"></a><a name="p101341755105914"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>配置格式参考Linux权限设置，如“777”、“755”等。</p>
</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6718844173115"><a name="p6718844173115"></a><a name="p6718844173115"></a>parameters.rootSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p07183448314"><a name="p07183448314"></a><a name="p07183448314"></a><span>用于设置是否允许客户端的root权限。</span></p>
<p id="p129442384148"><a name="p129442384148"></a><a name="p129442384148"></a>可选值：</p>
<a name="ul124031949175810"></a><a name="ul124031949175810"></a><ul id="ul124031949175810"><li><span>root_squash：表示不允许客户端以root用户访问，客户端使用root用户访问时映射为匿名用户。</span></li><li><span>no_root_squash：</span><span>表示允许客户端以root用户访问，保留root用户的权限。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p73701479521"><a name="p73701479521"></a><a name="p73701479521"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p13981710165217"><a name="p13981710165217"></a><a name="p13981710165217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1413416553593"><a name="p1413416553593"></a><a name="p1413416553593"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14519141410508"><a name="p14519141410508"></a><a name="p14519141410508"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p3644133462719"><a name="p3644133462719"></a><a name="p3644133462719"></a>用于<span>设置是否保留共享目录的UID和GID。</span></p>
<p id="p19519161416501"><a name="p19519161416501"></a><a name="p19519161416501"></a>可选值：</p>
<a name="ul14691584594"></a><a name="ul14691584594"></a><ul id="ul14691584594"><li><span>all_squash：表示共享目录的UID和GID映射为匿名用户。</span></li><li><span>no_all_squash：表示保留共享目录的UID和GID。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p163702712526"><a name="p163702712526"></a><a name="p163702712526"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p7398121045211"><a name="p7398121045211"></a><a name="p7398121045211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p11134115595916"><a name="p11134115595916"></a><a name="p11134115595916"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row4779143834112"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6779173815418"><a name="p6779173815418"></a><a name="p6779173815418"></a>parameters.accesskrb5</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p159171449164417"><a name="p159171449164417"></a><a name="p159171449164417"></a>用于配置krb5安全协议。</p>
<a name="ul957213141953"></a><a name="ul957213141953"></a><ul id="ul957213141953"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p577912382417"><a name="p577912382417"></a><a name="p577912382417"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p9779193814412"><a name="p9779193814412"></a><a name="p9779193814412"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p111342055115917"><a name="p111342055115917"></a><a name="p111342055115917"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p15292191316454"><a name="p15292191316454"></a><a name="p15292191316454"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row99331045154111"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p933031214424"><a name="p933031214424"></a><a name="p933031214424"></a>parameters.accesskrb5i</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p7359241154"><a name="p7359241154"></a><a name="p7359241154"></a>用于配置krb5i安全协议。</p>
<a name="ul149421336953"></a><a name="ul149421336953"></a><ul id="ul149421336953"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p129331245154111"><a name="p129331245154111"></a><a name="p129331245154111"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p96976291391"><a name="p96976291391"></a><a name="p96976291391"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1713445513599"><a name="p1713445513599"></a><a name="p1713445513599"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p787455154620"><a name="p787455154620"></a><a name="p787455154620"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row47801443164117"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p11892181264220"><a name="p11892181264220"></a><a name="p11892181264220"></a>parameters.accesskrb5p</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p19699145314447"><a name="p19699145314447"></a><a name="p19699145314447"></a>用于配置krb5p安全协议。</p>
<a name="ul1713519393512"></a><a name="ul1713519393512"></a><ul id="ul1713519393512"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p1780134314118"><a name="p1780134314118"></a><a name="p1780134314118"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p14114173118919"><a name="p14114173118919"></a><a name="p14114173118919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p131341955105920"><a name="p131341955105920"></a><a name="p131341955105920"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1132519619463"><a name="p1132519619463"></a><a name="p1132519619463"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row446717321624"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p204682321028"><a name="p204682321028"></a><a name="p204682321028"></a>parameters.snapshotDirectoryVisibility</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p124681932122"><a name="p124681932122"></a><a name="p124681932122"></a>用于设置快照目录是否可见。</p>
<p id="p445010115419"><a name="p445010115419"></a><a name="p445010115419"></a>可选值：</p>
<a name="ul129350148597"></a><a name="ul129350148597"></a><ul id="ul129350148597"><li>visible：表示快照目录可见。</li><li>invisible：表示快照目录不可见。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p23707785219"><a name="p23707785219"></a><a name="p23707785219"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p14398210185219"><a name="p14398210185219"></a><a name="p14398210185219"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p101347555596"><a name="p101347555596"></a><a name="p101347555596"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1346853212219"><a name="p1346853212219"></a><a name="p1346853212219"></a>仅支持NAS存储。</p>
</td>
</tr>
<tr id="row102662571219"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p526715711214"><a name="p526715711214"></a><a name="p526715711214"></a><span>parameters.reservedSnapshotSpaceRatio</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p18267205722111"><a name="p18267205722111"></a><a name="p18267205722111"></a>用于配置快照预留空间。</p>
<p id="p31927526212"><a name="p31927526212"></a><a name="p31927526212"></a>参数类型：字符串</p>
<p id="p1010918514227"><a name="p1010918514227"></a><a name="p1010918514227"></a>取值范围："0"~"50"</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p3370167175211"><a name="p3370167175211"></a><a name="p3370167175211"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p5398131019522"><a name="p5398131019522"></a><a name="p5398131019522"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p16134155555910"><a name="p16134155555910"></a><a name="p16134155555910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p826718573213"><a name="p826718573213"></a><a name="p826718573213"></a>支持OceanStor Dorado 6.1.5+、OceanStor 6.1.5+的NAS存储。</p>
</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a><span>parameters.disableVerifyCapacity</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1899222312222"><a name="p1899222312222"></a><a name="p1899222312222"></a>是否禁用卷容量校验，禁用后将不校验卷容量是否为扇区大小整数倍。</p>
<p id="p4236912172515"><a name="p4236912172515"></a><a name="p4236912172515"></a>可选值：</p>
<a name="ul7370193012510"></a><a name="ul7370193012510"></a><ul id="ul7370193012510"><li>"true": 禁用卷容量校验。</li><li>"false": 开启卷容量校验。</li></ul>
<div class="notice" id="note163681158114916"><a name="note163681158114916"></a><a name="note163681158114916"></a><span class="noticetitle"> 须知： </span><div class="noticebody"><p id="p6368158104913"><a name="p6368158104913"></a><a name="p6368158104913"></a>使用Red Hat OpenShift Virtualization对接CSI时，该参数必须设置为"true"。</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p3134555195918"><a name="p3134555195918"></a><a name="p3134555195918"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p0723450135618"><a name="p0723450135618"></a><a name="p0723450135618"></a>OceanStor Dorado、OceanStor的扇区大小为512 B。</p>
</td>
</tr>
<tr id="row4937192492016"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1893710249209"><a name="p1893710249209"></a><a name="p1893710249209"></a><span>parameters.</span><span>description</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p20937182432010"><a name="p20937182432010"></a><a name="p20937182432010"></a>用于配置创建的文件系统的描述信息。</p>
<p id="p259255182110"><a name="p259255182110"></a><a name="p259255182110"></a>参数类型：字符串</p>
<p id="p8541312112118"><a name="p8541312112118"></a><a name="p8541312112118"></a>长度限制：0-255</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p15370175529"><a name="p15370175529"></a><a name="p15370175529"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p17398151010524"><a name="p17398151010524"></a><a name="p17398151010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p14134105525910"><a name="p14134105525910"></a><a name="p14134105525910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row1795755912408"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1036995916474"><a name="p1036995916474"></a><a name="p1036995916474"></a>parameters.advancedOptions</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p737mcpsimp"><a name="p737mcpsimp"></a><a name="p737mcpsimp"></a>高级<span id="text221712597301"><a name="text221712597301"></a><a name="text221712597301"></a>创卷</span>参数。</p>
<p id="p738mcpsimp"><a name="p738mcpsimp"></a><a name="p738mcpsimp"></a>配置项值是字典格式的JSON字符串（字符串两边由单引号修饰，字典key由双引号修饰）。如：'{"<span>CAPACITYTHRESHOLD</span>": 90}'</p>
</td>
<td class="cellrowborder" valign="top" width="6.692104490754329%" headers="mcps1.2.7.1.3 "><p id="p53719725212"><a name="p53719725212"></a><a name="p53719725212"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.609725075824283%" headers="mcps1.2.7.1.4 "><p id="p13398141016526"><a name="p13398141016526"></a><a name="p13398141016526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p17135555145910"><a name="p17135555145910"></a><a name="p17135555145910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p208761647111216"><a name="p208761647111216"></a><a name="p208761647111216"></a>支持的高级参数列表请参考<a href="#_table034918373916">表4</a>说明。</p>
</td>
</tr>
</tbody>
</table>

**表 2**  常用mountOptions参数说明

<a name="table65545557506"></a>
<table><thead align="left"><tr id="row1555414559506"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.1"><p id="p5274819155114"><a name="p5274819155114"></a><a name="p5274819155114"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.2"><p id="p19274619145114"><a name="p19274619145114"></a><a name="p19274619145114"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.3"><p id="p6274171905110"><a name="p6274171905110"></a><a name="p6274171905110"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.4"><p id="p13274419205110"><a name="p13274419205110"></a><a name="p13274419205110"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.5"><p id="p19274171912519"><a name="p19274171912519"></a><a name="p19274171912519"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row8555755185012"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p162853569513"><a name="p162853569513"></a><a name="p162853569513"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1928585612516"><a name="p1928585612516"></a><a name="p1928585612516"></a>主机侧NFS挂载选项。支持如下挂载选项：</p>
<p id="p328516567514"><a name="p328516567514"></a><a name="p328516567514"></a>nfsvers：挂载NFS时的协议版本。支持配置的参数值为“3”，“4”，“4.0”，“4.1”和”4.2”。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p15285356185114"><a name="p15285356185114"></a><a name="p15285356185114"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p182851756145119"><a name="p182851756145119"></a><a name="p182851756145119"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p228545619510"><a name="p228545619510"></a><a name="p228545619510"></a>在主机执行mount命令时-o参数后的可选选项。列表格式。</p>
<p id="p13285856115110"><a name="p13285856115110"></a><a name="p13285856115110"></a>指定NFS版本挂载时，当前支持NFS 3/4.0/4.1/4.2协议（需存储设备支持且开启）。当配置参数为nfsvers=4时，因为操作系统配置的不同，实际挂载可能为NFS 4的最高版本协议，如4.2，当需要使用4.0协议时，建议配置nfsvers=4.0。</p>
</td>
</tr>
<tr id="row6770194365110"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p92851256105112"><a name="p92851256105112"></a><a name="p92851256105112"></a>mountOptions.sec</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p172852567515"><a name="p172852567515"></a><a name="p172852567515"></a>用于指定Kerberos 5协议挂载NFS文件系统。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p128511565512"><a name="p128511565512"></a><a name="p128511565512"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p152851756145118"><a name="p152851756145118"></a><a name="p152851756145118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><a name="ul1028516561513"></a><a name="ul1028516561513"></a><ul id="ul1028516561513"><li>使用Kerberos 5协议时，请配置krb5。</li><li>使用Kerberos 5i协议时，请配置krb5i。</li><li>使用Kerberos 5p协议时，请配置krb5p。</li><li>Kerberos仅支持NFSv4.0及以上版本的NFS协议。</li><li>OceanStor Dorado和OceanStor 6.1.3及以上版本支持Kerberos。</li></ul>
</td>
</tr>
<tr id="row1142654125113"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p028615569516"><a name="p028615569516"></a><a name="p028615569516"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p328617569519"><a name="p328617569519"></a><a name="p328617569519"></a>指定NFS挂载时使用的传输协议。</p>
<p id="p18286185612518"><a name="p18286185612518"></a><a name="p18286185612518"></a>支持配置参数值为：“rdma”。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p172868562511"><a name="p172868562511"></a><a name="p172868562511"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p1286155614517"><a name="p1286155614517"></a><a name="p1286155614517"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><a name="ul1428618567518"></a><a name="ul1428618567518"></a><ul id="ul1428618567518"><li>OceanStor Dorado和OceanStor 6.1.7及以上的NAS存储。</li></ul>
</td>
</tr>
<tr id="row16338113817517"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p6286105617518"><a name="p6286105617518"></a><a name="p6286105617518"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p628665645117"><a name="p628665645117"></a><a name="p628665645117"></a>指定NFS挂载时使用的<span>协议端口</span>。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p192861056115114"><a name="p192861056115114"></a><a name="p192861056115114"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p628655665114"><a name="p628655665114"></a><a name="p628655665114"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p6286145618514"><a name="p6286145618514"></a><a name="p6286145618514"></a>传输协议方式使用“rdma”时，请设置为：20049。</p>
</td>
</tr>
</tbody>
</table>

**表 3**  支持的QoS配置

<a name="table1315616262719"></a>
<table><thead align="left"><tr id="row111561026772"><th class="cellrowborder" valign="top" width="13.278672132786722%" id="mcps1.2.5.1.1"><p id="p2579113031316"><a name="p2579113031316"></a><a name="p2579113031316"></a>存储类型</p>
</th>
<th class="cellrowborder" valign="top" width="15.348465153484653%" id="mcps1.2.5.1.2"><p id="p1915611264713"><a name="p1915611264713"></a><a name="p1915611264713"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="26.167383261673834%" id="mcps1.2.5.1.3"><p id="p915615267717"><a name="p915615267717"></a><a name="p915615267717"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="45.205479452054796%" id="mcps1.2.5.1.4"><p id="p111561926172"><a name="p111561926172"></a><a name="p111561926172"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row18484951131113"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="p35795302132"><a name="p35795302132"></a><a name="p35795302132"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="p18524175292"><a name="p18524175292"></a><a name="p18524175292"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="p05251782913"><a name="p05251782913"></a><a name="p05251782913"></a>控制读写类型。</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="p152017102914"><a name="p152017102914"></a><a name="p152017102914"></a>可选参数（未明确指定将使用后端存储默认值，具体参考相关存储资料）。</p>
<p id="p85218172294"><a name="p85218172294"></a><a name="p85218172294"></a>有效值如下：</p>
<a name="ul5521517142918"></a><a name="ul5521517142918"></a><ul id="ul5521517142918"><li>0：读I/O</li><li>1：写I/O</li><li>2：读写I/O</li></ul>
</td>
</tr>
<tr id="row1548485117111"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p155211732919"><a name="p155211732919"></a><a name="p155211732919"></a><span>MAXBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p952111772918"><a name="p952111772918"></a><a name="p952111772918"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p352171716294"><a name="p352171716294"></a><a name="p352171716294"></a>单位MB/s，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row124848513110"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p9522175292"><a name="p9522175292"></a><a name="p9522175292"></a><span>MINBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p19522171298"><a name="p19522171298"></a><a name="p19522171298"></a>最小带宽保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p2052141711297"><a name="p2052141711297"></a><a name="p2052141711297"></a>单位MB/s，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row74854512113"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1052417132916"><a name="p1052417132916"></a><a name="p1052417132916"></a><span>MAXIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p352117102912"><a name="p352117102912"></a><a name="p352117102912"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p165211714296"><a name="p165211714296"></a><a name="p165211714296"></a>有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row1816819710019"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1316813713016"><a name="p1316813713016"></a><a name="p1316813713016"></a><span>MINIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p0521917172915"><a name="p0521917172915"></a><a name="p0521917172915"></a>最小IOPS保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p105201742914"><a name="p105201742914"></a><a name="p105201742914"></a>有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row1448555120112"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1952517192913"><a name="p1952517192913"></a><a name="p1952517192913"></a><span>LATENCY</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p85211722911"><a name="p85211722911"></a><a name="p85211722911"></a>最大时延保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p352161718293"><a name="p352161718293"></a><a name="p352161718293"></a>单位ms，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="row19156226876"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="p74551059151512"><a name="p74551059151512"></a><a name="p74551059151512"></a>OceanStor Dorado/OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="p115692619717"><a name="p115692619717"></a><a name="p115692619717"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="p41575261777"><a name="p41575261777"></a><a name="p41575261777"></a>控制读写类型。</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="p1315717261879"><a name="p1315717261879"></a><a name="p1315717261879"></a>有效值如下：</p>
<a name="ul121571261076"></a><a name="ul121571261076"></a><ul id="ul121571261076"><li>2：读写I/O</li></ul>
</td>
</tr>
<tr id="row17157826078"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p2015762612718"><a name="p2015762612718"></a><a name="p2015762612718"></a><span>MAXBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p7157126276"><a name="p7157126276"></a><a name="p7157126276"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p1515732617718"><a name="p1515732617718"></a><a name="p1515732617718"></a>单位MB/s，类型为整数， 范围1~999999999。</p>
</td>
</tr>
<tr id="row1215710263712"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p191576267720"><a name="p191576267720"></a><a name="p191576267720"></a><span>MINBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1215715261371"><a name="p1215715261371"></a><a name="p1215715261371"></a>最小带宽保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p8157426475"><a name="p8157426475"></a><a name="p8157426475"></a>单位MB/s，类型为整数， 范围1~999999999。</p>
</td>
</tr>
<tr id="row415742618720"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p01578266719"><a name="p01578266719"></a><a name="p01578266719"></a><span>MAXIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1515716261474"><a name="p1515716261474"></a><a name="p1515716261474"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p131571926873"><a name="p131571926873"></a><a name="p131571926873"></a>类型为整数， 范围100~999999999。</p>
</td>
</tr>
<tr id="row215718268711"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p01574267717"><a name="p01574267717"></a><a name="p01574267717"></a><span>MINIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p151571326777"><a name="p151571326777"></a><a name="p151571326777"></a>最小IOPS保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p15157102614718"><a name="p15157102614718"></a><a name="p15157102614718"></a>类型为整数， 范围100~999999999。</p>
</td>
</tr>
<tr id="row20157162619710"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p4157626475"><a name="p4157626475"></a><a name="p4157626475"></a><span>LATENCY</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p4157202613716"><a name="p4157202613716"></a><a name="p4157202613716"></a>最大时延保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p111571264718"><a name="p111571264718"></a><a name="p111571264718"></a>单位ms，仅支持配置0.5或1.5。</p>
</td>
</tr>
</tbody>
</table>

**表 4**  支持的高级创卷参数

<a name="_table034918373916"></a>
<table><thead align="left"><tr id="row756mcpsimp"><th class="cellrowborder" valign="top" width="16.85%" id="mcps1.2.4.1.1"><p id="p760mcpsimp"><a name="p760mcpsimp"></a><a name="p760mcpsimp"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="39.33%" id="mcps1.2.4.1.2"><p id="p762mcpsimp"><a name="p762mcpsimp"></a><a name="p762mcpsimp"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="43.82%" id="mcps1.2.4.1.3"><p id="p764mcpsimp"><a name="p764mcpsimp"></a><a name="p764mcpsimp"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row766mcpsimp"><td class="cellrowborder" valign="top" width="16.85%" headers="mcps1.2.4.1.1 "><p id="p770mcpsimp"><a name="p770mcpsimp"></a><a name="p770mcpsimp"></a><span>CAPACITYTHRESHOLD</span></p>
</td>
<td class="cellrowborder" valign="top" width="39.33%" headers="mcps1.2.4.1.2 "><p id="p773mcpsimp"><a name="p773mcpsimp"></a><a name="p773mcpsimp"></a>总空间容量告警阈值。</p>
</td>
<td class="cellrowborder" valign="top" width="43.82%" headers="mcps1.2.4.1.3 "><p id="p775mcpsimp"><a name="p775mcpsimp"></a><a name="p775mcpsimp"></a>参数类型，uint64。</p>
<p id="p776mcpsimp"><a name="p776mcpsimp"></a><a name="p776mcpsimp"></a>默认值和取值范围请参考对应存储产品手册。</p>
</td>
</tr>
</tbody>
</table>

