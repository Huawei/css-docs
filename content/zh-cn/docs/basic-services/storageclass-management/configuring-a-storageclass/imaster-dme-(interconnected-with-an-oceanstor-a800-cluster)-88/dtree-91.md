---
title: "Dtree"
linkTitle: "Dtree"
description: 
weight: 3
---

## 创建存储类{#section826673014506}

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

## NFS协议配置示例{#section18328546173619}

容器使用NFS协议对接Dtree资源时，可以参考如下存储类配置示例。该示例中，NFS挂载时指定版本为3。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dtree-181
  volumeType: dtree
  allocType: thin
  authClient: "*"
mountOptions:
  - nfsvers=3 # NFS挂载时指定版本为3
```

## DataTurbo协议配置示例{#section17204182983712}

容器DataTurbo协议对接Dtree资源时，可以参考如下配置示例。该示例中，DataTurbo共享用户名为user01。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: dtfs-nas-181
  volumeType: dtree
  allocType: thin
  authUser: user01
```

## Dtree支持的存储类参数详细说明{#section17270153014505}

**表 1**  StorageClass配置参数说明

<a name="zh-cn_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="18.481557577536446%" id="mcps1.2.7.1.1"><p id="p4360205445916"><a name="p4360205445916"></a><a name="p4360205445916"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="23.089717248801485%" id="mcps1.2.7.1.2"><p id="p3360185410592"><a name="p3360185410592"></a><a name="p3360185410592"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="6.848644946678408%" id="mcps1.2.7.1.3"><p id="p5360854155919"><a name="p5360854155919"></a><a name="p5360854155919"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="8.453184619900206%" id="mcps1.2.7.1.4"><p id="p53602054105911"><a name="p53602054105911"></a><a name="p53602054105911"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="7.35740142843166%" id="mcps1.2.7.1.5"><p id="p193607544599"><a name="p193607544599"></a><a name="p193607544599"></a>纳管卷是否生效</p>
</th>
<th class="cellrowborder" valign="top" width="35.7694941786518%" id="mcps1.2.7.1.6"><p id="p19360135495917"><a name="p19360135495917"></a><a name="p19360135495917"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14360115415917"><a name="p14360115415917"></a><a name="p14360115415917"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p836011544596"><a name="p836011544596"></a><a name="p836011544596"></a>自定义的StorageClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1736085411593"><a name="p1736085411593"></a><a name="p1736085411593"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p03601954125910"><a name="p03601954125910"></a><a name="p03601954125910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p11360145417590"><a name="p11360145417590"></a><a name="p11360145417590"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1360554145914"><a name="p1360554145914"></a><a name="p1360554145914"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p136014549598"><a name="p136014549598"></a><a name="p136014549598"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p536045495915"><a name="p536045495915"></a><a name="p536045495915"></a>制备器名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1436035415598"><a name="p1436035415598"></a><a name="p1436035415598"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p036018545593"><a name="p036018545593"></a><a name="p036018545593"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p153609549594"><a name="p153609549594"></a><a name="p153609549594"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p16360654125917"><a name="p16360654125917"></a><a name="p16360654125917"></a>该字段需要指定为安装华为CSI时设置的驱动名称。</p>
<p id="p17360205455917"><a name="p17360205455917"></a><a name="p17360205455917"></a>取值和values.yaml文件中driverName一致。</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p536015495918"><a name="p536015495918"></a><a name="p536015495918"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1736035416597"><a name="p1736035416597"></a><a name="p1736035416597"></a>回收策略。支持如下类型：</p>
<a name="ul1360115415918"></a><a name="ul1360115415918"></a><ul id="ul1360115415918"><li>Delete：自动回收资源。</li><li>Retain：<span>手动回收资源</span>。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p9360155413597"><a name="p9360155413597"></a><a name="p9360155413597"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p036055475913"><a name="p036055475913"></a><a name="p036055475913"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p536015415599"><a name="p536015415599"></a><a name="p536015415599"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul4360554145916"></a><a name="ul4360554145916"></a><ul id="ul4360554145916"><li>Delete：删除PV/PVC时会关联删除存储上的资源。</li><li>Retain：删除PV/PVC时不会删除存储上的资源。</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1936045416598"><a name="p1936045416598"></a><a name="p1936045416598"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p136065419593"><a name="p136065419593"></a><a name="p136065419593"></a>是否允许卷扩展。参数设置为true 时，使用该StorageClass的PV可以进行扩容操作。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p123601054195913"><a name="p123601054195913"></a><a name="p123601054195913"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p536015546597"><a name="p536015546597"></a><a name="p536015546597"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p18360205415914"><a name="p18360205415914"></a><a name="p18360205415914"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p6360185415915"><a name="p6360185415915"></a><a name="p6360185415915"></a>此功能仅可用于扩容PV，不能用于缩容PV。</p>
</td>
</tr>
<tr id="row63343268297"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14360205410597"><a name="p14360205410597"></a><a name="p14360205410597"></a>mountOptions</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p7360115475917"><a name="p7360115475917"></a><a name="p7360115475917"></a>挂载参数列表，可用于指定主机执行mount命令时-o选项的参数。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p3360135435914"><a name="p3360135435914"></a><a name="p3360135435914"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p236015543598"><a name="p236015543598"></a><a name="p236015543598"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p4360154175917"><a name="p4360154175917"></a><a name="p4360154175917"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1936045445914"><a name="p1936045445914"></a><a name="p1936045445914"></a>常见的mountOptions参数参考<a href="#table133792080248">表2</a>。</p>
<p id="p14360854175917"><a name="p14360854175917"></a><a name="p14360854175917"></a>也可自行指定其他挂载参数。</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p2360854165918"><a name="p2360854165918"></a><a name="p2360854165918"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p7360115414591"><a name="p7360115414591"></a><a name="p7360115414591"></a>待创建资源所在的后端名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p173601654145917"><a name="p173601654145917"></a><a name="p173601654145917"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1036195435913"><a name="p1036195435913"></a><a name="p1036195435913"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p14361165411595"><a name="p14361165411595"></a><a name="p14361165411595"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>如果不设置，华为CSI随机选择一个满足容量要求的后端创建资源。</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>建议指定后端，确保创建的资源在预期的后端上。</p>
<p id="p1746961523912"><a name="p1746961523912"></a><a name="p1746961523912"></a>配置了parameters.parentname时，该参数必填。</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p346918322193"><a name="p346918322193"></a><a name="p346918322193"></a><span>parameters.</span>parentname</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1046913215196"><a name="p1046913215196"></a><a name="p1046913215196"></a>当前存储上的某一个文件系统名称，在此文件系统下创建Dtree。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p34696327196"><a name="p34696327196"></a><a name="p34696327196"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p19469032191910"><a name="p19469032191910"></a><a name="p19469032191910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p11469163213191"><a name="p11469163213191"></a><a name="p11469163213191"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1146912323198"><a name="p1146912323198"></a><a name="p1146912323198"></a>当backend未配置parentname时，该参数必填。</p>
<p id="p17469143218194"><a name="p17469143218194"></a><a name="p17469143218194"></a>若仅在StorageClass中配置了parentname，而存储后端中未配置时，要求在安装CSI时将CSIDriverObject.attachRequired设置为true。</p>
</td>
</tr>
<tr id="row12968565337"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p10361145455915"><a name="p10361145455915"></a><a name="p10361145455915"></a>parameters.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p12361125411596"><a name="p12361125411596"></a><a name="p12361125411596"></a>指定动态卷供应创建的存储资源名称。</p>
<p id="p636111549590"><a name="p636111549590"></a><a name="p636111549590"></a>支持配置占位符对存储资源名称进行自定义，支持的占位符如下：</p>
<a name="ul0361354175919"></a><a name="ul0361354175919"></a><ul id="ul0361354175919"><li>PVC命名空间：{{ .PVCNamespace }}</li><li>PVC名称：{{ .PVCName }}</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1361175425912"><a name="p1361175425912"></a><a name="p1361175425912"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p236115412598"><a name="p236115412598"></a><a name="p236115412598"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p236114548594"><a name="p236114548594"></a><a name="p236114548594"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul5361145475918"></a><a name="ul5361145475918"></a><ul id="ul5361145475918"><li>支持配置字母、数字、"-"、"_"、"."，不能配置为空，生成的存储资源名称长度范围是1-255。</li><li>必须同时配置PVC命名空间和PVC名称。</li><li>为了避免资源名称重复，会将PVC UID作为唯一标识符默认添加到名称末尾。</li></ul>
<p id="p7361105465918"><a name="p7361105465918"></a><a name="p7361105465918"></a></p>
<p id="p23613547598"><a name="p23613547598"></a><a name="p23613547598"></a>配置示例：</p>
<p id="p20361454185915"><a name="p20361454185915"></a><a name="p20361454185915"></a>PVC命名空间为："namespace"，PVC名称为："pvc-1"，PVC UID："c2fd3f46-bf17-4a7d-b88e-2e3232bae434"。</p>
<p id="p1136105425912"><a name="p1136105425912"></a><a name="p1136105425912"></a>volumeName配置为: "prefix-{{ .PVCNamespace }}_{{ .PVCName }}"。</p>
<p id="p14361145475913"><a name="p14361145475913"></a><a name="p14361145475913"></a>最终存储资源名称为："prefix-namespace_pvc-1-c2fd3f46bf174a7db88e2e3232bae434"。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p336111545595"><a name="p336111545595"></a><a name="p336111545595"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1236105414591"><a name="p1236105414591"></a><a name="p1236105414591"></a>待创建卷类型。支持如下类型：</p>
<a name="ul83612547596"></a><a name="ul83612547596"></a><ul id="ul83612547596"><li>lun：存储侧发放的资源是LUN。</li><li>fs：存储侧发放的资源是文件系统。</li><li>dtree：存储侧发放的资源是Dtree类型的卷</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p5361115414595"><a name="p5361115414595"></a><a name="p5361115414595"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p836125405919"><a name="p836125405919"></a><a name="p836125405919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1236119545592"><a name="p1236119545592"></a><a name="p1236119545592"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p11361354145911"><a name="p11361354145911"></a><a name="p11361354145911"></a>使用Dtree时，必须为dtree。</p>
</td>
</tr>
<tr id="row20604911148"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="zh-cn_topic_0000001162111564_p13750171110290"><a name="zh-cn_topic_0000001162111564_p13750171110290"></a><a name="zh-cn_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="zh-cn_topic_0000001162111564_p67501211102911"><a name="zh-cn_topic_0000001162111564_p67501211102911"></a><a name="zh-cn_topic_0000001162111564_p67501211102911"></a>待创建卷的分配类型。支持如下类型：</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li>thin：创建时不会分配所有需要的空间，而是根据使用情况动态分配。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>thin</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p9722056181617"><a name="p9722056181617"></a><a name="p9722056181617"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="zh-cn_topic_0000001162111564_p57502011142910"><a name="zh-cn_topic_0000001162111564_p57502011142910"></a><a name="zh-cn_topic_0000001162111564_p57502011142910"></a>配置为thin时，创建卷不会立即分配所有需要的空间，而是根据使用情况动态分配。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1636105411595"><a name="p1636105411595"></a><a name="p1636105411595"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1361145414593"><a name="p1361145414593"></a><a name="p1361145414593"></a>可访问该卷的NFS客户端IP地址信息，在使用nfs和nfs+协议时必选。</p>
<p id="p03611454155915"><a name="p03611454155915"></a><a name="p03611454155915"></a>支持输入客户端主机名称（建议使用全称域名）、客户端IP地址、客户端IP地址段。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p17361175425917"><a name="p17361175425917"></a><a name="p17361175425917"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p636110547592"><a name="p636110547592"></a><a name="p636110547592"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p736185495917"><a name="p736185495917"></a><a name="p736185495917"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1636119549596"><a name="p1636119549596"></a><a name="p1636119549596"></a>可以使用“*”表示任意客户端。当您不确定访问客户端IP信息时，建议使用“*”防止客户端访问被存储拒绝。</p>
<p id="p336155414598"><a name="p336155414598"></a><a name="p336155414598"></a>当使用客户端主机名称时建议使用全称域名。</p>
<p id="p536119542595"><a name="p536119542595"></a><a name="p536119542595"></a>IP地址支持IPv4、IPv6地址或两者的混合IP地址。</p>
<p id="p636118544595"><a name="p636118544595"></a><a name="p636118544595"></a>可以同时输入多个主机名称、IP地址或IP地址段，以英文分号隔开。如示例："192.168.0.10;192.168.0.0/24;myserver1.test"</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p236119547597"><a name="p236119547597"></a><a name="p236119547597"></a>parameters.authUser</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p63611054195911"><a name="p63611054195911"></a><a name="p63611054195911"></a>可访问DataTurbo共享的DataTurbo用户，在使用DataTurbo(dtfs)协议时必选。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p11361115415913"><a name="p11361115415913"></a><a name="p11361115415913"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1736175419593"><a name="p1736175419593"></a><a name="p1736175419593"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p136165435918"><a name="p136165435918"></a><a name="p136165435918"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p10361185420590"><a name="p10361185420590"></a><a name="p10361185420590"></a>可以同时输入多个DataTurbo用户，以英文分号隔开。如示例："auth_user1;auth_user2;auth_user3"</p>
</td>
</tr>
<tr id="row2531173517323"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p15361205411598"><a name="p15361205411598"></a><a name="p15361205411598"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15361175418593"><a name="p15361175418593"></a><a name="p15361175418593"></a>挂载到容器内的目录权限。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p23611549592"><a name="p23611549592"></a><a name="p23611549592"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p15361195495910"><a name="p15361195495910"></a><a name="p15361195495910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p83610540593"><a name="p83610540593"></a><a name="p83610540593"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1836195415918"><a name="p1836195415918"></a><a name="p1836195415918"></a>配置格式参考Linux权限设置，如"777"、"755"等。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750161119295"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p636195475915"><a name="p636195475915"></a><a name="p636195475915"></a>parameters.rootSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15361854105912"><a name="p15361854105912"></a><a name="p15361854105912"></a><span>用于设置是否允许客户端的root权限。</span></p>
<p id="p19361454175914"><a name="p19361454175914"></a><a name="p19361454175914"></a>可选值：</p>
<a name="ul1736165435912"></a><a name="ul1736165435912"></a><ul id="ul1736165435912"><li><span>root_squash：表示不允许客户端以root用户访问，客户端使用root用户访问时映射为匿名用户。</span></li><li><span>no_root_squash：</span><span>表示允许客户端以root用户访问，保留root用户的权限。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p436165495914"><a name="p436165495914"></a><a name="p436165495914"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p20361105405917"><a name="p20361105405917"></a><a name="p20361105405917"></a><span>no_root_squash</span></p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p436115425914"><a name="p436115425914"></a><a name="p436115425914"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6361354175916"><a name="p6361354175916"></a><a name="p6361354175916"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p10361054155920"><a name="p10361054155920"></a><a name="p10361054155920"></a>用于<span>设置是否保留共享目录的UID和GID。</span></p>
<p id="p13361195410596"><a name="p13361195410596"></a><a name="p13361195410596"></a>可选值：</p>
<a name="ul736116546593"></a><a name="ul736116546593"></a><ul id="ul736116546593"><li><span>all_squash：表示共享目录的UID和GID映射为匿名用户。</span></li><li><span>no_all_squash：表示保留共享目录的UID和GID。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1636112547597"><a name="p1636112547597"></a><a name="p1636112547597"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1936125495916"><a name="p1936125495916"></a><a name="p1936125495916"></a><span>no_all_squash</span></p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p63619545598"><a name="p63619545598"></a><a name="p63619545598"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14362135495917"><a name="p14362135495917"></a><a name="p14362135495917"></a><span>parameters.disableVerifyCapacity</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p636216541599"><a name="p636216541599"></a><a name="p636216541599"></a>是否禁用卷容量校验，禁用后将不校验卷容量是否为扇区大小整数倍。</p>
<p id="p3362145495919"><a name="p3362145495919"></a><a name="p3362145495919"></a>可选值：</p>
<a name="ul123624548592"></a><a name="ul123624548592"></a><ul id="ul123624548592"><li>"true": 禁用卷容量校验。</li><li>"false": 开启卷容量校验。</li></ul>
<div class="notice" id="note03621054175911"><a name="note03621054175911"></a><a name="note03621054175911"></a><span class="noticetitle"> 须知： </span><div class="noticebody"><p id="p1836218544599"><a name="p1836218544599"></a><a name="p1836218544599"></a>使用Red Hat OpenShift Virtualization对接CSI时，该参数必须设置为"true"。</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p2362054145917"><a name="p2362054145917"></a><a name="p2362054145917"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p63625549594"><a name="p63625549594"></a><a name="p63625549594"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1136295417590"><a name="p1136295417590"></a><a name="p1136295417590"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p13621954105917"><a name="p13621954105917"></a><a name="p13621954105917"></a>iMaster DME Dtree的扇区大小为1KB。</p>
</td>
</tr>
</tbody>
</table>

**表 2**  常用mountOptions参数说明

<a name="table133792080248"></a>
<table><thead align="left"><tr id="row7379880247"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.1"><p id="p736255418592"><a name="p736255418592"></a><a name="p736255418592"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.2"><p id="p1336225415916"><a name="p1336225415916"></a><a name="p1336225415916"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.3"><p id="p15362195417595"><a name="p15362195417595"></a><a name="p15362195417595"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.4"><p id="p2362155419596"><a name="p2362155419596"></a><a name="p2362155419596"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.5"><p id="p16362754175910"><a name="p16362754175910"></a><a name="p16362754175910"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row17379182241"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p162853569513"><a name="p162853569513"></a><a name="p162853569513"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1928585612516"><a name="p1928585612516"></a><a name="p1928585612516"></a>主机侧NFS挂载选项。支持如下挂载选项：</p>
<p id="p328516567514"><a name="p328516567514"></a><a name="p328516567514"></a>nfsvers：挂载NFS时的协议版本。支持配置的参数值为“3”。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p15285356185114"><a name="p15285356185114"></a><a name="p15285356185114"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p182851756145119"><a name="p182851756145119"></a><a name="p182851756145119"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p228545619510"><a name="p228545619510"></a><a name="p228545619510"></a>在主机执行mount命令时-o参数后的可选选项。列表格式。</p>
<p id="p13285856115110"><a name="p13285856115110"></a><a name="p13285856115110"></a>指定NFS版本挂载时，当前支持NFS 3协议（需存储设备支持且开启）。</p>
</td>
</tr>
<tr id="row437958102416"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p3371343123317"><a name="p3371343123317"></a><a name="p3371343123317"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p5379432333"><a name="p5379432333"></a><a name="p5379432333"></a>指定NFS挂载时使用的传输协议。</p>
<p id="p43784311336"><a name="p43784311336"></a><a name="p43784311336"></a>支持配置参数值为：“rdma”。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p637743143311"><a name="p637743143311"></a><a name="p637743143311"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p13371243193313"><a name="p13371243193313"></a><a name="p13371243193313"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row3379182244"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p183744319338"><a name="p183744319338"></a><a name="p183744319338"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1237943163315"><a name="p1237943163315"></a><a name="p1237943163315"></a>指定NFS挂载时使用的<span>协议端口</span>。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p19371043103315"><a name="p19371043103315"></a><a name="p19371043103315"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p143774323313"><a name="p143774323313"></a><a name="p143774323313"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p13371743113311"><a name="p13371743113311"></a><a name="p13371743113311"></a>传输协议方式使用“rdma”时，请设置为：20049。</p>
</td>
</tr>
<tr id="row937988202418"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p63621054105914"><a name="p63621054105914"></a><a name="p63621054105914"></a>mountOptions.dn</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p236215411596"><a name="p236215411596"></a><a name="p236215411596"></a>指定DataTurbo(dtfs)协议挂载时使用的逻辑端口的域名。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p123626548593"><a name="p123626548593"></a><a name="p123626548593"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p2036235420592"><a name="p2036235420592"></a><a name="p2036235420592"></a>存储设备WWN</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p153621754155919"><a name="p153621754155919"></a><a name="p153621754155919"></a>挂载HyperScale集群文件系统dn需要填写HyperScale集群下的域名。</p>
<p id="p1136210542597"><a name="p1136210542597"></a><a name="p1136210542597"></a>dn参数描述仅供参考，DataTurbo协议其他挂载详细参数说明请参考<a href="https://support.huawei.com/enterprise/zh/doc/EDOC1100539415/a8d5b478?idPath=7919749|251366268|250389224|263153904|264568316" target="_blank" rel="noopener noreferrer">《AI Storage Kit 25.x.x DTFS 用户指南》</a>。</p>
</td>
</tr>
</tbody>
</table>

