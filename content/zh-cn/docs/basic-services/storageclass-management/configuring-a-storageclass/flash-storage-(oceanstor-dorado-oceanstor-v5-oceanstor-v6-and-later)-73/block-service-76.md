---
title: "块业务"
linkTitle: "块业务"
description: 
weight: 3
---

## 创建存储类{#section432911256567}

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

## 块业务存储类配置示例{#section19821415151111}

使用LUN作为存储资源时，且需要格式化文件系统为本地文件系统时，可以参考如下示例。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: lun-181
  pool: StoragePool001
  volumeType: lun
  allocType: thin
  fsType: ext4
```

## 块业务支持的存储类参数详细说明{#section624915310113}

**表 1**  StorageClass配置参数说明

<a name="zh-cn_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="18.481557577536446%" id="mcps1.2.7.1.1"><p id="zh-cn_topic_0000001162111564_p875071122919"><a name="zh-cn_topic_0000001162111564_p875071122919"></a><a name="zh-cn_topic_0000001162111564_p875071122919"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="23.089717248801485%" id="mcps1.2.7.1.2"><p id="zh-cn_topic_0000001162111564_p17750131113295"><a name="zh-cn_topic_0000001162111564_p17750131113295"></a><a name="zh-cn_topic_0000001162111564_p17750131113295"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="6.848644946678408%" id="mcps1.2.7.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="8.453184619900206%" id="mcps1.2.7.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>默认值</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>Delete</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p2432227172910"><a name="p2432227172910"></a><a name="p2432227172910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1432112762919"><a name="p1432112762919"></a><a name="p1432112762919"></a>-</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p10863133161415"><a name="p10863133161415"></a><a name="p10863133161415"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>如果不设置，华为CSI随机选择一个满足容量要求的后端创建资源。</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>建议指定后端，确保创建的资源在预期的后端上。</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p395711171674"><a name="p395711171674"></a><a name="p395711171674"></a>parameters.pool</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p119571517771"><a name="p119571517771"></a><a name="p119571517771"></a>待创建资源所在的存储资源池名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p43701077524"><a name="p43701077524"></a><a name="p43701077524"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p12398310135213"><a name="p12398310135213"></a><a name="p12398310135213"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p78631236144"><a name="p78631236144"></a><a name="p78631236144"></a>否</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p49687693314"><a name="p49687693314"></a><a name="p49687693314"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p096819643312"><a name="p096819643312"></a><a name="p096819643312"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p2086315351417"><a name="p2086315351417"></a><a name="p2086315351417"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul165061538173414"></a><a name="ul165061538173414"></a><ul id="ul165061538173414"><li>支持配置字母、数字、"-"、"_"、"."，不能配置为空，生成的存储资源名称长度范围是1-255。</li><li>必须同时配置PVC命名空间和PVC名称。</li><li>为了避免资源名称重复，会将PVC UID作为唯一标识符默认添加到名称末尾。</li></ul>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p686315351411"><a name="p686315351411"></a><a name="p686315351411"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p153691347193413"><a name="p153691347193413"></a><a name="p153691347193413"></a>此处固定配置为lun。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p13750171110290"><a name="zh-cn_topic_0000001162111564_p13750171110290"></a><a name="zh-cn_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="zh-cn_topic_0000001162111564_p67501211102911"><a name="zh-cn_topic_0000001162111564_p67501211102911"></a><a name="zh-cn_topic_0000001162111564_p67501211102911"></a>待创建卷的分配类型。支持如下类型：</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li>thin：创建时不会分配所有需要的空间，而是根据使用情况动态分配。</li><li>thick：创建时分配所有需要的空间。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>thin</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p18863335147"><a name="p18863335147"></a><a name="p18863335147"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="zh-cn_topic_0000001162111564_p57502011142910"><a name="zh-cn_topic_0000001162111564_p57502011142910"></a><a name="zh-cn_topic_0000001162111564_p57502011142910"></a>配置为thin时，创建卷不会立即分配所有需要的空间，而是根据使用情况动态分配。</p>
<p id="p371813715289"><a name="p371813715289"></a><a name="p371813715289"></a>OceanStor Dorado不支持thick</p>
</td>
</tr>
<tr id="row167642021133711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p18750171111299"><a name="zh-cn_topic_0000001162111564_p18750171111299"></a><a name="zh-cn_topic_0000001162111564_p18750171111299"></a>parameters.fsType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p19169191111571"><a name="p19169191111571"></a><a name="p19169191111571"></a>主机文件系统类型。支持类型为：</p>
<a name="ul9614171916576"></a><a name="ul9614171916576"></a><ul id="ul9614171916576"><li>ext2</li><li>ext3</li><li>ext4</li><li>xfs</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p937047165217"><a name="p937047165217"></a><a name="p937047165217"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1439871055220"><a name="p1439871055220"></a><a name="p1439871055220"></a>ext4</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p10863113181414"><a name="p10863113181414"></a><a name="p10863113181414"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="zh-cn_topic_0000001162111564_p8750311172910"><a name="zh-cn_topic_0000001162111564_p8750311172910"></a><a name="zh-cn_topic_0000001162111564_p8750311172910"></a>仅当PVC的volumeMode配置为“Filesystem”时生效。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row475081162913"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p187501311122918"><a name="zh-cn_topic_0000001162111564_p187501311122918"></a><a name="zh-cn_topic_0000001162111564_p187501311122918"></a>parameters.cloneSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="zh-cn_topic_0000001162111564_p77501911192918"><a name="zh-cn_topic_0000001162111564_p77501911192918"></a><a name="zh-cn_topic_0000001162111564_p77501911192918"></a>克隆速度。支持配置为1~4。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p20370157155213"><a name="p20370157155213"></a><a name="p20370157155213"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p2398810105211"><a name="p2398810105211"></a><a name="p2398810105211"></a>3</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p208635341411"><a name="p208635341411"></a><a name="p208635341411"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="zh-cn_topic_0000001162111564_p1775091110298"><a name="zh-cn_topic_0000001162111564_p1775091110298"></a><a name="zh-cn_topic_0000001162111564_p1775091110298"></a>4速度最快。配置克隆PVC或从快照创建PVC时生效。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750161119295"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p133711471387"><a name="p133711471387"></a><a name="p133711471387"></a>parameters.applicationType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p153378472388"><a name="p153378472388"></a><a name="p153378472388"></a>指定创建LUN时的应用类型名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p193700711523"><a name="p193700711523"></a><a name="p193700711523"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p8398201010524"><a name="p8398201010524"></a><a name="p8398201010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p886363141411"><a name="p886363141411"></a><a name="p886363141411"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p19352161314317"><a name="p19352161314317"></a><a name="p19352161314317"></a>在DeviceManager管理界面，选择“服务 &gt; 块服务 &gt; LUN组 (Namespace组)&gt; LUN (Namespace)&gt; 创建 &gt; 应用类型”，获取应用类型名称。</p>
</td>
</tr>
<tr id="row15478113119190"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p18478163131914"><a name="p18478163131914"></a><a name="p18478163131914"></a>parameters.qos</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15525175120211"><a name="p15525175120211"></a><a name="p15525175120211"></a>PV在存储侧的LUN/NAS的QoS设置。</p>
<p id="p12218174732111"><a name="p12218174732111"></a><a name="p12218174732111"></a>配置项值是字典格式的JSON字符串（字符串两边由单引号修饰，字典key由双引号修饰）。如：'{"maxMBPS": 999, "maxIOPS": 999}'</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p03704715211"><a name="p03704715211"></a><a name="p03704715211"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1439818100526"><a name="p1439818100526"></a><a name="p1439818100526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p158633361418"><a name="p158633361418"></a><a name="p158633361418"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p24789316192"><a name="p24789316192"></a><a name="p24789316192"></a>支持的QoS配置请参考<a href="#table74841513116">表3</a>说明。</p>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>挂载到容器内的目录权限。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1886312301416"><a name="p1886312301416"></a><a name="p1886312301416"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>配置格式参考Linux权限设置，如“777”、“755”等。</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1286333181417"><a name="p1286333181417"></a><a name="p1286333181417"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p0723450135618"><a name="p0723450135618"></a><a name="p0723450135618"></a>OceanStor Dorado、OceanStor的扇区大小为512 B。</p>
</td>
</tr>
<tr id="row4937192492016"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1893710249209"><a name="p1893710249209"></a><a name="p1893710249209"></a><span>parameters.</span><span>description</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p20937182432010"><a name="p20937182432010"></a><a name="p20937182432010"></a>用于配置创建的LUN的描述信息。</p>
<p id="p259255182110"><a name="p259255182110"></a><a name="p259255182110"></a>参数类型：字符串</p>
<p id="p8541312112118"><a name="p8541312112118"></a><a name="p8541312112118"></a>长度限制：0-255</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p15370175529"><a name="p15370175529"></a><a name="p15370175529"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p873262175517"><a name="p873262175517"></a><a name="p873262175517"></a>Created from Kubernetes CSI</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p2863193131413"><a name="p2863193131413"></a><a name="p2863193131413"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
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
<tbody><tr id="row15555205517503"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p202861156155119"><a name="p202861156155119"></a><a name="p202861156155119"></a>mountOptions.discard</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1928616565514"><a name="p1928616565514"></a><a name="p1928616565514"></a><span>挂载文件系统时自动触发Trim/Discard操作。该操作会通知块设备释放未使用的块</span>。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p1328610561511"><a name="p1328610561511"></a><a name="p1328610561511"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p2286175613513"><a name="p2286175613513"></a><a name="p2286175613513"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p4286556155111"><a name="p4286556155111"></a><a name="p4286556155111"></a>支持xfs、ext4文件系统。</p>
</td>
</tr>
</tbody>
</table>

**表 3**  支持的QoS配置

<a name="table74841513116"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000002427305089_row111561026772"><th class="cellrowborder" valign="top" width="13.278672132786722%" id="mcps1.2.5.1.1"><p id="zh-cn_topic_0000002427305089_p2579113031316"><a name="zh-cn_topic_0000002427305089_p2579113031316"></a><a name="zh-cn_topic_0000002427305089_p2579113031316"></a>存储类型</p>
</th>
<th class="cellrowborder" valign="top" width="15.348465153484653%" id="mcps1.2.5.1.2"><p id="zh-cn_topic_0000002427305089_p1915611264713"><a name="zh-cn_topic_0000002427305089_p1915611264713"></a><a name="zh-cn_topic_0000002427305089_p1915611264713"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="26.167383261673834%" id="mcps1.2.5.1.3"><p id="zh-cn_topic_0000002427305089_p915615267717"><a name="zh-cn_topic_0000002427305089_p915615267717"></a><a name="zh-cn_topic_0000002427305089_p915615267717"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="45.205479452054796%" id="mcps1.2.5.1.4"><p id="zh-cn_topic_0000002427305089_p111561926172"><a name="zh-cn_topic_0000002427305089_p111561926172"></a><a name="zh-cn_topic_0000002427305089_p111561926172"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000002427305089_row18484951131113"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p35795302132"><a name="zh-cn_topic_0000002427305089_p35795302132"></a><a name="zh-cn_topic_0000002427305089_p35795302132"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p18524175292"><a name="zh-cn_topic_0000002427305089_p18524175292"></a><a name="zh-cn_topic_0000002427305089_p18524175292"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p05251782913"><a name="zh-cn_topic_0000002427305089_p05251782913"></a><a name="zh-cn_topic_0000002427305089_p05251782913"></a>控制读写类型。</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000002427305089_p152017102914"><a name="zh-cn_topic_0000002427305089_p152017102914"></a><a name="zh-cn_topic_0000002427305089_p152017102914"></a>可选参数（未明确指定将使用后端存储默认值，具体参考相关存储资料）。</p>
<p id="zh-cn_topic_0000002427305089_p85218172294"><a name="zh-cn_topic_0000002427305089_p85218172294"></a><a name="zh-cn_topic_0000002427305089_p85218172294"></a>有效值如下：</p>
<a name="zh-cn_topic_0000002427305089_ul5521517142918"></a><a name="zh-cn_topic_0000002427305089_ul5521517142918"></a><ul id="zh-cn_topic_0000002427305089_ul5521517142918"><li>0：读I/O</li><li>1：写I/O</li><li>2：读写I/O</li></ul>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row1548485117111"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p155211732919"><a name="zh-cn_topic_0000002427305089_p155211732919"></a><a name="zh-cn_topic_0000002427305089_p155211732919"></a><span>MAXBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p952111772918"><a name="zh-cn_topic_0000002427305089_p952111772918"></a><a name="zh-cn_topic_0000002427305089_p952111772918"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p352171716294"><a name="zh-cn_topic_0000002427305089_p352171716294"></a><a name="zh-cn_topic_0000002427305089_p352171716294"></a>单位MB/s，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row124848513110"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p9522175292"><a name="zh-cn_topic_0000002427305089_p9522175292"></a><a name="zh-cn_topic_0000002427305089_p9522175292"></a><span>MINBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p19522171298"><a name="zh-cn_topic_0000002427305089_p19522171298"></a><a name="zh-cn_topic_0000002427305089_p19522171298"></a>最小带宽保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p2052141711297"><a name="zh-cn_topic_0000002427305089_p2052141711297"></a><a name="zh-cn_topic_0000002427305089_p2052141711297"></a>单位MB/s，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row74854512113"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p1052417132916"><a name="zh-cn_topic_0000002427305089_p1052417132916"></a><a name="zh-cn_topic_0000002427305089_p1052417132916"></a><span>MAXIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p352117102912"><a name="zh-cn_topic_0000002427305089_p352117102912"></a><a name="zh-cn_topic_0000002427305089_p352117102912"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p165211714296"><a name="zh-cn_topic_0000002427305089_p165211714296"></a><a name="zh-cn_topic_0000002427305089_p165211714296"></a>有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row1816819710019"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p1316813713016"><a name="zh-cn_topic_0000002427305089_p1316813713016"></a><a name="zh-cn_topic_0000002427305089_p1316813713016"></a><span>MINIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p0521917172915"><a name="zh-cn_topic_0000002427305089_p0521917172915"></a><a name="zh-cn_topic_0000002427305089_p0521917172915"></a>最小IOPS保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p105201742914"><a name="zh-cn_topic_0000002427305089_p105201742914"></a><a name="zh-cn_topic_0000002427305089_p105201742914"></a>有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row1448555120112"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p1952517192913"><a name="zh-cn_topic_0000002427305089_p1952517192913"></a><a name="zh-cn_topic_0000002427305089_p1952517192913"></a><span>LATENCY</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p85211722911"><a name="zh-cn_topic_0000002427305089_p85211722911"></a><a name="zh-cn_topic_0000002427305089_p85211722911"></a>最大时延保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p352161718293"><a name="zh-cn_topic_0000002427305089_p352161718293"></a><a name="zh-cn_topic_0000002427305089_p352161718293"></a>单位ms，有效值为&gt;0的整数。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row19156226876"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p74551059151512"><a name="zh-cn_topic_0000002427305089_p74551059151512"></a><a name="zh-cn_topic_0000002427305089_p74551059151512"></a>OceanStor Dorado/OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p115692619717"><a name="zh-cn_topic_0000002427305089_p115692619717"></a><a name="zh-cn_topic_0000002427305089_p115692619717"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p41575261777"><a name="zh-cn_topic_0000002427305089_p41575261777"></a><a name="zh-cn_topic_0000002427305089_p41575261777"></a>控制读写类型。</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0000002427305089_p1315717261879"><a name="zh-cn_topic_0000002427305089_p1315717261879"></a><a name="zh-cn_topic_0000002427305089_p1315717261879"></a>有效值如下：</p>
<a name="zh-cn_topic_0000002427305089_ul121571261076"></a><a name="zh-cn_topic_0000002427305089_ul121571261076"></a><ul id="zh-cn_topic_0000002427305089_ul121571261076"><li>2：读写I/O</li></ul>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row17157826078"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p2015762612718"><a name="zh-cn_topic_0000002427305089_p2015762612718"></a><a name="zh-cn_topic_0000002427305089_p2015762612718"></a><span>MAXBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p7157126276"><a name="zh-cn_topic_0000002427305089_p7157126276"></a><a name="zh-cn_topic_0000002427305089_p7157126276"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p1515732617718"><a name="zh-cn_topic_0000002427305089_p1515732617718"></a><a name="zh-cn_topic_0000002427305089_p1515732617718"></a>单位MB/s，类型为整数， 范围1~999999999。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row1215710263712"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p191576267720"><a name="zh-cn_topic_0000002427305089_p191576267720"></a><a name="zh-cn_topic_0000002427305089_p191576267720"></a><span>MINBANDWIDTH</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p1215715261371"><a name="zh-cn_topic_0000002427305089_p1215715261371"></a><a name="zh-cn_topic_0000002427305089_p1215715261371"></a>最小带宽保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p8157426475"><a name="zh-cn_topic_0000002427305089_p8157426475"></a><a name="zh-cn_topic_0000002427305089_p8157426475"></a>单位MB/s，类型为整数， 范围1~999999999。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row415742618720"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p01578266719"><a name="zh-cn_topic_0000002427305089_p01578266719"></a><a name="zh-cn_topic_0000002427305089_p01578266719"></a><span>MAXIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p1515716261474"><a name="zh-cn_topic_0000002427305089_p1515716261474"></a><a name="zh-cn_topic_0000002427305089_p1515716261474"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p131571926873"><a name="zh-cn_topic_0000002427305089_p131571926873"></a><a name="zh-cn_topic_0000002427305089_p131571926873"></a>类型为整数， 范围100~999999999。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row215718268711"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p01574267717"><a name="zh-cn_topic_0000002427305089_p01574267717"></a><a name="zh-cn_topic_0000002427305089_p01574267717"></a><span>MINIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p151571326777"><a name="zh-cn_topic_0000002427305089_p151571326777"></a><a name="zh-cn_topic_0000002427305089_p151571326777"></a>最小IOPS保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p15157102614718"><a name="zh-cn_topic_0000002427305089_p15157102614718"></a><a name="zh-cn_topic_0000002427305089_p15157102614718"></a>类型为整数， 范围100~999999999。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000002427305089_row20157162619710"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0000002427305089_p4157626475"><a name="zh-cn_topic_0000002427305089_p4157626475"></a><a name="zh-cn_topic_0000002427305089_p4157626475"></a><span>LATENCY</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0000002427305089_p4157202613716"><a name="zh-cn_topic_0000002427305089_p4157202613716"></a><a name="zh-cn_topic_0000002427305089_p4157202613716"></a>最大时延保护策略。</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0000002427305089_p111571264718"><a name="zh-cn_topic_0000002427305089_p111571264718"></a><a name="zh-cn_topic_0000002427305089_p111571264718"></a>单位ms，仅支持配置0.5或1.5。</p>
</td>
</tr>
</tbody>
</table>

