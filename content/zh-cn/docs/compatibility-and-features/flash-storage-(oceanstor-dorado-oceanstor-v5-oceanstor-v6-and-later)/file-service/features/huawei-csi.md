---
title: "华为CSI"
linkTitle: "华为CSI"
description: 
weight: 1
---

**表 1**  华为存储支持的特性及约束

<a name="table14995183994515"></a>
<table><thead align="left"><tr id="row6996173914451"><th class="cellrowborder" valign="top" width="21.36%" id="mcps1.2.5.1.1"><p id="p199961439154519"><a name="p199961439154519"></a><a name="p199961439154519"></a>特性</p>
</th>
<th class="cellrowborder" valign="top" width="20.41%" id="mcps1.2.5.1.2"><p id="p09961739124513"><a name="p09961739124513"></a><a name="p09961739124513"></a>OceanStor V5</p>
</th>
<th class="cellrowborder" valign="top" width="27.83%" id="mcps1.2.5.1.3"><p id="p1699615397457"><a name="p1699615397457"></a><a name="p1699615397457"></a>OceanStor</p>
</th>
<th class="cellrowborder" valign="top" width="30.4%" id="mcps1.2.5.1.4"><p id="p11601298188"><a name="p11601298188"></a><a name="p11601298188"></a>OceanStor Dorado</p>
</th>
</tr>
</thead>
<tbody><tr id="row1899683984519"><td class="cellrowborder" valign="top" width="21.36%" headers="mcps1.2.5.1.1 "><p id="p899653994514"><a name="p899653994514"></a><a name="p899653994514"></a><span>Static Provisioning</span></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="20.41%" headers="mcps1.2.5.1.2 "><p id="p9633201715"><a name="p9633201715"></a><a name="p9633201715"></a>NFS 3</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="27.83%" headers="mcps1.2.5.1.3 "><a name="ul5142135920"></a><a name="ul5142135920"></a><ul id="ul5142135920"><li>NFS 3/4.0/4.1/4.2</li><li>仅6.1.7及以后版本支持NFS over RDMA</li><li>仅6.1.8及以后版本支持NFS 4.2</li></ul>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="30.4%" headers="mcps1.2.5.1.4 "><a name="ul1321316916219"></a><a name="ul1321316916219"></a><ul id="ul1321316916219"><li>NFS 3/4.0/4.1/4.2/NFS+</li><li>仅6.1.3及以后版本支持NFS 4.1</li><li>仅6.1.7及以后版本支持NFS over RDMA</li><li>仅6.1.8及以后版本支持NFS 4.2</li><li>仅6.1.7及以后版本支持NFS+</li></ul>
</td>
</tr>
<tr id="row49961039174517"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p9996173974516"><a name="p9996173974516"></a><a name="p9996173974516"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row55791517133218"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p3579151783219"><a name="p3579151783219"></a><a name="p3579151783219"></a>Manage Provisioning</p>
</td>
</tr>
<tr id="row8996539144513"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p49961939194517"><a name="p49961939194517"></a><a name="p49961939194517"></a><span>Expand Persistent Volume</span></p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p071645145119"><a name="p071645145119"></a><a name="p071645145119"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row14996173944518"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p280819372253"><a name="p280819372253"></a><a name="p280819372253"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p1771745145117"><a name="p1771745145117"></a><a name="p1771745145117"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row1599693916456"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p49961939184516"><a name="p49961939184516"></a><a name="p49961939184516"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p2996153934511"><a name="p2996153934511"></a><a name="p2996153934511"></a>支持</p>
</td>
</tr>
<tr id="row15996173994516"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p15997133914455"><a name="p15997133914455"></a><a name="p15997133914455"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p149971339154511"><a name="p149971339154511"></a><a name="p149971339154511"></a>支持</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p199713910459"><a name="p199713910459"></a><a name="p199713910459"></a>仅6.1.5及其之后版本支持</p>
</td>
</tr>
<tr id="row19976393452"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1799710394452"><a name="p1799710394452"></a><a name="p1799710394452"></a>Clone <span>Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p197114535118"><a name="p197114535118"></a><a name="p197114535118"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的非双活卷</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p17444111738"><a name="p17444111738"></a><a name="p17444111738"></a>仅6.1.5及其之后版本支持使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row253813281571"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p105391828872"><a name="p105391828872"></a><a name="p105391828872"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p7539162811719"><a name="p7539162811719"></a><a name="p7539162811719"></a>不支持</p>
</td>
</tr>
<tr id="row76671821015"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p146673811105"><a name="p146673811105"></a><a name="p146673811105"></a>Topology</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p18667138181019"><a name="p18667138181019"></a><a name="p18667138181019"></a>支持</p>
</td>
</tr>
<tr id="row91081351378"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1423525343819"><a name="p1423525343819"></a><a name="p1423525343819"></a>Generic Ephemeral Volumes</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p2091319219390"><a name="p2091319219390"></a><a name="p2091319219390"></a>支持</p>
</td>
</tr>
<tr id="row59655172115"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p996591717110"><a name="p996591717110"></a><a name="p996591717110"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p69001214125219"><a name="p69001214125219"></a><a name="p69001214125219"></a><span>RWO/ROX/RWX/RWOP，</span><span>RWOP</span>需<span>Kubernetes 1.22</span>版本以上支持</p>
</td>
</tr>
<tr id="row4749123262619"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p274993211262"><a name="p274993211262"></a><a name="p274993211262"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1374918324264"><a name="p1374918324264"></a><a name="p1374918324264"></a>仅系统用户支持</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p106126462253"><a name="p106126462253"></a><a name="p106126462253"></a>支持</p>
</td>
</tr>
<tr id="row13606622132720"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1760612292716"><a name="p1760612292716"></a><a name="p1760612292716"></a>应用类型</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p49831014582"><a name="p49831014582"></a><a name="p49831014582"></a>不支持</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p1360619224273"><a name="p1360619224273"></a><a name="p1360619224273"></a>支持</p>
</td>
</tr>
<tr id="row17943182222817"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p79432225287"><a name="p79432225287"></a><a name="p79432225287"></a>卷双活</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p09431322152815"><a name="p09431322152815"></a><a name="p09431322152815"></a>不支持</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p794313221284"><a name="p794313221284"></a><a name="p794313221284"></a>支持，仅支持AA双活</p>
</td>
</tr>
<tr id="row8191849183619"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p81912491363"><a name="p81912491363"></a><a name="p81912491363"></a>存储多租户</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p15191349103613"><a name="p15191349103613"></a><a name="p15191349103613"></a>支持</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p165451751102711"><a name="p165451751102711"></a><a name="p165451751102711"></a>6.1.3及以后版本支持</p>
</td>
</tr>
</tbody>
</table>

**表 2**  华为企业存储Dtree支持的特性

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
<tr id="row1283074261313"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p08311742201314"><a name="p08311742201314"></a><a name="p08311742201314"></a>Manage Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p1483184281313"><a name="p1483184281313"></a><a name="p1483184281313"></a>X</p>
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

