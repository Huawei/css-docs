---
title: "Huawei CSI"
linkTitle: "Huawei CSI"
description: 
weight: 1
---

<a name="table175022559255"></a>
<table><thead align="left"><tr id="row250245510250"><th class="cellrowborder" valign="top" width="31.96%" id="mcps1.1.4.1.1"><p id="p10502355102510"><a name="p10502355102510"></a><a name="p10502355102510"></a>Feature</p>
</th>
<th class="cellrowborder" valign="top" width="32.62%" id="mcps1.1.4.1.2"><p id="p7502455182516"><a name="p7502455182516"></a><a name="p7502455182516"></a>FusionStorage Block</p>
</th>
<th class="cellrowborder" valign="top" width="35.42%" id="mcps1.1.4.1.3"><p id="p150255532517"><a name="p150255532517"></a><a name="p150255532517"></a>OceanStor Pacific Series</p>
</th>
</tr>
</thead>
<tbody><tr id="row45029556254"><td class="cellrowborder" valign="top" width="31.96%" headers="mcps1.1.4.1.1 "><p id="p1250235572516"><a name="p1250235572516"></a><a name="p1250235572516"></a>Static Provisioning</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="32.62%" headers="mcps1.1.4.1.2 "><p id="p10502055182512"><a name="p10502055182512"></a><a name="p10502055182512"></a>iSCSI/SCSI</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="35.42%" headers="mcps1.1.4.1.3 "><p id="p1550235510250"><a name="p1550235510250"></a><a name="p1550235510250"></a>iSCSI/SCSI</p>
</td>
</tr>
<tr id="row16502165517252"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p145026553256"><a name="p145026553256"></a><a name="p145026553256"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row247620119518"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p447601759"><a name="p447601759"></a><a name="p447601759"></a>Manage Provisioning</p>
</td>
</tr>
<tr id="row1050205518258"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p1650211552251"><a name="p1650211552251"></a><a name="p1650211552251"></a>Expand Persistent Volume</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><a name="ul423017233577"></a><a name="ul423017233577"></a><ul id="ul423017233577"><li>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</li><li>The provisioned PVC whose <strong id="b1541938242114624"><a name="b1541938242114624"></a><a name="b1541938242114624"></a>volumeType</strong> is <strong id="b501600776114624"><a name="b501600776114624"></a><a name="b501600776114624"></a>lun</strong> and <strong id="b1485115715114624"><a name="b1485115715114624"></a><a name="b1485115715114624"></a>accessModes</strong> is <strong id="b2063803334114624"><a name="b2063803334114624"></a><a name="b2063803334114624"></a>ReadOnlyMany</strong> does not support capacity expansion.</li></ul>
</td>
</tr>
<tr id="row1450218559251"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p150210556258"><a name="p150210556258"></a><a name="p150210556258"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p1799618394459"><a name="p1799618394459"></a><a name="p1799618394459"></a>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
</tr>
<tr id="row205026554251"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p150235517255"><a name="p150235517255"></a><a name="p150235517255"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p150235542511"><a name="p150235542511"></a><a name="p150235542511"></a>Supported</p>
</td>
</tr>
<tr id="row050219555257"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p550285513251"><a name="p550285513251"></a><a name="p550285513251"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p450275592511"><a name="p450275592511"></a><a name="p450275592511"></a>Supported</p>
</td>
</tr>
<tr id="row135028553252"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p65021755192513"><a name="p65021755192513"></a><a name="p65021755192513"></a>Clone Persistent Volume</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p114410410618"><a name="p114410410618"></a><a name="p114410410618"></a>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
</tr>
<tr id="row9502145510258"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p15022553257"><a name="p15022553257"></a><a name="p15022553257"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p550255512257"><a name="p550255512257"></a><a name="p550255512257"></a>Supported</p>
</td>
</tr>
<tr id="row17502135542517"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p5502355172519"><a name="p5502355172519"></a><a name="p5502355172519"></a>Topology</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p65038550258"><a name="p65038550258"></a><a name="p65038550258"></a>Supported</p>
</td>
</tr>
<tr id="row795501615390"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p1250314558253"><a name="p1250314558253"></a><a name="p1250314558253"></a>Generic Ephemeral Inline Volumes</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p1503195532514"><a name="p1503195532514"></a><a name="p1503195532514"></a>Supported</p>
</td>
</tr>
<tr id="row11503255132515"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p1150335519251"><a name="p1150335519251"></a><a name="p1150335519251"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p11965017181111"><a name="p11965017181111"></a><a name="p11965017181111"></a>RWO/ROX/RWOP: supported by all types of volumes. RWOP is supported only by Kubernetes 1.22 and later versions.</p>
<p id="p1241355910226"><a name="p1241355910226"></a><a name="p1241355910226"></a>RWX: supported only by Raw Block volumes.</p>
</td>
</tr>
<tr id="row550395532512"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p1950375552517"><a name="p1950375552517"></a><a name="p1950375552517"></a>QoS</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p350312554251"><a name="p350312554251"></a><a name="p350312554251"></a>Supported</p>
</td>
</tr>
<tr id="row950335510253"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p850315518253"><a name="p850315518253"></a><a name="p850315518253"></a>Soft and hard quotas</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p850319558258"><a name="p850319558258"></a><a name="p850319558258"></a>Not supported</p>
</td>
</tr>
<tr id="row7503185592511"><td class="cellrowborder" valign="top" headers="mcps1.1.4.1.1 "><p id="p3503185514257"><a name="p3503185514257"></a><a name="p3503185514257"></a>Storage multi-tenant</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.1.4.1.2 mcps1.1.4.1.3 "><p id="p453141013615"><a name="p453141013615"></a><a name="p453141013615"></a>Not supported</p>
</td>
</tr>
</tbody>
</table>

