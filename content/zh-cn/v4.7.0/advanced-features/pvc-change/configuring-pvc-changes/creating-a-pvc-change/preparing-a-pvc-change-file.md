---
title: "准备PVC变更文件"
linkTitle: "准备PVC变更文件"
description: 
weight: 1
---

## PVC变更文件说明{#section45675517546}

PVC变更文件样例模板为/examples/volumemodifyclaim.yaml，具体配置项如下表所示：

**表 1**  参数说明

<a name="table882408155517"></a>
<table><thead align="left"><tr id="row1882418105518"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.1"><p id="p282412815559"><a name="p282412815559"></a><a name="p282412815559"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.2"><p id="p1682410825515"><a name="p1682410825515"></a><a name="p1682410825515"></a>描述</p>
</th>
<th class="cellrowborder" valign="top" width="7.64%" id="mcps1.2.6.1.3"><p id="p17824188185518"><a name="p17824188185518"></a><a name="p17824188185518"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="18.04%" id="mcps1.2.6.1.4"><p id="p16824148195513"><a name="p16824148195513"></a><a name="p16824148195513"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="34.32%" id="mcps1.2.6.1.5"><p id="p98241783553"><a name="p98241783553"></a><a name="p98241783553"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row282438175514"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p38247819556"><a name="p38247819556"></a><a name="p38247819556"></a>apiVersion</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001541071762_p0896194484915"><a name="zh-cn_topic_0000001541071762_p0896194484915"></a><a name="zh-cn_topic_0000001541071762_p0896194484915"></a>API组，string类型</p>
</td>
<td class="cellrowborder" valign="top" width="7.64%" headers="mcps1.2.6.1.3 "><p id="p8824178125515"><a name="p8824178125515"></a><a name="p8824178125515"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="18.04%" headers="mcps1.2.6.1.4 "><p id="p138247865515"><a name="p138247865515"></a><a name="p138247865515"></a>xuanwu.huawei.io/v1</p>
</td>
<td class="cellrowborder" valign="top" width="34.32%" headers="mcps1.2.6.1.5 "><p id="p982408115517"><a name="p982408115517"></a><a name="p982408115517"></a>固定填写xuanwu.huawei.io/v1</p>
</td>
</tr>
<tr id="row158241788556"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1382416825518"><a name="p1382416825518"></a><a name="p1382416825518"></a>kind</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p782438195513"><a name="p782438195513"></a><a name="p782438195513"></a>资源的类型，string类型</p>
</td>
<td class="cellrowborder" valign="top" width="7.64%" headers="mcps1.2.6.1.3 "><p id="p88244814556"><a name="p88244814556"></a><a name="p88244814556"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="18.04%" headers="mcps1.2.6.1.4 "><p id="p1782413819554"><a name="p1782413819554"></a><a name="p1782413819554"></a>VolumeModifyClaim</p>
</td>
<td class="cellrowborder" valign="top" width="34.32%" headers="mcps1.2.6.1.5 "><p id="p12824198115512"><a name="p12824198115512"></a><a name="p12824198115512"></a>固定填写VolumeModifyClaim</p>
</td>
</tr>
<tr id="row7824198185511"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1182488115510"><a name="p1182488115510"></a><a name="p1182488115510"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p188241387558"><a name="p188241387558"></a><a name="p188241387558"></a>集群资源对象的名称，string类型</p>
</td>
<td class="cellrowborder" valign="top" width="7.64%" headers="mcps1.2.6.1.3 "><p id="p5824684559"><a name="p5824684559"></a><a name="p5824684559"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="18.04%" headers="mcps1.2.6.1.4 "><p id="p1782413895514"><a name="p1782413895514"></a><a name="p1782413895514"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.32%" headers="mcps1.2.6.1.5 "><p id="p1482417805520"><a name="p1482417805520"></a><a name="p1482417805520"></a>名称必须满足<a href="https://kubernetes.io/zh-cn/docs/concepts/overview/working-with-objects/names#dns-subdomain-names" target="_blank" rel="noopener noreferrer">DNS 子域名</a>的命名规则，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以小写字母数字字符开头和结尾，最大长度不超过63个字符。</p>
<p id="p1890916560354"><a name="p1890916560354"></a><a name="p1890916560354"></a>注意：在PVC变更过程中，会对原StorageClass进行备份，备份StorageClass的名称为“<em id="i1932131117367"><a name="i1932131117367"></a><a name="i1932131117367"></a>&lt;原StorageClass名称&gt;&lt;VolumeModifyClaim名称&gt;</em>”，且需符合StorageClass命名规则。</p>
</td>
</tr>
<tr id="row1482498135514"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p18241589552"><a name="p18241589552"></a><a name="p18241589552"></a>spec.source.kind</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p13824158195519"><a name="p13824158195519"></a><a name="p13824158195519"></a>数据源类型，string类型</p>
</td>
<td class="cellrowborder" valign="top" width="7.64%" headers="mcps1.2.6.1.3 "><p id="p1082428125517"><a name="p1082428125517"></a><a name="p1082428125517"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="18.04%" headers="mcps1.2.6.1.4 "><p id="p982420825510"><a name="p982420825510"></a><a name="p982420825510"></a>StorageClass</p>
</td>
<td class="cellrowborder" valign="top" width="34.32%" headers="mcps1.2.6.1.5 "><p id="p138240835517"><a name="p138240835517"></a><a name="p138240835517"></a>仅支持设置为：StorageClass</p>
</td>
</tr>
<tr id="row1580118248311"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p48021124438"><a name="p48021124438"></a><a name="p48021124438"></a>spec.source.name</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p68021524930"><a name="p68021524930"></a><a name="p68021524930"></a>数据源名称，string类型</p>
</td>
<td class="cellrowborder" valign="top" width="7.64%" headers="mcps1.2.6.1.3 "><p id="p480210241835"><a name="p480210241835"></a><a name="p480210241835"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="18.04%" headers="mcps1.2.6.1.4 "><p id="p980213243314"><a name="p980213243314"></a><a name="p980213243314"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.32%" headers="mcps1.2.6.1.5 "><p id="p1380282420314"><a name="p1380282420314"></a><a name="p1380282420314"></a>仅支持设置StorageClass名称</p>
</td>
</tr>
<tr id="row19555112614317"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p0555826131"><a name="p0555826131"></a><a name="p0555826131"></a>spec.parameters.hyperMetro</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p145556261430"><a name="p145556261430"></a><a name="p145556261430"></a>是否将普通卷变更为双活卷。当前取值仅支持"true"。</p>
</td>
<td class="cellrowborder" valign="top" width="7.64%" headers="mcps1.2.6.1.3 "><p id="p205555261534"><a name="p205555261534"></a><a name="p205555261534"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="18.04%" headers="mcps1.2.6.1.4 "><p id="p1555926531"><a name="p1555926531"></a><a name="p1555926531"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.32%" headers="mcps1.2.6.1.5 "><p id="p465413911106"><a name="p465413911106"></a><a name="p465413911106"></a>仅支持主站点普通存储卷变更为双活存储卷。</p>
</td>
</tr>
<tr id="row141343508506"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p13134125010508"><a name="p13134125010508"></a><a name="p13134125010508"></a>spec.parameters.metroPairSyncSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p11242177125214"><a name="p11242177125214"></a><a name="p11242177125214"></a>双活Pair同步速率。支持配置为1~4。</p>
<p id="p1924214720529"><a name="p1924214720529"></a><a name="p1924214720529"></a>可选值：</p>
<a name="ul4215172125219"></a><a name="ul4215172125219"></a><ul id="ul4215172125219"><li>1：低</li><li>2：中</li><li>3：高</li><li>4：最高</li></ul>
</td>
<td class="cellrowborder" valign="top" width="7.64%" headers="mcps1.2.6.1.3 "><p id="p1413415016505"><a name="p1413415016505"></a><a name="p1413415016505"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="18.04%" headers="mcps1.2.6.1.4 "><p id="p113425015509"><a name="p113425015509"></a><a name="p113425015509"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.32%" headers="mcps1.2.6.1.5 "><p id="p1813405016505"><a name="p1813405016505"></a><a name="p1813405016505"></a>当且仅当spec.parameters.hyperMetro为"true"时生效。</p>
<p id="p688744685818"><a name="p688744685818"></a><a name="p688744685818"></a>注意：</p>
<a name="ul35821048175812"></a><a name="ul35821048175812"></a><ul id="ul35821048175812"><li>未配置该参数时，双活Pair存储速率由存储决定。</li><li>最高速率同步时可能导致主机时延增大。</li></ul>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>-   spec.source.kind和spec.source.name用于指定卷变更范围，例如配置为StorageClass和对应名称时，将会变更使用目标StorageClass发放的所有的处于Bound状态的PVC。
>-   当所有关联的PVC完成变更后，华为CSI会替换原有的StorageClass，并增加VolumeModifyClaim的spec.parameters参数，使得PVC满足StorageClass定义。

典型场景配置请参考如下示例：

## 变更普通卷为双活卷{#section637055131612}

配置变更普通卷为双活卷示例如下：

```yaml
apiVersion: xuanwu.huawei.io/v1
kind: VolumeModifyClaim
metadata:
  name: myvmc
spec:
  source:
    kind: StorageClass
    name: mysc
  parameters:
    hyperMetro: "true"
```

