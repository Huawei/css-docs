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
<th class="cellrowborder" valign="top" width="64.66%" id="mcps1.2.3.1.2"><p id="p202787402488"><a name="p202787402488"></a><a name="p202787402488"></a>OceanDisk 1500T</p>
</th>
</tr>
</thead>
<tbody><tr id="row45029556254"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p1250235572516"><a name="p1250235572516"></a><a name="p1250235572516"></a><span>Static Provisioning</span></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p136811144154810"><a name="p136811144154810"></a><a name="p136811144154810"></a>NFS 3/4.0</p>
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
<tr id="row950335510253"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p850315518253"><a name="p850315518253"></a><a name="p850315518253"></a>应用类型</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p1934555034816"><a name="p1934555034816"></a><a name="p1934555034816"></a>支持</p>
</td>
</tr>
<tr id="row7503185592511"><td class="cellrowborder" valign="top" width="35.339999999999996%" headers="mcps1.2.3.1.1 "><p id="p3503185514257"><a name="p3503185514257"></a><a name="p3503185514257"></a>存储多租户</p>
</td>
<td class="cellrowborder" valign="top" width="64.66%" headers="mcps1.2.3.1.2 "><p id="p14871012588"><a name="p14871012588"></a><a name="p14871012588"></a>支持</p>
</td>
</tr>
</tbody>
</table>

