---
title: "Dtree"
linkTitle: "Dtree"
description: 
weight: 2
---

## 创建存储类{#section1464491216409}

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

## NFS协议支持的存储类配置示例{#section1053116812255}

容器使用NFS协议对接Dtree资源时，可以参考如下存储类配置示例。该示例中，NFS挂载时指定版本为4.1。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dtree-181
  parentname: parent-filesystem-name
  volumeType: dtree
  authClient: "*"
mountOptions:
  - nfsvers=4.1 # NFS挂载时指定版本为4.1
```

## NFS+协议支持的存储类配置示例{#section36031677149}

容器使用NFS+协议对接Dtree资源时，可以参考如下存储类配置示例。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dtree-181
  parentname: parent-filesystem-name
  volumeType: dtree
  authClient: "*"
```

## Dtree支持的存储类参数详细说明{#section1758842912252}

**表 1**  StorageClass配置参数说明

<a name="zh-cn_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="20.43%" id="mcps1.2.6.1.1"><p id="zh-cn_topic_0000001162111564_p875071122919"><a name="zh-cn_topic_0000001162111564_p875071122919"></a><a name="zh-cn_topic_0000001162111564_p875071122919"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="25.52%" id="mcps1.2.6.1.2"><p id="zh-cn_topic_0000001162111564_p17750131113295"><a name="zh-cn_topic_0000001162111564_p17750131113295"></a><a name="zh-cn_topic_0000001162111564_p17750131113295"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="5.18%" id="mcps1.2.6.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="9.34%" id="mcps1.2.6.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="39.53%" id="mcps1.2.6.1.5"><p id="zh-cn_topic_0000001162111564_p075011113295"><a name="zh-cn_topic_0000001162111564_p075011113295"></a><a name="zh-cn_topic_0000001162111564_p075011113295"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p4750141111292"><a name="zh-cn_topic_0000001162111564_p4750141111292"></a><a name="zh-cn_topic_0000001162111564_p4750141111292"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p475091120296"><a name="zh-cn_topic_0000001162111564_p475091120296"></a><a name="zh-cn_topic_0000001162111564_p475091120296"></a>自定义的StorageClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001162111564_p861713973915"><a name="zh-cn_topic_0000001162111564_p861713973915"></a><a name="zh-cn_topic_0000001162111564_p861713973915"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p8750161119299"><a name="zh-cn_topic_0000001162111564_p8750161119299"></a><a name="zh-cn_topic_0000001162111564_p8750161119299"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p15750201119295"><a name="zh-cn_topic_0000001162111564_p15750201119295"></a><a name="zh-cn_topic_0000001162111564_p15750201119295"></a>制备器名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>该字段需要指定为安装华为CSI时设置的驱动名称。</p>
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>取值和values.yaml文件中driverName一致。</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p119108535312"><a name="p119108535312"></a><a name="p119108535312"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p16910135393118"><a name="p16910135393118"></a><a name="p16910135393118"></a>回收策略。支持如下类型：</p>
<a name="ul5209917195517"></a><a name="ul5209917195517"></a><ul id="ul5209917195517"><li>Delete：自动回收资源。</li><li>Retain：<span>手动回收资源</span>。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li>Delete：删除PV/PVC时会关联删除存储上的资源。</li><li>Retain：删除PV/PVC时不会删除存储上的资源。</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p192771821155012"><a name="p192771821155012"></a><a name="p192771821155012"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p8277132112501"><a name="p8277132112501"></a><a name="p8277132112501"></a>是否允许卷扩展。参数设置为true 时，使用该StorageClass的PV可以进行扩容操作。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p13923171118495"><a name="p13923171118495"></a><a name="p13923171118495"></a>此功能仅可用于扩容PV，不能用于缩容PV。</p>
</td>
</tr>
<tr id="row63343268297"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p13432132752911"><a name="p13432132752911"></a><a name="p13432132752911"></a>mountOptions</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p134321427192916"><a name="p134321427192916"></a><a name="p134321427192916"></a>挂载参数列表，可用于指定主机执行mount命令时-o选项的参数。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p2432227172910"><a name="p2432227172910"></a><a name="p2432227172910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1432112762919"><a name="p1432112762919"></a><a name="p1432112762919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p15432162772912"><a name="p15432162772912"></a><a name="p15432162772912"></a>常见的mountOptions参数参考<a href="#table65545557506">表2</a>。</p>
<p id="p104322027152920"><a name="p104322027152920"></a><a name="p104322027152920"></a>也可自行指定其他挂载参数。</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>待创建资源所在的后端名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>如果不设置，华为CSI随机选择一个满足容量要求的后端创建资源。</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>建议指定后端，确保创建的资源在预期的后端上。</p>
<p id="p1746961523912"><a name="p1746961523912"></a><a name="p1746961523912"></a>配置了parameters.parentname时，该参数必填。</p>
</td>
</tr>
<tr id="row9425191220356"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p122751558184511"><a name="p122751558184511"></a><a name="p122751558184511"></a><span>parameters.</span>parentname</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p327525817451"><a name="p327525817451"></a><a name="p327525817451"></a>当前存储上的某一个文件系统名称，在此文件系统下创建Dtree。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p8275125812453"><a name="p8275125812453"></a><a name="p8275125812453"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p327535812450"><a name="p327535812450"></a><a name="p327535812450"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p16731411944"><a name="p16731411944"></a><a name="p16731411944"></a>当backend未配置parentname时，该参数必填。</p>
<p id="p122751358134518"><a name="p122751358134518"></a><a name="p122751358134518"></a>若仅在StorageClass中配置了parentname，而存储后端中未配置时，要求在安装CSI时将CSIDriverObject.attachRequired设置为true。</p>
</td>
</tr>
<tr id="row12968565337"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p19968166163320"><a name="p19968166163320"></a><a name="p19968166163320"></a>parameters.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p270mcpsimp"><a name="p270mcpsimp"></a><a name="p270mcpsimp"></a>指定动态卷供应创建的存储资源名称。</p>
<p id="p271mcpsimp"><a name="p271mcpsimp"></a><a name="p271mcpsimp"></a>支持配置占位符对存储资源名称进行自定义，支持的占位符如下：</p>
<a name="ul277mcpsimp"></a><a name="ul277mcpsimp"></a><ul id="ul277mcpsimp"><li>PVC命名空间：{{ .PVCNamespace }}</li><li>PVC名称：{{ .PVCName }}</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p49687693314"><a name="p49687693314"></a><a name="p49687693314"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p096819643312"><a name="p096819643312"></a><a name="p096819643312"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul165061538173414"></a><a name="ul165061538173414"></a><ul id="ul165061538173414"><li>支持配置字母、数字、"-"、"_"、"."，不能配置为空，生成的存储资源名称长度范围是1-255。</li><li>必须同时配置PVC命名空间和PVC名称。</li><li>为了避免资源名称重复，会将PVC UID作为唯一标识符默认添加到名称末尾。</li></ul>
<p id="p3486174714359"><a name="p3486174714359"></a><a name="p3486174714359"></a></p>
<p id="p292mcpsimp"><a name="p292mcpsimp"></a><a name="p292mcpsimp"></a>配置示例：</p>
<p id="p293mcpsimp"><a name="p293mcpsimp"></a><a name="p293mcpsimp"></a>PVC命名空间为："namespace"，PVC名称为："pvc-1"，PVC UID："c2fd3f46-bf17-4a7d-b88e-2e3232bae434"。</p>
<p id="p301mcpsimp"><a name="p301mcpsimp"></a><a name="p301mcpsimp"></a>volumeName配置为: "prefix-{{ .PVCNamespace }}_{{ .PVCName }}"。</p>
<p id="p302mcpsimp"><a name="p302mcpsimp"></a><a name="p302mcpsimp"></a>最终存储资源名称为："prefix-namespace_pvc-1-c2fd3f46bf174a7db88e2e3232bae434"。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001162111564_p1775061119292"><a name="zh-cn_topic_0000001162111564_p1775061119292"></a><a name="zh-cn_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001162111564_p975011122920"><a name="zh-cn_topic_0000001162111564_p975011122920"></a><a name="zh-cn_topic_0000001162111564_p975011122920"></a>待创建卷类型。支持如下类型：</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li>lun：存储侧发放的资源是LUN。</li><li>fs：存储侧发放的资源是文件系统。</li><li>dtree：存储侧发放的资源是Dtree类型的卷</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p159151023181412"><a name="p159151023181412"></a><a name="p159151023181412"></a>使用Dtree时，必须为dtree。</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p499022713590"><a name="p499022713590"></a><a name="p499022713590"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p552215442213"><a name="p552215442213"></a><a name="p552215442213"></a>可访问该卷的NFS客户端IP地址信息。</p>
<p id="p914297103211"><a name="p914297103211"></a><a name="p914297103211"></a>支持输入客户端主机名称（建议使用全称域名）、客户端IP地址、客户端IP地址段。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1637013765210"><a name="p1637013765210"></a><a name="p1637013765210"></a>必选</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p113981010185211"><a name="p113981010185211"></a><a name="p113981010185211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p466615315578"><a name="p466615315578"></a><a name="p466615315578"></a>可以使用“*”表示任意客户端。当您不确定访问客户端IP信息时，建议使用“*”防止客户端访问被存储拒绝。</p>
<p id="p164521752175617"><a name="p164521752175617"></a><a name="p164521752175617"></a>当使用客户端主机名称时建议使用全称域名。</p>
<p id="p20828214135714"><a name="p20828214135714"></a><a name="p20828214135714"></a>IP地址支持IPv4、IPv6地址或两者的混合IP地址。</p>
<p id="p208641555185710"><a name="p208641555185710"></a><a name="p208641555185710"></a>可以同时输入多个主机名称、IP地址或IP地址段，以英文分号隔开。如示例："192.168.0.10;192.168.0.0/24;myserver1.test"</p>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>挂载到容器内的目录权限。</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>配置格式参考Linux权限设置，如“777”、“755”等。</p>
</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p6718844173115"><a name="p6718844173115"></a><a name="p6718844173115"></a>parameters.rootSquash</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p07183448314"><a name="p07183448314"></a><a name="p07183448314"></a><span>用于设置是否允许客户端的root权限。</span></p>
<p id="p129442384148"><a name="p129442384148"></a><a name="p129442384148"></a>可选值：</p>
<a name="ul124031949175810"></a><a name="ul124031949175810"></a><ul id="ul124031949175810"><li><span>root_squash：表示不允许客户端以root用户访问，客户端使用root用户访问时映射为匿名用户。</span></li><li><span>no_root_squash：</span><span>表示允许客户端以root用户访问，保留root用户的权限。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p73701479521"><a name="p73701479521"></a><a name="p73701479521"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p13981710165217"><a name="p13981710165217"></a><a name="p13981710165217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p14519141410508"><a name="p14519141410508"></a><a name="p14519141410508"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p3644133462719"><a name="p3644133462719"></a><a name="p3644133462719"></a>用于<span>设置是否保留共享目录的UID和GID。</span></p>
<p id="p19519161416501"><a name="p19519161416501"></a><a name="p19519161416501"></a>可选值：</p>
<a name="ul14691584594"></a><a name="ul14691584594"></a><ul id="ul14691584594"><li><span>all_squash：表示共享目录的UID和GID映射为匿名用户。</span></li><li><span>no_all_squash：表示保留共享目录的UID和GID。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p163702712526"><a name="p163702712526"></a><a name="p163702712526"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p7398121045211"><a name="p7398121045211"></a><a name="p7398121045211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row4779143834112"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p6779173815418"><a name="p6779173815418"></a><a name="p6779173815418"></a>parameters.accesskrb5</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p159171449164417"><a name="p159171449164417"></a><a name="p159171449164417"></a>用于配置krb5安全协议。</p>
<a name="ul957213141953"></a><a name="ul957213141953"></a><ul id="ul957213141953"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p577912382417"><a name="p577912382417"></a><a name="p577912382417"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p9779193814412"><a name="p9779193814412"></a><a name="p9779193814412"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p15292191316454"><a name="p15292191316454"></a><a name="p15292191316454"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row99331045154111"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p933031214424"><a name="p933031214424"></a><a name="p933031214424"></a>parameters.accesskrb5i</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p7359241154"><a name="p7359241154"></a><a name="p7359241154"></a>用于配置krb5i安全协议。</p>
<a name="ul149421336953"></a><a name="ul149421336953"></a><ul id="ul149421336953"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p129331245154111"><a name="p129331245154111"></a><a name="p129331245154111"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p96976291391"><a name="p96976291391"></a><a name="p96976291391"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p787455154620"><a name="p787455154620"></a><a name="p787455154620"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row47801443164117"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p11892181264220"><a name="p11892181264220"></a><a name="p11892181264220"></a>parameters.accesskrb5p</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p19699145314447"><a name="p19699145314447"></a><a name="p19699145314447"></a>用于配置krb5p安全协议。</p>
<a name="ul1713519393512"></a><a name="ul1713519393512"></a><ul id="ul1713519393512"><li>read_only：只读</li><li>read_write：读写</li><li>none：无权限</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1780134314118"><a name="p1780134314118"></a><a name="p1780134314118"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p14114173118919"><a name="p14114173118919"></a><a name="p14114173118919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p1132519619463"><a name="p1132519619463"></a><a name="p1132519619463"></a>挂载时，可以在mountOptions中指定参数sec。</p>
</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a><span>parameters.disableVerifyCapacity</span></p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000002427305089_p1899222312222"><a name="zh-cn_topic_0000002427305089_p1899222312222"></a><a name="zh-cn_topic_0000002427305089_p1899222312222"></a>是否禁用卷容量校验，禁用后将不校验卷容量是否为扇区大小整数倍。</p>
<p id="zh-cn_topic_0000002427305089_p4236912172515"><a name="zh-cn_topic_0000002427305089_p4236912172515"></a><a name="zh-cn_topic_0000002427305089_p4236912172515"></a>可选值：</p>
<a name="zh-cn_topic_0000002427305089_ul7370193012510"></a><a name="zh-cn_topic_0000002427305089_ul7370193012510"></a><ul id="zh-cn_topic_0000002427305089_ul7370193012510"><li>"true": 禁用卷容量校验。</li><li>"false": 开启卷容量校验。</li></ul>
<div class="notice" id="zh-cn_topic_0000002427305089_note163681158114916"><a name="zh-cn_topic_0000002427305089_note163681158114916"></a><a name="zh-cn_topic_0000002427305089_note163681158114916"></a><span class="noticetitle"> 须知： </span><div class="noticebody"><p id="zh-cn_topic_0000002427305089_p6368158104913"><a name="zh-cn_topic_0000002427305089_p6368158104913"></a><a name="zh-cn_topic_0000002427305089_p6368158104913"></a>使用Red Hat OpenShift Virtualization对接CSI时，该参数必须设置为"true"。</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p0723450135618"><a name="p0723450135618"></a><a name="p0723450135618"></a>OceanStor Dorado、OceanStor的扇区大小为512 B。</p>
</td>
</tr>
<tr id="row4937192492016"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p1893710249209"><a name="p1893710249209"></a><a name="p1893710249209"></a><span>parameters.</span><span>description</span></p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p20937182432010"><a name="p20937182432010"></a><a name="p20937182432010"></a>用于配置创建的Dtree共享的描述信息。</p>
<p id="p259255182110"><a name="p259255182110"></a><a name="p259255182110"></a>参数类型：字符串</p>
<p id="p8541312112118"><a name="p8541312112118"></a><a name="p8541312112118"></a>长度限制：0-255</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p15370175529"><a name="p15370175529"></a><a name="p15370175529"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p5564181665510"><a name="p5564181665510"></a><a name="p5564181665510"></a>Created from Kubernetes CSI</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
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

