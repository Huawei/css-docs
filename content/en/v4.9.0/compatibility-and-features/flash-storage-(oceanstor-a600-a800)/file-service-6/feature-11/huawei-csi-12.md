---
title: "Huawei CSI"
linkTitle: "Huawei CSI"
description: 
weight: 1
---

**Table  1**  Features supported by Huawei storage and constraints

<a name="table14995183994515"></a>
<table><thead align="left"><tr id="row6996173914451"><th class="cellrowborder" valign="top" width="33.040000000000006%" id="mcps1.2.3.1.1"><p id="p199961439154519"><a name="p199961439154519"></a><a name="p199961439154519"></a>Feature</p>
</th>
<th class="cellrowborder" valign="top" width="66.96%" id="mcps1.2.3.1.2"><p id="p1598210014585"><a name="p1598210014585"></a><a name="p1598210014585"></a>OceanStor A Series</p>
</th>
</tr>
</thead>
<tbody><tr id="row1899683984519"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p899653994514"><a name="p899653994514"></a><a name="p899653994514"></a>Static Provisioning</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><a name="ul563501712309"></a><a name="ul563501712309"></a><ul id="ul563501712309"><li>DataTurbo/NFS 3/4.0/4.1/4.2</li><li>Only local file systems of storage with a single zone are supported.</li></ul>
</td>
</tr>
<tr id="row49961039174517"><td class="cellrowborder" valign="top" headers="mcps1.2.3.1.1 "><p id="p9996173974516"><a name="p9996173974516"></a><a name="p9996173974516"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row55791517133218"><td class="cellrowborder" valign="top" headers="mcps1.2.3.1.1 "><p id="p3579151783219"><a name="p3579151783219"></a><a name="p3579151783219"></a>Manage Provisioning</p>
</td>
</tr>
<tr id="row8996539144513"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p49961939194517"><a name="p49961939194517"></a><a name="p49961939194517"></a>Expand Persistent Volume</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p071645145119"><a name="p071645145119"></a><a name="p071645145119"></a>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
</tr>
<tr id="row14996173944518"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p280819372253"><a name="p280819372253"></a><a name="p280819372253"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p11273191454117"><a name="p11273191454117"></a><a name="p11273191454117"></a>Not supported</p>
</td>
</tr>
<tr id="row1599693916456"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p49961939184516"><a name="p49961939184516"></a><a name="p49961939184516"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p79824055810"><a name="p79824055810"></a><a name="p79824055810"></a>Not supported</p>
</td>
</tr>
<tr id="row15996173994516"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p15997133914455"><a name="p15997133914455"></a><a name="p15997133914455"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p174291031765"><a name="p174291031765"></a><a name="p174291031765"></a>Not supported</p>
</td>
</tr>
<tr id="row19976393452"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p1799710394452"><a name="p1799710394452"></a><a name="p1799710394452"></a>Clone Persistent Volume</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p159231455612"><a name="p159231455612"></a><a name="p159231455612"></a>Not supported</p>
</td>
</tr>
<tr id="row253813281571"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p105391828872"><a name="p105391828872"></a><a name="p105391828872"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p1102201017613"><a name="p1102201017613"></a><a name="p1102201017613"></a>Not supported</p>
</td>
</tr>
<tr id="row76671821015"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p146673811105"><a name="p146673811105"></a><a name="p146673811105"></a>Topology</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p79826015584"><a name="p79826015584"></a><a name="p79826015584"></a>Supported</p>
</td>
</tr>
<tr id="row91081351378"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p1423525343819"><a name="p1423525343819"></a><a name="p1423525343819"></a>Generic Ephemeral Volumes</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p14982170205819"><a name="p14982170205819"></a><a name="p14982170205819"></a>Supported</p>
</td>
</tr>
<tr id="row59655172115"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p996591717110"><a name="p996591717110"></a><a name="p996591717110"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p69001214125219"><a name="p69001214125219"></a><a name="p69001214125219"></a>RWO, ROX, RWX, and RWOP. RWOP is supported only in Kubernetes 1.22 or later.</p>
</td>
</tr>
<tr id="row4749123262619"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p274993211262"><a name="p274993211262"></a><a name="p274993211262"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p998300165818"><a name="p998300165818"></a><a name="p998300165818"></a>Not supported</p>
</td>
</tr>
<tr id="row13606622132720"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p1760612292716"><a name="p1760612292716"></a><a name="p1760612292716"></a>Application type</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p11983603587"><a name="p11983603587"></a><a name="p11983603587"></a>Supported</p>
</td>
</tr>
<tr id="row17943182222817"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p79432225287"><a name="p79432225287"></a><a name="p79432225287"></a>Volume HyperMetro</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p49831807585"><a name="p49831807585"></a><a name="p49831807585"></a>Not supported</p>
</td>
</tr>
<tr id="row8191849183619"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p81912491363"><a name="p81912491363"></a><a name="p81912491363"></a>Storage multi-tenant</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p49831014582"><a name="p49831014582"></a><a name="p49831014582"></a>Not supported</p>
</td>
</tr>
</tbody>
</table>

