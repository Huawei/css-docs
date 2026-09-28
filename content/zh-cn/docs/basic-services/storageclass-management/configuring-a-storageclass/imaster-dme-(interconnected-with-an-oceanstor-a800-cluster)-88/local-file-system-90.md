---
title: "本地文件系统"
linkTitle: "本地文件系统"
description: 
weight: 2
---

## 创建存储类{#section4456164612616}

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

## KVCache配置示例{#section1826982521216}

当容器使用KVCache对接iMaster DME本地文件系统，且存储支持KVCache功能时，可以参考如下配置示例。

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: kvcache-nas-sc
provisioner: csi.huawei.com
reclaimPolicy: Delete
parameters:
  backend: dme-a800-backend
  pool: StoragePool001
  zoneVstoreName: System_vstore
  volumeType: fs
  enableKVCache: "true"
  enableTimeAwareGc: "true"
  gcTimeThreshold: "30"
  disableVerifyCapacity: "true"
mountOptions:
  - nfsvers=3 # NFS挂载时指定版本为3
```

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
<tbody><tr id="zh-cn_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p7351266291"><a name="p7351266291"></a><a name="p7351266291"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p5351186152912"><a name="p5351186152912"></a><a name="p5351186152912"></a>自定义的 StorageClass 对象名称</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1135114692910"><a name="p1135114692910"></a><a name="p1135114692910"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p15351176122912"><a name="p15351176122912"></a><a name="p15351176122912"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1135136112914"><a name="p1135136112914"></a><a name="p1135136112914"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p193511568294"><a name="p193511568294"></a><a name="p193511568294"></a>以 Kubernetes v1.22.1 为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p2351136152918"><a name="p2351136152918"></a><a name="p2351136152918"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p6351465291"><a name="p6351465291"></a><a name="p6351465291"></a>制备器名称</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1435186202914"><a name="p1435186202914"></a><a name="p1435186202914"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p8351465293"><a name="p8351465293"></a><a name="p8351465293"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1035117620294"><a name="p1035117620294"></a><a name="p1035117620294"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p13511632912"><a name="p13511632912"></a><a name="p13511632912"></a>该字段需要指定为安装华为 CSI 时设置的驱动名称。取值和 values.yaml 文件中 driverName 一致</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p163519610297"><a name="p163519610297"></a><a name="p163519610297"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p73511060291"><a name="p73511060291"></a><a name="p73511060291"></a>回收策略。支持如下类型：Delete：自动回收资源；Retain：手动回收资源</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p16351866298"><a name="p16351866298"></a><a name="p16351866298"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p43515622918"><a name="p43515622918"></a><a name="p43515622918"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1735111622915"><a name="p1735111622915"></a><a name="p1735111622915"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p7351126132915"><a name="p7351126132915"></a><a name="p7351126132915"></a>Delete：删除 PV/PVC 时会关联删除存储上的资源。Retain：删除 PV/PVC 时不会删除存储上的资源。注意！删除 KVCache 资源会连同文件系统共享一起删除</p>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p635186112917"><a name="p635186112917"></a><a name="p635186112917"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p83519614299"><a name="p83519614299"></a><a name="p83519614299"></a>是否允许卷扩展。参数设置为 true 时，使用该 StorageClass 的 PV 可以进行扩容操作</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p235115672910"><a name="p235115672910"></a><a name="p235115672910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1135196102918"><a name="p1135196102918"></a><a name="p1135196102918"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p73513642910"><a name="p73513642910"></a><a name="p73513642910"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p12351769299"><a name="p12351769299"></a><a name="p12351769299"></a>此功能仅可用于扩容 PV，不能用于缩容 PV</p>
</td>
</tr>
<tr id="row63343268297"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1635176112913"><a name="p1635176112913"></a><a name="p1635176112913"></a>mountOptions</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p135113610291"><a name="p135113610291"></a><a name="p135113610291"></a>挂载参数列表，可用于指定主机执行 mount 命令时 -o 选项的参数</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1435114612910"><a name="p1435114612910"></a><a name="p1435114612910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p635119610294"><a name="p635119610294"></a><a name="p635119610294"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p103515672915"><a name="p103515672915"></a><a name="p103515672915"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1936045445914"><a name="p1936045445914"></a><a name="p1936045445914"></a>常见的mountOptions参数参考<a href="#table65545557506">表2</a>。</p>
<p id="p14360854175917"><a name="p14360854175917"></a><a name="p14360854175917"></a>也可自行指定其他挂载参数。</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p17351061291"><a name="p17351061291"></a><a name="p17351061291"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p835114612912"><a name="p835114612912"></a><a name="p835114612912"></a>待创建资源所在的后端名称。如果设置 parameters.pool，则必须设置本字段</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p135220682919"><a name="p135220682919"></a><a name="p135220682919"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p535216642917"><a name="p535216642917"></a><a name="p535216642917"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p835246142911"><a name="p835246142911"></a><a name="p835246142911"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1635216192917"><a name="p1635216192917"></a><a name="p1635216192917"></a>当前iMaster DME本地文件系统创建KVCache场景下，需要指定使用的backend。</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1735296182915"><a name="p1735296182915"></a><a name="p1735296182915"></a>parameters.pool</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1235214611293"><a name="p1235214611293"></a><a name="p1235214611293"></a>待创建资源所在的存储资源池名称</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p335215602910"><a name="p335215602910"></a><a name="p335215602910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p635206172918"><a name="p635206172918"></a><a name="p635206172918"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p535246162914"><a name="p535246162914"></a><a name="p535246162914"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p133521965295"><a name="p133521965295"></a><a name="p133521965295"></a>如果不设置，华为 CSI 会在所选后端上选择一个剩余容量最大的存储池创建资源。建议指定存储池，确保创建的资源在预期的存储池上</p>
</td>
</tr>
<tr id="row12968565337"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p148909442443"><a name="p148909442443"></a><a name="p148909442443"></a>parameters.zoneVstoreName</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p8890244174410"><a name="p8890244174410"></a><a name="p8890244174410"></a>存储设备的租户名。</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p138909443445"><a name="p138909443445"></a><a name="p138909443445"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p9890154416446"><a name="p9890154416446"></a><a name="p9890154416446"></a>System_vStore</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p849004934413"><a name="p849004934413"></a><a name="p849004934413"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p166922509449"><a name="p166922509449"></a><a name="p166922509449"></a>仅在填入zoneSN场景下生效。在iMaster DME管理界面，选择"基础设施 &gt; 存储设备 &gt;系统 &gt; 租户"。获取对应zone下的非全局租户名称。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p203528613295"><a name="p203528613295"></a><a name="p203528613295"></a>parameters.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p035210642914"><a name="p035210642914"></a><a name="p035210642914"></a>指定动态卷供应创建的存储资源名称。支持配置占位符对存储资源名称进行自定义，支持的占位符如下：PVC 命名空间：{{ .PVCNamespace }}；PVC 名称：{{ .PVCName }}</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p113526662911"><a name="p113526662911"></a><a name="p113526662911"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p43524612299"><a name="p43524612299"></a><a name="p43524612299"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p7352106142918"><a name="p7352106142918"></a><a name="p7352106142918"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p03524662910"><a name="p03524662910"></a><a name="p03524662910"></a>支持配置字母、数字、"_"、"-"，不能配置为空，生成的存储资源名称长度范围是 1-255。必须同时配置 PVC 命名空间和 PVC 名称。为了避免资源名称重复，会将 PVC UID 作为唯一标识符默认添加到名称末尾</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p11856152785018"><a name="p11856152785018"></a><a name="p11856152785018"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p198561027135014"><a name="p198561027135014"></a><a name="p198561027135014"></a>待创建卷类型。支持如下类型：</p>
<a name="ul8856102725020"></a><a name="ul8856102725020"></a><ul id="ul8856102725020"><li>lun：存储侧发放的资源是LUN。</li><li>fs：存储侧发放的资源是文件系统。</li><li>dtree：存储侧发放的资源是Dtree类型的卷</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p14856327155015"><a name="p14856327155015"></a><a name="p14856327155015"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p19856627135013"><a name="p19856627135013"></a><a name="p19856627135013"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1785612755013"><a name="p1785612755013"></a><a name="p1785612755013"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p208561927135012"><a name="p208561927135012"></a><a name="p208561927135012"></a>使用文件业务必须配置为fs。</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14352176102917"><a name="p14352176102917"></a><a name="p14352176102917"></a>parameters.disableVerifyCapacity</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p135216662913"><a name="p135216662913"></a><a name="p135216662913"></a>是否禁用卷容量校验，禁用后将不校验卷容量是否为扇区大小整数倍。可选值："true"：禁用卷容量校验；"false"：开启卷容量校验。使用 Red Hat OpenShift Virtualization 对接 CSI 时，该参数必须设置为 "true"</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p235211611296"><a name="p235211611296"></a><a name="p235211611296"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p133524615295"><a name="p133524615295"></a><a name="p133524615295"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p10352116142916"><a name="p10352116142916"></a><a name="p10352116142916"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p10352069295"><a name="p10352069295"></a><a name="p10352069295"></a>OceanStor A 系列的扇区大小为 512 B</p>
</td>
</tr>
<tr id="row2531173517323"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p235216692919"><a name="p235216692919"></a><a name="p235216692919"></a>parameters.description</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1235256112912"><a name="p1235256112912"></a><a name="p1235256112912"></a>用于配置创建的文件系统的描述信息。参数类型：字符串；长度限制：1-255</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p53524613294"><a name="p53524613294"></a><a name="p53524613294"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p12352868299"><a name="p12352868299"></a><a name="p12352868299"></a>Created from Kubernetes CSI</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p133526622919"><a name="p133526622919"></a><a name="p133526622919"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p12352565293"><a name="p12352565293"></a><a name="p12352565293"></a>parameters.enableKVCache</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p035211611294"><a name="p035211611294"></a><a name="p035211611294"></a>是否创建 KVCache 库。"false"：关闭；"true"：开启</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p535219620294"><a name="p535219620294"></a><a name="p535219620294"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1935296122916"><a name="p1935296122916"></a><a name="p1935296122916"></a>"false"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p835217614298"><a name="p835217614298"></a><a name="p835217614298"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1035216122919"><a name="p1035216122919"></a><a name="p1035216122919"></a>当前场景创建单zone资源时必须配置为true</p>
</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p235212642913"><a name="p235212642913"></a><a name="p235212642913"></a>parameters.enableTimeAwareGc</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p11352965293"><a name="p11352965293"></a><a name="p11352965293"></a>是否启用 KVCache 主动清理。"false"：关闭；"true"：开启</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p4353361292"><a name="p4353361292"></a><a name="p4353361292"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p18353156162913"><a name="p18353156162913"></a><a name="p18353156162913"></a>"false"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p335356122917"><a name="p335356122917"></a><a name="p335356122917"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p335316672919"><a name="p335316672919"></a><a name="p335316672919"></a>无论配置为 "true" 还是 "false"，后台均会在记忆库容量不足时清理 KVCache；配置为 "true" 时，后台会清理过期的 KVCache</p>
</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p8353966294"><a name="p8353966294"></a><a name="p8353966294"></a>parameters.gcTimeThreshold</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p83531160297"><a name="p83531160297"></a><a name="p83531160297"></a>KVCache 过期时间，范围 1-3650 天。示例 "1"</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1353166132913"><a name="p1353166132913"></a><a name="p1353166132913"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p183533615290"><a name="p183533615290"></a><a name="p183533615290"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p17353156172910"><a name="p17353156172910"></a><a name="p17353156172910"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p113530692915"><a name="p113530692915"></a><a name="p113530692915"></a>当 parameters.enableTimeAwareGc 配置为 "true" 时，本参数必填</p>
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
</tbody>
</table>

