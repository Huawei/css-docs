---
title: "文件系统"
linkTitle: "文件系统"
description: 
weight: 1
---

## 创建存储类{#section1071213595715}

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
  pool: pool001
  volumeType: fs
  allocType: thin
  authClient: "*"
mountOptions:
  - nfsvers=4.1 # NFS挂载时指定版本为4.1
```

## DPC协议配置示例{#section420824715129}

存储支持DPC协议访问时，可以在StorageClass中配置DPC访问的挂载参数。本例中设置挂载时使用“**acl**”做鉴权参数，使用“**cnflush**”为设置异步刷盘模式。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dpc-101
  pool: pool001
  volumeType: fs
  allocType: thin
mountOptions:
  - acl # 鉴权参数
  - cnflush # 设置异步刷盘模式
```

## 文件系统支持的存储类参数详细说明{#section1758842912252}

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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p184571869188"><a name="p184571869188"></a><a name="p184571869188"></a>否</p>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p445711620185"><a name="p445711620185"></a><a name="p445711620185"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p99571317978"><a name="p99571317978"></a><a name="p99571317978"></a>如果不设置，华为CSI会在所选后端上随机选择一个满足容量要求的存储池创建资源。建议指定存储池，确保创建的资源在预期的存储池上。</p>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p845812615184"><a name="p845812615184"></a><a name="p845812615184"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p159151023181412"><a name="p159151023181412"></a><a name="p159151023181412"></a>此处固定配置为fs。</p>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p14582641817"><a name="p14582641817"></a><a name="p14582641817"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="zh-cn_topic_0000001162111564_p57502011142910"><a name="zh-cn_topic_0000001162111564_p57502011142910"></a><a name="zh-cn_topic_0000001162111564_p57502011142910"></a>配置为thin时，创建卷不会立即分配所有需要的空间，而是根据使用情况动态分配。</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p499022713590"><a name="p499022713590"></a><a name="p499022713590"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p552215442213"><a name="p552215442213"></a><a name="p552215442213"></a>可访问该卷的NFS客户端IP地址信息。在使用nfs协议时必选。</p>
<p id="p914297103211"><a name="p914297103211"></a><a name="p914297103211"></a>支持输入客户端主机名称（建议使用全称域名）、客户端IP地址、客户端IP地址段。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637013765210"><a name="p1637013765210"></a><a name="p1637013765210"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p113981010185211"><a name="p113981010185211"></a><a name="p113981010185211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1145820621813"><a name="p1145820621813"></a><a name="p1145820621813"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p466615315578"><a name="p466615315578"></a><a name="p466615315578"></a>可以使用“*”表示任意客户端。当您不确定访问客户端IP信息时，建议使用“*”防止客户端访问被存储拒绝。</p>
<p id="p164521752175617"><a name="p164521752175617"></a><a name="p164521752175617"></a>当使用客户端主机名称时建议使用全称域名。</p>
<p id="p20828214135714"><a name="p20828214135714"></a><a name="p20828214135714"></a>IP地址支持IPv4、IPv6地址或两者的混合IP地址。</p>
<p id="p208641555185710"><a name="p208641555185710"></a><a name="p208641555185710"></a>可以同时输入多个主机名称、IP地址或IP地址段，以英文分号隔开。如示例："192.168.0.10;192.168.0.0/24;myserver1.test"</p>
</td>
</tr>
<tr id="row17122191413012"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p513251416380"><a name="p513251416380"></a><a name="p513251416380"></a>parameters.storageQuota</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p613221412389"><a name="p613221412389"></a><a name="p613221412389"></a>文件系统配额设置。</p>
<p id="p7371208112220"><a name="p7371208112220"></a><a name="p7371208112220"></a>配置项值是字典格式的JSON字符串（字符串两边由单引号修饰，字典key由双引号修饰）。如：'{"spaceQuota": "softQuota", "gracePeriod": 100}'</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p73707715210"><a name="p73707715210"></a><a name="p73707715210"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p639812105526"><a name="p639812105526"></a><a name="p639812105526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1545816617183"><a name="p1545816617183"></a><a name="p1545816617183"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p21321014103814"><a name="p21321014103814"></a><a name="p21321014103814"></a>支持的配额配置请参考<a href="#table2083974632312">表4</a>说明。</p>
</td>
</tr>
<tr id="row15478113119190"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p18478163131914"><a name="p18478163131914"></a><a name="p18478163131914"></a>parameters.qos</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15525175120211"><a name="p15525175120211"></a><a name="p15525175120211"></a>PV在存储侧的文件系统的QoS设置。</p>
<p id="p12218174732111"><a name="p12218174732111"></a><a name="p12218174732111"></a>配置项值是字典格式的JSON字符串（字符串两边由单引号修饰，字典key由双引号修饰）。如：'{"maxMBPS": 999, "maxIOPS": 999}'</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p03704715211"><a name="p03704715211"></a><a name="p03704715211"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1439818100526"><a name="p1439818100526"></a><a name="p1439818100526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1245817618182"><a name="p1245817618182"></a><a name="p1245817618182"></a>否</p>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p6458267189"><a name="p6458267189"></a><a name="p6458267189"></a>否</p>
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
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p73701479521"><a name="p73701479521"></a><a name="p73701479521"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p13981710165217"><a name="p13981710165217"></a><a name="p13981710165217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p145819610185"><a name="p145819610185"></a><a name="p145819610185"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14519141410508"><a name="p14519141410508"></a><a name="p14519141410508"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p3644133462719"><a name="p3644133462719"></a><a name="p3644133462719"></a>用于<span>设置是否保留共享目录的UID和GID。</span></p>
<p id="p19519161416501"><a name="p19519161416501"></a><a name="p19519161416501"></a>可选值：</p>
<a name="ul14691584594"></a><a name="ul14691584594"></a><ul id="ul14691584594"><li><span>all_squash：表示共享目录的UID和GID映射为匿名用户。</span></li><li><span>no_all_squash：表示保留共享目录的UID和GID。</span></li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p163702712526"><a name="p163702712526"></a><a name="p163702712526"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p7398121045211"><a name="p7398121045211"></a><a name="p7398121045211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1345810617186"><a name="p1345810617186"></a><a name="p1345810617186"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row446717321624"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p204682321028"><a name="p204682321028"></a><a name="p204682321028"></a>parameters.snapshotDirectoryVisibility</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p124681932122"><a name="p124681932122"></a><a name="p124681932122"></a>用于设置快照目录是否可见。</p>
<p id="p445010115419"><a name="p445010115419"></a><a name="p445010115419"></a>可选值：</p>
<a name="ul129350148597"></a><a name="ul129350148597"></a><ul id="ul129350148597"><li>visible：表示快照目录可见。</li><li>invisible：表示快照目录不可见。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p23707785219"><a name="p23707785219"></a><a name="p23707785219"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p14398210185219"><a name="p14398210185219"></a><a name="p14398210185219"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1045846111813"><a name="p1045846111813"></a><a name="p1045846111813"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p164589651813"><a name="p164589651813"></a><a name="p164589651813"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p332084914582"><a name="p332084914582"></a><a name="p332084914582"></a>OceanStor Pacific NAS的扇区大小为1 KB。</p>
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
<tr id="row1142654125113"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p028615569516"><a name="p028615569516"></a><a name="p028615569516"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p328617569519"><a name="p328617569519"></a><a name="p328617569519"></a>指定NFS挂载时使用的传输协议。</p>
<p id="p18286185612518"><a name="p18286185612518"></a><a name="p18286185612518"></a>支持配置参数值为：“rdma”。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p172868562511"><a name="p172868562511"></a><a name="p172868562511"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p1286155614517"><a name="p1286155614517"></a><a name="p1286155614517"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p647716526533"><a name="p647716526533"></a><a name="p647716526533"></a>仅8.2.0及以后版本支持。</p>
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
<tr id="row697305614016"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p128525610511"><a name="p128525610511"></a><a name="p128525610511"></a>mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p112856566510"><a name="p112856566510"></a><a name="p112856566510"></a>DPC命名空间支持ACL功能。DPC客户端支持POSIX ACL、NFSv4 ACL、NT ACL的鉴权行为。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p228505620512"><a name="p228505620512"></a><a name="p228505620512"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p132852564514"><a name="p132852564514"></a><a name="p132852564514"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p428595635116"><a name="p428595635116"></a><a name="p428595635116"></a>acl、aclonlyposix、cnflush、cflush参数描述仅供参考，详细参数说明请参考<a href="https://support.huawei.com/enterprise/zh/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">《OceanStor Pacific系列 产品文档》</a> &gt; 配置 &gt; 文件服务基础业务配置指南 &gt; 配置基础业务（DPC场景） &gt; 客户端访问DPC共享 &gt; 步骤2。</p>
</td>
</tr>
<tr id="row1153312541506"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p528513563511"><a name="p528513563511"></a><a name="p528513563511"></a>mountOptions.aclonlyposix</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p328545655110"><a name="p328545655110"></a><a name="p328545655110"></a>DPC命名空间支持POSIX ACL功能，DPC客户端支持POSIX ACL的鉴权行为。</p>
<p id="p02851756105111"><a name="p02851756105111"></a><a name="p02851756105111"></a>支持POSIX ACL的协议有：DPC、NFSv3、HDFS。如使用NFSv4 ACL或NT ACL，会导致DPC客户端无法识别该类型的ACL，从而导致该类型的ACL不会生效。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p1428575617514"><a name="p1428575617514"></a><a name="p1428575617514"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p3285056145120"><a name="p3285056145120"></a><a name="p3285056145120"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p192851156145118"><a name="p192851156145118"></a><a name="p192851156145118"></a>aclonlyposix与acl参数同时使用时，仅acl参数生效，即命名空间支持ACL功能。</p>
</td>
</tr>
<tr id="row281161110"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1228513566515"><a name="p1228513566515"></a><a name="p1228513566515"></a>mountOptions.cnflush</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p52851756125115"><a name="p52851756125115"></a><a name="p52851756125115"></a>异步刷盘模式，即关闭命名空间下的文件时不会立即刷盘。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p12854568514"><a name="p12854568514"></a><a name="p12854568514"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p9285956175117"><a name="p9285956175117"></a><a name="p9285956175117"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p228575614518"><a name="p228575614518"></a><a name="p228575614518"></a>异步刷盘模式，当文件关闭时不会同步将Cache的数据持久化到存储介质中，而是通过Cache异步刷盘的方式将数据写入存储介质，Cache的后台刷盘将在写业务完成后根据刷盘周期定时刷盘。在多客户端场景下，对同一文件进行并行操作，文件Size的更新会受刷盘周期的影响，即当刷盘动作完成后才会更新文件的Size，更新通常会在数秒内完成。同步I/O不受刷盘周期影响。</p>
</td>
</tr>
<tr id="row177671317113"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p22851456185117"><a name="p22851456185117"></a><a name="p22851456185117"></a>mountOptions.cflush</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p18285656115120"><a name="p18285656115120"></a><a name="p18285656115120"></a>同步刷盘模式，即关闭命名空间下的文件时立即刷盘。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p528515645111"><a name="p528515645111"></a><a name="p528515645111"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p528545655118"><a name="p528545655118"></a><a name="p528545655118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p8285185695115"><a name="p8285185695115"></a><a name="p8285185695115"></a>默认使用同步刷盘模式。</p>
</td>
</tr>
</tbody>
</table>

**表 3**  支持的QoS配置

<a name="table74841513116"></a>
<table><thead align="left"><tr id="row74844518118"><th class="cellrowborder" valign="top" width="17.7%" id="mcps1.2.4.1.1"><p id="p1643904313015"><a name="p1643904313015"></a><a name="p1643904313015"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="30.17%" id="mcps1.2.4.1.2"><p id="p164391543143020"><a name="p164391543143020"></a><a name="p164391543143020"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="52.129999999999995%" id="mcps1.2.4.1.3"><p id="p34393439301"><a name="p34393439301"></a><a name="p34393439301"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row3455115971517"><td class="cellrowborder" valign="top" width="17.7%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0273440106_p743994313307"><a name="zh-cn_topic_0273440106_p743994313307"></a><a name="zh-cn_topic_0273440106_p743994313307"></a>maxMBPS</p>
</td>
<td class="cellrowborder" valign="top" width="30.17%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0273440106_p7439243173012"><a name="zh-cn_topic_0273440106_p7439243173012"></a><a name="zh-cn_topic_0273440106_p7439243173012"></a>最大带宽限制策略。</p>
</td>
<td class="cellrowborder" valign="top" width="52.129999999999995%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0273440106_p184391143133017"><a name="zh-cn_topic_0273440106_p184391143133017"></a><a name="zh-cn_topic_0273440106_p184391143133017"></a>必填。有效值为大于0的整数，单位MB/s。最大值请参考存储设备实际限制，如OceanStor Pacific NAS最大值为1073741824。</p>
</td>
</tr>
<tr id="row545565991517"><td class="cellrowborder" valign="top" width="17.7%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0273440106_p184399439309"><a name="zh-cn_topic_0273440106_p184399439309"></a><a name="zh-cn_topic_0273440106_p184399439309"></a><span>maxIOPS</span></p>
</td>
<td class="cellrowborder" valign="top" width="30.17%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0273440106_p1943913439308"><a name="zh-cn_topic_0273440106_p1943913439308"></a><a name="zh-cn_topic_0273440106_p1943913439308"></a>最大IOPS限制策略。</p>
</td>
<td class="cellrowborder" valign="top" width="52.129999999999995%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0273440106_p14439114315304"><a name="zh-cn_topic_0273440106_p14439114315304"></a><a name="zh-cn_topic_0273440106_p14439114315304"></a>必填。有效值为大于0的整数。最大值请参考存储设备实际限制，如OceanStor Pacific NAS最大值为1073741824000。</p>
</td>
</tr>
</tbody>
</table>

**表 4**  支持的配额配置

<a name="table2083974632312"></a>
<table><thead align="left"><tr id="row68394463230"><th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0000001218368853_p1643904313015"><a name="zh-cn_topic_0000001218368853_p1643904313015"></a><a name="zh-cn_topic_0000001218368853_p1643904313015"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0000001218368853_p164391543143020"><a name="zh-cn_topic_0000001218368853_p164391543143020"></a><a name="zh-cn_topic_0000001218368853_p164391543143020"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0000001218368853_p34393439301"><a name="zh-cn_topic_0000001218368853_p34393439301"></a><a name="zh-cn_topic_0000001218368853_p34393439301"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row58391646142313"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001218368853_p10540642195814"><a name="zh-cn_topic_0000001218368853_p10540642195814"></a><a name="zh-cn_topic_0000001218368853_p10540642195814"></a>spaceQuota</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001218368853_p7439243173012"><a name="zh-cn_topic_0000001218368853_p7439243173012"></a><a name="zh-cn_topic_0000001218368853_p7439243173012"></a>文件配额类型。</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001218368853_p184391143133017"><a name="zh-cn_topic_0000001218368853_p184391143133017"></a><a name="zh-cn_topic_0000001218368853_p184391143133017"></a>必选。仅支持配置<span class="parmvalue" id="zh-cn_topic_0000001218368853_parmvalue6901424105917"><a name="zh-cn_topic_0000001218368853_parmvalue6901424105917"></a><a name="zh-cn_topic_0000001218368853_parmvalue6901424105917"></a>“softQuota”</span>或者<span class="parmvalue" id="zh-cn_topic_0000001218368853_parmvalue1265010297596"><a name="zh-cn_topic_0000001218368853_parmvalue1265010297596"></a><a name="zh-cn_topic_0000001218368853_parmvalue1265010297596"></a>“hardQuota”</span>。</p>
</td>
</tr>
<tr id="row13839124642310"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001218368853_p184399439309"><a name="zh-cn_topic_0000001218368853_p184399439309"></a><a name="zh-cn_topic_0000001218368853_p184399439309"></a>gracePeriod</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001218368853_p1943913439308"><a name="zh-cn_topic_0000001218368853_p1943913439308"></a><a name="zh-cn_topic_0000001218368853_p1943913439308"></a>配置软配额时，允许的超限天数。</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001218368853_p1540512282024"><a name="zh-cn_topic_0000001218368853_p1540512282024"></a><a name="zh-cn_topic_0000001218368853_p1540512282024"></a>条件可选，当<span class="parmname" id="zh-cn_topic_0000001218368853_parmname5404162815213"><a name="zh-cn_topic_0000001218368853_parmname5404162815213"></a><a name="zh-cn_topic_0000001218368853_parmname5404162815213"></a>“spaceQuota”</span>配置为<span class="parmvalue" id="zh-cn_topic_0000001218368853_parmvalue74056285216"><a name="zh-cn_topic_0000001218368853_parmvalue74056285216"></a><a name="zh-cn_topic_0000001218368853_parmvalue74056285216"></a>“softQuota”</span>时可选。</p>
<p id="zh-cn_topic_0000001218368853_p14439114315304"><a name="zh-cn_topic_0000001218368853_p14439114315304"></a><a name="zh-cn_topic_0000001218368853_p14439114315304"></a>类型为整数，支持范围为0～4294967294。</p>
</td>
</tr>
</tbody>
</table>

