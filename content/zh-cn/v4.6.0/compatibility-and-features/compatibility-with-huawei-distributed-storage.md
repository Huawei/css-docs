---
title: "华为分布式存储兼容性"
linkTitle: "华为分布式存储兼容性"
description: 
weight: 4
---

华为CSI插件兼容华为OceanStor系列的分布式存储系统，具体支持的存储版本如下表所示：

## 支持的华为分布式存储{#section723118313717}

**表 1**  支持的华为分布式存储

<a name="table13501195552513"></a>
<table><thead align="left"><tr id="row17501175532518"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p5501555152518"><a name="p5501555152518"></a><a name="p5501555152518"></a>存储产品</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p250185516255"><a name="p250185516255"></a><a name="p250185516255"></a>版本</p>
</th>
</tr>
</thead>
<tbody><tr id="row350255517254"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="zh-cn_topic_0150885201_p283231353315"><a name="zh-cn_topic_0150885201_p283231353315"></a><a name="zh-cn_topic_0150885201_p283231353315"></a>FusionStorage Block</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="zh-cn_topic_0150885201_p1283201313319"><a name="zh-cn_topic_0150885201_p1283201313319"></a><a name="zh-cn_topic_0150885201_p1283201313319"></a>8.0.1</p>
</td>
</tr>
<tr id="row16502155513258"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="zh-cn_topic_0150885201_p467542723319"><a name="zh-cn_topic_0150885201_p467542723319"></a><a name="zh-cn_topic_0150885201_p467542723319"></a>OceanStor Pacific系列</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="zh-cn_topic_0150885201_p146755279338"><a name="zh-cn_topic_0150885201_p146755279338"></a><a name="zh-cn_topic_0150885201_p146755279338"></a>8.1.0, 8.1.1, 8.1.2, 8.1.3, 8.1.5, 8.2.0</p>
</td>
</tr>
</tbody>
</table>

## 华为分布式存储支持的特性{#section14115311203711}

华为CSI插件针对华为分布式存储支持如下特性。

**表 2**  华为分布式存储支持的特性及约束

<a name="table175022559255"></a>
<table><thead align="left"><tr id="row250245510250"><th class="cellrowborder" valign="top" width="21.95%" id="mcps1.2.4.1.1"><p id="p10502355102510"><a name="p10502355102510"></a><a name="p10502355102510"></a>特性</p>
</th>
<th class="cellrowborder" valign="top" width="42.449999999999996%" id="mcps1.2.4.1.2"><p id="p7502455182516"><a name="p7502455182516"></a><a name="p7502455182516"></a>FusionStorage Block</p>
</th>
<th class="cellrowborder" valign="top" width="35.6%" id="mcps1.2.4.1.3"><p id="p150255532517"><a name="p150255532517"></a><a name="p150255532517"></a>OceanStor Pacific系列</p>
</th>
</tr>
</thead>
<tbody><tr id="row45029556254"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p1250235572516"><a name="p1250235572516"></a><a name="p1250235572516"></a><span>Static Provisioning</span></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p10502055182512"><a name="p10502055182512"></a><a name="p10502055182512"></a>SAN：iSCSI/SCSI</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p1550235510250"><a name="p1550235510250"></a><a name="p1550235510250"></a>SAN：iSCSI/SCSI</p>
<p id="p1155184451813"><a name="p1155184451813"></a><a name="p1155184451813"></a>NAS：DPC<sup id="sup03431118543"><a name="sup03431118543"></a><a name="sup03431118543"></a>2</sup>/NFS 3/4.1<sup id="sup592411910418"><a name="sup592411910418"></a><a name="sup592411910418"></a>3</sup></p>
</td>
</tr>
<tr id="row16502165517252"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p145026553256"><a name="p145026553256"></a><a name="p145026553256"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row247620119518"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p447601759"><a name="p447601759"></a><a name="p447601759"></a>Manage Provisioning<sup id="sup25964561381"><a name="sup25964561381"></a><a name="sup25964561381"></a>1</sup></p>
</td>
</tr>
<tr id="row1050205518258"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p1650211552251"><a name="p1650211552251"></a><a name="p1650211552251"></a><span>Expand Persistent Volume</span><sup id="sup99731871303"><a name="sup99731871303"></a><a name="sup99731871303"></a>4</sup></p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.4.1.2 mcps1.2.4.1.3 "><p id="p3160102971819"><a name="p3160102971819"></a><a name="p3160102971819"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row1450218559251"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p150210556258"><a name="p150210556258"></a><a name="p150210556258"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.4.1.2 mcps1.2.4.1.3 "><p id="p1799618394459"><a name="p1799618394459"></a><a name="p1799618394459"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的SAN类型卷</p>
</td>
</tr>
<tr id="row205026554251"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p150235517255"><a name="p150235517255"></a><a name="p150235517255"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p150235542511"><a name="p150235542511"></a><a name="p150235542511"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p1616113011918"><a name="p1616113011918"></a><a name="p1616113011918"></a>仅支持SAN类型的卷快照</p>
</td>
</tr>
<tr id="row050219555257"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p550285513251"><a name="p550285513251"></a><a name="p550285513251"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p450275592511"><a name="p450275592511"></a><a name="p450275592511"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p1016012981815"><a name="p1016012981815"></a><a name="p1016012981815"></a>仅支持SAN类型的卷快照</p>
</td>
</tr>
<tr id="row135028553252"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p65021755192513"><a name="p65021755192513"></a><a name="p65021755192513"></a>Clone <span>Persistent Volume</span></p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.4.1.2 mcps1.2.4.1.3 "><p id="p114410410618"><a name="p114410410618"></a><a name="p114410410618"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的SAN类型卷</p>
</td>
</tr>
<tr id="row9502145510258"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p15022553257"><a name="p15022553257"></a><a name="p15022553257"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p550255512257"><a name="p550255512257"></a><a name="p550255512257"></a>仅支持SAN类型的卷</p>
</td>
<td class="cellrowborder" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p15502135513255"><a name="p15502135513255"></a><a name="p15502135513255"></a>仅支持SAN类型的卷</p>
</td>
</tr>
<tr id="row17502135542517"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p5502355172519"><a name="p5502355172519"></a><a name="p5502355172519"></a>Topology</p>
</td>
<td class="cellrowborder" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p65038550258"><a name="p65038550258"></a><a name="p65038550258"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p155031155122514"><a name="p155031155122514"></a><a name="p155031155122514"></a>支持</p>
</td>
</tr>
<tr id="row795501615390"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p1250314558253"><a name="p1250314558253"></a><a name="p1250314558253"></a>Generic Ephemeral Inline Volumes</p>
</td>
<td class="cellrowborder" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p1503195532514"><a name="p1503195532514"></a><a name="p1503195532514"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p1503125510250"><a name="p1503125510250"></a><a name="p1503125510250"></a>支持</p>
</td>
</tr>
<tr id="row11503255132515"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="p1150335519251"><a name="p1150335519251"></a><a name="p1150335519251"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.4.1.2 mcps1.2.4.1.3 "><p id="p11965017181111"><a name="p11965017181111"></a><a name="p11965017181111"></a><span>RWO/ROX/RWOP：</span>所有类型卷均支持，<span>RWOP在</span><span>Kubernetes 1.22及以上</span>版本支持。</p>
<p id="p1241355910226"><a name="p1241355910226"></a><a name="p1241355910226"></a><span>RWX</span>：仅Raw Block卷和NFS类型的卷支持。</p>
</td>
</tr>
<tr id="row550395532512"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p1950375552517"><a name="p1950375552517"></a><a name="p1950375552517"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p350312554251"><a name="p350312554251"></a><a name="p350312554251"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p8503855132516"><a name="p8503855132516"></a><a name="p8503855132516"></a>支持</p>
</td>
</tr>
<tr id="row950335510253"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p850315518253"><a name="p850315518253"></a><a name="p850315518253"></a>软硬配额</p>
</td>
<td class="cellrowborder" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p850319558258"><a name="p850319558258"></a><a name="p850319558258"></a>不支持</p>
</td>
<td class="cellrowborder" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p105891507518"><a name="p105891507518"></a><a name="p105891507518"></a>仅支持NAS类型的卷</p>
</td>
</tr>
<tr id="row7503185592511"><td class="cellrowborder" valign="top" width="21.95%" headers="mcps1.2.4.1.1 "><p id="p3503185514257"><a name="p3503185514257"></a><a name="p3503185514257"></a>存储多租户</p>
</td>
<td class="cellrowborder" valign="top" width="42.449999999999996%" headers="mcps1.2.4.1.2 "><p id="p453141013615"><a name="p453141013615"></a><a name="p453141013615"></a>不支持</p>
</td>
<td class="cellrowborder" valign="top" width="35.6%" headers="mcps1.2.4.1.3 "><p id="p14871012588"><a name="p14871012588"></a><a name="p14871012588"></a>仅支持NAS类型的卷</p>
</td>
</tr>
</tbody>
</table>

-   注释1 Manage Provisioning是华为CSI自定义的纳管卷特性，该特性支持将已有存储资源纳管至Kubernetes。不允许将一个存储资源纳管多次和针对同一个存储资源进行并发删除/创建操作。
-   注释2 仅OceanStor Pacific系列 8.1.2及以后版本支持DPC。使用DPC时操作系统需同时满足[华为CSI支持的操作系统](/docs/compatibility-and-features/kubernetes-and-os-compatibility#table133422378818)和OceanStor Pacific系列兼容性中DPC基本连通性支持的操作系统。
-   注释3 仅OceanStor Pacific系列 8.1.2及以后版本支持NFS 4.1。OceanStor Pacific系列 8.2.0及以后版本支持NFS over RDMA，且使用NFS over RDMA时，仅支持NFS 3。
-   注释4 发放的volumeType为lun且accessModes为ReadOnlyMany的PVC不支持扩容。

