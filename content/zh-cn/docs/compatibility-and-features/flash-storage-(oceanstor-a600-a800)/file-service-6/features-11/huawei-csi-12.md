---
title: "华为CSI"
linkTitle: "华为CSI"
description: 
weight: 1
---

**表 1**  华为A系列存储支持的特性及约束

<a name="table14995183994515"></a>
<table><thead align="left"><tr id="row6996173914451"><th class="cellrowborder" valign="top" width="33.040000000000006%" id="mcps1.2.3.1.1"><p id="p199961439154519"><a name="p199961439154519"></a><a name="p199961439154519"></a>特性</p>
</th>
<th class="cellrowborder" valign="top" width="66.96%" id="mcps1.2.3.1.2"><p id="p1598210014585"><a name="p1598210014585"></a><a name="p1598210014585"></a>OceanStor A系列</p>
</th>
</tr>
</thead>
<tbody><tr id="row1899683984519"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p899653994514"><a name="p899653994514"></a><a name="p899653994514"></a><span>Static Provisioning</span></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><a name="ul563501712309"></a><a name="ul563501712309"></a><ul id="ul563501712309"><li>DataTurbo/NFS 3/4.0/4.1/4.2</li><li>仅支持单zone存储的本地文件系统</li></ul>
</td>
</tr>
<tr id="row49961039174517"><td class="cellrowborder" valign="top" headers="mcps1.2.3.1.1 "><p id="p9996173974516"><a name="p9996173974516"></a><a name="p9996173974516"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row55791517133218"><td class="cellrowborder" valign="top" headers="mcps1.2.3.1.1 "><p id="p3579151783219"><a name="p3579151783219"></a><a name="p3579151783219"></a>Manage Provisioning</p>
</td>
</tr>
<tr id="row8996539144513"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p49961939194517"><a name="p49961939194517"></a><a name="p49961939194517"></a><span>Expand Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p071645145119"><a name="p071645145119"></a><a name="p071645145119"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row14996173944518"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p280819372253"><a name="p280819372253"></a><a name="p280819372253"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p11273191454117"><a name="p11273191454117"></a><a name="p11273191454117"></a>不支持</p>
</td>
</tr>
<tr id="row1599693916456"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p49961939184516"><a name="p49961939184516"></a><a name="p49961939184516"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p79824055810"><a name="p79824055810"></a><a name="p79824055810"></a>不支持</p>
</td>
</tr>
<tr id="row15996173994516"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p15997133914455"><a name="p15997133914455"></a><a name="p15997133914455"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p174291031765"><a name="p174291031765"></a><a name="p174291031765"></a>不支持</p>
</td>
</tr>
<tr id="row19976393452"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p1799710394452"><a name="p1799710394452"></a><a name="p1799710394452"></a>Clone <span>Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p159231455612"><a name="p159231455612"></a><a name="p159231455612"></a>不支持</p>
</td>
</tr>
<tr id="row253813281571"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p105391828872"><a name="p105391828872"></a><a name="p105391828872"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p1102201017613"><a name="p1102201017613"></a><a name="p1102201017613"></a>不支持</p>
</td>
</tr>
<tr id="row76671821015"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p146673811105"><a name="p146673811105"></a><a name="p146673811105"></a>Topology</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p79826015584"><a name="p79826015584"></a><a name="p79826015584"></a>支持</p>
</td>
</tr>
<tr id="row91081351378"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p1423525343819"><a name="p1423525343819"></a><a name="p1423525343819"></a>Generic Ephemeral Volumes</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p14982170205819"><a name="p14982170205819"></a><a name="p14982170205819"></a>支持</p>
</td>
</tr>
<tr id="row59655172115"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p996591717110"><a name="p996591717110"></a><a name="p996591717110"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p69001214125219"><a name="p69001214125219"></a><a name="p69001214125219"></a><span>RWO/ROX/RWX/RWOP，</span><span>RWOP</span>需<span>Kubernetes 1.22</span>版本以上支持</p>
</td>
</tr>
<tr id="row4749123262619"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p274993211262"><a name="p274993211262"></a><a name="p274993211262"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p998300165818"><a name="p998300165818"></a><a name="p998300165818"></a>不支持</p>
</td>
</tr>
<tr id="row13606622132720"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p1760612292716"><a name="p1760612292716"></a><a name="p1760612292716"></a>应用类型</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p11983603587"><a name="p11983603587"></a><a name="p11983603587"></a>支持</p>
</td>
</tr>
<tr id="row17943182222817"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p79432225287"><a name="p79432225287"></a><a name="p79432225287"></a>卷双活</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p49831807585"><a name="p49831807585"></a><a name="p49831807585"></a>不支持</p>
</td>
</tr>
<tr id="row8191849183619"><td class="cellrowborder" valign="top" width="33.040000000000006%" headers="mcps1.2.3.1.1 "><p id="p81912491363"><a name="p81912491363"></a><a name="p81912491363"></a>存储多租户</p>
</td>
<td class="cellrowborder" valign="top" width="66.96%" headers="mcps1.2.3.1.2 "><p id="p49831014582"><a name="p49831014582"></a><a name="p49831014582"></a>不支持</p>
</td>
</tr>
</tbody>
</table>

**表 2**  华为A系列存储Dtree支持的特性

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
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p159mcpsimp"><a name="p159mcpsimp"></a><a name="p159mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row1283074261313"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p08311742201314"><a name="p08311742201314"></a><a name="p08311742201314"></a>Manage Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p1483184281313"><a name="p1483184281313"></a><a name="p1483184281313"></a>X</p>
</td>
</tr>
<tr id="row341412531489"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p162mcpsimp"><a name="p162mcpsimp"></a><a name="p162mcpsimp"></a><span>Expand Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p165mcpsimp"><a name="p165mcpsimp"></a><a name="p165mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row104141753384"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p168mcpsimp"><a name="p168mcpsimp"></a><a name="p168mcpsimp"></a>Access Mode</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p170mcpsimp"><a name="p170mcpsimp"></a><a name="p170mcpsimp"></a><span>√ （RWX/RWO/ROX/RWOP：RWOP需Kubernetes 1.22版本以上支持。）</span></p>
</td>
</tr>
<tr id="row7414145315813"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p174mcpsimp"><a name="p174mcpsimp"></a><a name="p174mcpsimp"></a>多租户</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p176mcpsimp"><a name="p176mcpsimp"></a><a name="p176mcpsimp"></a>X</p>
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

