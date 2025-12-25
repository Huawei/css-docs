---
title: "华为CSI"
linkTitle: "华为CSI"
description: 
weight: 1
---

**表 1**  华为存储支持的特性及约束

<a name="table175022559255"></a>
<table><thead align="left"><tr id="row250245510250"><th class="cellrowborder" valign="top" width="35.339999999999996%" id="mcps1.2.3.1.1"><p id="p10502355102510"><a name="p10502355102510"></a><a name="p10502355102510"></a>特性</p>
</th>
<th class="cellrowborder" valign="top" width="64.66%" id="mcps1.2.3.1.2"><p id="p150255532517"><a name="p150255532517"></a><a name="p150255532517"></a>OceanStor Pacific系列</p>
</th>
</tr>
</thead>
<tbody><tr id="row45029556254"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p1250235572516"><a name="p1250235572516"></a><a name="p1250235572516"></a><span>Static Provisioning</span></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><a name="ul20322165912442"></a><a name="ul20322165912442"></a><ul id="ul20322165912442"><li>DPC/NFS 3/4.1</li><li>仅8.1.2及以后版本支持DPC</li><li>仅8.1.2及以后版本支持NFS 4.1</li><li>仅8.2.0及以后版本支持NFS over RDMA，且使用NFS over RDMA时，仅支持NFS 3</li></ul>
</td>
</tr>
<tr id="row16502165517252"><td class="cellrowborder" valign="top" headers="mcps1.2.3.1.1 "><p id="p145026553256"><a name="p145026553256"></a><a name="p145026553256"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row247620119518"><td class="cellrowborder" valign="top" headers="mcps1.2.3.1.1 "><p id="p447601759"><a name="p447601759"></a><a name="p447601759"></a>Manage Provisioning</p>
</td>
</tr>
<tr id="row1050205518258"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p1650211552251"><a name="p1650211552251"></a><a name="p1650211552251"></a><span>Expand Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p10114173084218"><a name="p10114173084218"></a><a name="p10114173084218"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row1450218559251"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p150210556258"><a name="p150210556258"></a><a name="p150210556258"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p2011483094213"><a name="p2011483094213"></a><a name="p2011483094213"></a>不支持</p>
</td>
</tr>
<tr id="row205026554251"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p150235517255"><a name="p150235517255"></a><a name="p150235517255"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p17294191134320"><a name="p17294191134320"></a><a name="p17294191134320"></a>不支持</p>
</td>
</tr>
<tr id="row050219555257"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p550285513251"><a name="p550285513251"></a><a name="p550285513251"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p570871274311"><a name="p570871274311"></a><a name="p570871274311"></a>不支持</p>
</td>
</tr>
<tr id="row135028553252"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p65021755192513"><a name="p65021755192513"></a><a name="p65021755192513"></a>Clone <span>Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p3642192024311"><a name="p3642192024311"></a><a name="p3642192024311"></a>不支持</p>
</td>
</tr>
<tr id="row9502145510258"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p15022553257"><a name="p15022553257"></a><a name="p15022553257"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p6869724164319"><a name="p6869724164319"></a><a name="p6869724164319"></a>不支持</p>
</td>
</tr>
<tr id="row17502135542517"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p5502355172519"><a name="p5502355172519"></a><a name="p5502355172519"></a>Topology</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p155031155122514"><a name="p155031155122514"></a><a name="p155031155122514"></a>支持</p>
</td>
</tr>
<tr id="row795501615390"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p1250314558253"><a name="p1250314558253"></a><a name="p1250314558253"></a>Generic Ephemeral Inline Volumes</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p1503125510250"><a name="p1503125510250"></a><a name="p1503125510250"></a>支持</p>
</td>
</tr>
<tr id="row11503255132515"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p1150335519251"><a name="p1150335519251"></a><a name="p1150335519251"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p69001214125219"><a name="p69001214125219"></a><a name="p69001214125219"></a><span>RWO/ROX/RWX/RWOP，</span><span>RWOP</span>需<span>Kubernetes 1.22</span>版本以上支持</p>
</td>
</tr>
<tr id="row550395532512"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p1950375552517"><a name="p1950375552517"></a><a name="p1950375552517"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p8503855132516"><a name="p8503855132516"></a><a name="p8503855132516"></a>支持</p>
</td>
</tr>
<tr id="row950335510253"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p850315518253"><a name="p850315518253"></a><a name="p850315518253"></a>软硬配额</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p105891507518"><a name="p105891507518"></a><a name="p105891507518"></a>支持</p>
</td>
</tr>
<tr id="row7503185592511"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p3503185514257"><a name="p3503185514257"></a><a name="p3503185514257"></a>存储多租户</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p14871012588"><a name="p14871012588"></a><a name="p14871012588"></a>支持</p>
</td>
</tr>
</tbody>
</table>

**表 2**  华为分布式存储Dtree支持的特性

<a name="table17535153417812"></a>
<table><thead align="left"><tr id="row753517341082"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p1053517341819"><a name="p1053517341819"></a><a name="p1053517341819"></a>特性</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p453514341681"><a name="p453514341681"></a><a name="p453514341681"></a>支持情况</p>
</th>
</tr>
</thead>
<tbody><tr id="row1541413531981"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p151mcpsimp"><a name="p151mcpsimp"></a><a name="p151mcpsimp"></a><span>Static Provisioning</span></p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p154mcpsimp"><a name="p154mcpsimp"></a><a name="p154mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row241417531381"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p157mcpsimp"><a name="p157mcpsimp"></a><a name="p157mcpsimp"></a>Dynamic Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p159mcpsimp"><a name="p159mcpsimp"></a><a name="p159mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row1487435141420"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p148741052141"><a name="p148741052141"></a><a name="p148741052141"></a>Manage Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p17874257145"><a name="p17874257145"></a><a name="p17874257145"></a>X</p>
</td>
</tr>
<tr id="row341412531489"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p162mcpsimp"><a name="p162mcpsimp"></a><a name="p162mcpsimp"></a><span>Expand Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p165mcpsimp"><a name="p165mcpsimp"></a><a name="p165mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row104141753384"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p168mcpsimp"><a name="p168mcpsimp"></a><a name="p168mcpsimp"></a>Access Mode</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p170mcpsimp"><a name="p170mcpsimp"></a><a name="p170mcpsimp"></a><span>√ （RWX/RWO/ROX/RWOP：RWOP需Kubernetes 1.22版本以上支持。）</span></p>
</td>
</tr>
<tr id="row7414145315813"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p174mcpsimp"><a name="p174mcpsimp"></a><a name="p174mcpsimp"></a>多租户</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p176mcpsimp"><a name="p176mcpsimp"></a><a name="p176mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row1741418531812"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p179mcpsimp"><a name="p179mcpsimp"></a><a name="p179mcpsimp"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p181mcpsimp"><a name="p181mcpsimp"></a><a name="p181mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row124142534814"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p184mcpsimp"><a name="p184mcpsimp"></a><a name="p184mcpsimp"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p186mcpsimp"><a name="p186mcpsimp"></a><a name="p186mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row194141853587"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p189mcpsimp"><a name="p189mcpsimp"></a><a name="p189mcpsimp"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p191mcpsimp"><a name="p191mcpsimp"></a><a name="p191mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row2041411533814"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p194mcpsimp"><a name="p194mcpsimp"></a><a name="p194mcpsimp"></a>Clone <span>Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p197mcpsimp"><a name="p197mcpsimp"></a><a name="p197mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row1441414539814"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p200mcpsimp"><a name="p200mcpsimp"></a><a name="p200mcpsimp"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p202mcpsimp"><a name="p202mcpsimp"></a><a name="p202mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row04141953984"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p205mcpsimp"><a name="p205mcpsimp"></a><a name="p205mcpsimp"></a>卷双活</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p207mcpsimp"><a name="p207mcpsimp"></a><a name="p207mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row84129531881"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p210mcpsimp"><a name="p210mcpsimp"></a><a name="p210mcpsimp"></a>应用类型</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p212mcpsimp"><a name="p212mcpsimp"></a><a name="p212mcpsimp"></a>X</p>
</td>
</tr>
</tbody>
</table>

