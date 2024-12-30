---
title: "华为企业存储兼容性"
linkTitle: "华为企业存储兼容性"
description: 
weight: 3
---

华为CSI插件兼容华为OceanStor系列的全闪存存储和混合闪存存储，具体支持的存储版本如下表所示：

## 支持的华为企业存储{#section6374917361}

**表 1**  支持的华为企业存储

<a name="table993123194920"></a>
<table><thead align="left"><tr id="row1893163144911"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="zh-cn_topic_0150885201_p85821945142912"><a name="zh-cn_topic_0150885201_p85821945142912"></a><a name="zh-cn_topic_0150885201_p85821945142912"></a>存储产品</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="zh-cn_topic_0150885201_p458218450291"><a name="zh-cn_topic_0150885201_p458218450291"></a><a name="zh-cn_topic_0150885201_p458218450291"></a>版本</p>
</th>
</tr>
</thead>
<tbody><tr id="row093253164916"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="zh-cn_topic_0150885201_p194271510143119"><a name="zh-cn_topic_0150885201_p194271510143119"></a><a name="zh-cn_topic_0150885201_p194271510143119"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="zh-cn_topic_0150885201_p16427151073111"><a name="zh-cn_topic_0150885201_p16427151073111"></a><a name="zh-cn_topic_0150885201_p16427151073111"></a>V500R007, V500R007 Kunpeng</p>
</td>
</tr>
<tr id="row169322032493"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p958616149499"><a name="p958616149499"></a><a name="p958616149499"></a>OceanStor Dorado V3</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p05854142497"><a name="p05854142497"></a><a name="p05854142497"></a>V300R002</p>
</td>
</tr>
<tr id="row096032118493"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="zh-cn_topic_0150885201_p112034513115"><a name="zh-cn_topic_0150885201_p112034513115"></a><a name="zh-cn_topic_0150885201_p112034513115"></a>OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="zh-cn_topic_0150885201_p612014452314"><a name="zh-cn_topic_0150885201_p612014452314"></a><a name="zh-cn_topic_0150885201_p612014452314"></a>6.1.3, 6.1.5, 6.1.6, 6.1.7, 6.1.8, V700R001C00</p>
</td>
</tr>
<tr id="row17366171818495"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p193661118204917"><a name="p193661118204917"></a><a name="p193661118204917"></a>OceanStor Dorado</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p3366618184918"><a name="p3366618184918"></a><a name="p3366618184918"></a>6.1.0, 6.1.2, 6.1.3, 6.1.5, 6.1.6, 6.1.7, 6.1.8, V700R001C00</p>
</td>
</tr>
</tbody>
</table>

## 华为企业存储支持的特性{#section0652122673620}

华为CSI插件针对华为企业存储支持如下特性。

**表 2**  华为企业存储支持的特性及约束

<a name="table14995183994515"></a>
<table><thead align="left"><tr id="row6996173914451"><th class="cellrowborder" valign="top" width="19.88%" id="mcps1.2.6.1.1"><p id="p199961439154519"><a name="p199961439154519"></a><a name="p199961439154519"></a>特性</p>
</th>
<th class="cellrowborder" valign="top" width="18.759999999999998%" id="mcps1.2.6.1.2"><p id="p09961739124513"><a name="p09961739124513"></a><a name="p09961739124513"></a>OceanStor V5</p>
</th>
<th class="cellrowborder" valign="top" width="19.42%" id="mcps1.2.6.1.3"><p id="p189961739104515"><a name="p189961739104515"></a><a name="p189961739104515"></a>OceanStor Dorado V3</p>
</th>
<th class="cellrowborder" valign="top" width="20.59%" id="mcps1.2.6.1.4"><p id="p1699615397457"><a name="p1699615397457"></a><a name="p1699615397457"></a>OceanStor</p>
</th>
<th class="cellrowborder" valign="top" width="21.349999999999998%" id="mcps1.2.6.1.5"><p id="p11601298188"><a name="p11601298188"></a><a name="p11601298188"></a>OceanStor Dorado</p>
</th>
</tr>
</thead>
<tbody><tr id="row1899683984519"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p899653994514"><a name="p899653994514"></a><a name="p899653994514"></a><span>Static Provisioning</span></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p86732141719"><a name="p86732141719"></a><a name="p86732141719"></a>SAN：FC/iSCSI<sup id="sup777718253598"><a name="sup777718253598"></a><a name="sup777718253598"></a>2</sup></p>
<p id="p9633201715"><a name="p9633201715"></a><a name="p9633201715"></a>NAS：NFS 3</p>
<p id="p1957941763215"><a name="p1957941763215"></a><a name="p1957941763215"></a></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p3996103915451"><a name="p3996103915451"></a><a name="p3996103915451"></a>SAN：FC/iSCSI<sup id="sup107073234594"><a name="sup107073234594"></a><a name="sup107073234594"></a>2</sup></p>
<p id="p11579201753211"><a name="p11579201753211"></a><a name="p11579201753211"></a></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p12996173920456"><a name="p12996173920456"></a><a name="p12996173920456"></a>SAN：FC/iSCSI/NVMe over RoCE/NVMe over FC<sup id="sup1754136102416"><a name="sup1754136102416"></a><a name="sup1754136102416"></a>3</sup></p>
<p id="p20838142381814"><a name="p20838142381814"></a><a name="p20838142381814"></a>NAS：NFS 3/4.0/4.1/4.2<sup id="sup38128018014"><a name="sup38128018014"></a><a name="sup38128018014"></a>4</sup></p>
<p id="p7579181715326"><a name="p7579181715326"></a><a name="p7579181715326"></a></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p115594419186"><a name="p115594419186"></a><a name="p115594419186"></a>SAN：FC/iSCSI/NVMe over RoCE/NVMe over FC<sup id="sup13412163962419"><a name="sup13412163962419"></a><a name="sup13412163962419"></a>3</sup></p>
<p id="p12839143282719"><a name="p12839143282719"></a><a name="p12839143282719"></a>NAS：NFS 3/4.0/4.1/4.2<sup id="sup5839532102713"><a name="sup5839532102713"></a><a name="sup5839532102713"></a>4</sup></p>
<p id="p757919176329"><a name="p757919176329"></a><a name="p757919176329"></a></p>
</td>
</tr>
<tr id="row49961039174517"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p9996173974516"><a name="p9996173974516"></a><a name="p9996173974516"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row55791517133218"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p3579151783219"><a name="p3579151783219"></a><a name="p3579151783219"></a>Manage Provisioning<sup id="sup113201739217"><a name="sup113201739217"></a><a name="sup113201739217"></a>1</sup></p>
</td>
</tr>
<tr id="row8996539144513"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p49961939194517"><a name="p49961939194517"></a><a name="p49961939194517"></a><span>Expand Persistent Volume</span><sup id="sup745085319811"><a name="sup745085319811"></a><a name="sup745085319811"></a>5</sup></p>
</td>
<td class="cellrowborder" colspan="4" valign="top" headers="mcps1.2.6.1.2 mcps1.2.6.1.3 mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p071645145119"><a name="p071645145119"></a><a name="p071645145119"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row14996173944518"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p280819372253"><a name="p280819372253"></a><a name="p280819372253"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="4" valign="top" headers="mcps1.2.6.1.2 mcps1.2.6.1.3 mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p1771745145117"><a name="p1771745145117"></a><a name="p1771745145117"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row1599693916456"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p49961939184516"><a name="p49961939184516"></a><a name="p49961939184516"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p2996153934511"><a name="p2996153934511"></a><a name="p2996153934511"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p1499616398455"><a name="p1499616398455"></a><a name="p1499616398455"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p10996183911451"><a name="p10996183911451"></a><a name="p10996183911451"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p111601529121812"><a name="p111601529121812"></a><a name="p111601529121812"></a>支持</p>
</td>
</tr>
<tr id="row15996173994516"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p15997133914455"><a name="p15997133914455"></a><a name="p15997133914455"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p149971339154511"><a name="p149971339154511"></a><a name="p149971339154511"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p29971639124518"><a name="p29971639124518"></a><a name="p29971639124518"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p199713910459"><a name="p199713910459"></a><a name="p199713910459"></a>SAN：支持</p>
<p id="p33033201414"><a name="p33033201414"></a><a name="p33033201414"></a>NAS：仅6.1.5及其之后版本支持</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p193754331128"><a name="p193754331128"></a><a name="p193754331128"></a>SAN：支持</p>
<p id="p153757331127"><a name="p153757331127"></a><a name="p153757331127"></a>NAS：仅6.1.5及其之后版本支持</p>
</td>
</tr>
<tr id="row19976393452"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p1799710394452"><a name="p1799710394452"></a><a name="p1799710394452"></a>Clone <span>Persistent Volume</span></p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.6.1.2 mcps1.2.6.1.3 "><p id="p197114535118"><a name="p197114535118"></a><a name="p197114535118"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的非双活卷</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p17444111738"><a name="p17444111738"></a><a name="p17444111738"></a>SAN：支持使用Dynamic Provisioning，Manage Provisioning方式创建的非双活卷</p>
<p id="p17444611332"><a name="p17444611332"></a><a name="p17444611332"></a>NAS：仅6.1.5及其之后版本支持使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row253813281571"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p105391828872"><a name="p105391828872"></a><a name="p105391828872"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p7539162811719"><a name="p7539162811719"></a><a name="p7539162811719"></a>仅支持SAN类型的卷</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p12539162810713"><a name="p12539162810713"></a><a name="p12539162810713"></a>仅支持SAN类型的卷</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p1353952811711"><a name="p1353952811711"></a><a name="p1353952811711"></a>仅支持SAN类型的卷</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p153913281879"><a name="p153913281879"></a><a name="p153913281879"></a>仅支持SAN类型的卷</p>
</td>
</tr>
<tr id="row76671821015"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p146673811105"><a name="p146673811105"></a><a name="p146673811105"></a>Topology</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p18667138181019"><a name="p18667138181019"></a><a name="p18667138181019"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p1566710821013"><a name="p1566710821013"></a><a name="p1566710821013"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p106676821018"><a name="p106676821018"></a><a name="p106676821018"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p166671688101"><a name="p166671688101"></a><a name="p166671688101"></a>支持</p>
</td>
</tr>
<tr id="row91081351378"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p1423525343819"><a name="p1423525343819"></a><a name="p1423525343819"></a>Generic Ephemeral Volumes</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p2091319219390"><a name="p2091319219390"></a><a name="p2091319219390"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p15913152193911"><a name="p15913152193911"></a><a name="p15913152193911"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p1691418293913"><a name="p1691418293913"></a><a name="p1691418293913"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p18914028397"><a name="p18914028397"></a><a name="p18914028397"></a>支持</p>
</td>
</tr>
<tr id="row59655172115"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p996591717110"><a name="p996591717110"></a><a name="p996591717110"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" colspan="4" valign="top" headers="mcps1.2.6.1.2 mcps1.2.6.1.3 mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p69001214125219"><a name="p69001214125219"></a><a name="p69001214125219"></a><span>RWO/ROX/RWOP：</span>所有类型卷均支持，<span>RWOP</span>需<span>Kubernetes 1.22</span>版本以上支持。</p>
<p id="p1390021412527"><a name="p1390021412527"></a><a name="p1390021412527"></a><span>RWX</span>：仅Raw Block卷和NFS类型的卷支持</p>
</td>
</tr>
<tr id="row4749123262619"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p274993211262"><a name="p274993211262"></a><a name="p274993211262"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p1374918324264"><a name="p1374918324264"></a><a name="p1374918324264"></a>支持<sup id="sup6549410191016"><a name="sup6549410191016"></a><a name="sup6549410191016"></a>6</sup></p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p4749123216266"><a name="p4749123216266"></a><a name="p4749123216266"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p8749203242620"><a name="p8749203242620"></a><a name="p8749203242620"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p19749123216264"><a name="p19749123216264"></a><a name="p19749123216264"></a>支持</p>
</td>
</tr>
<tr id="row13606622132720"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p1760612292716"><a name="p1760612292716"></a><a name="p1760612292716"></a>应用类型</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p1960652212711"><a name="p1960652212711"></a><a name="p1960652212711"></a>不涉及</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p136063224270"><a name="p136063224270"></a><a name="p136063224270"></a>不涉及</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p1360619224273"><a name="p1360619224273"></a><a name="p1360619224273"></a>支持</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p1960622242718"><a name="p1960622242718"></a><a name="p1960622242718"></a>支持</p>
</td>
</tr>
<tr id="row17943182222817"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p79432225287"><a name="p79432225287"></a><a name="p79432225287"></a>卷双活<sup id="sup13691121310106"><a name="sup13691121310106"></a><a name="sup13691121310106"></a>7</sup></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="p09431322152815"><a name="p09431322152815"></a><a name="p09431322152815"></a>不支持</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="p5943522142818"><a name="p5943522142818"></a><a name="p5943522142818"></a>不涉及</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p794313221284"><a name="p794313221284"></a><a name="p794313221284"></a>仅支持NAS类型的卷</p>
</td>
</tr>
<tr id="row8191849183619"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p81912491363"><a name="p81912491363"></a><a name="p81912491363"></a>存储多租户</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="p177194510519"><a name="p177194510519"></a><a name="p177194510519"></a>仅支持NAS类型的卷</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="p219124920369"><a name="p219124920369"></a><a name="p219124920369"></a>不涉及</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p15191349103613"><a name="p15191349103613"></a><a name="p15191349103613"></a>仅支持NAS类型的卷<sup id="sup17244016111016"><a name="sup17244016111016"></a><a name="sup17244016111016"></a>8</sup></p>
</td>
</tr>
</tbody>
</table>

-   注释1 Manage Provisioning是华为CSI自定义的纳管卷特性，该特性支持将已有存储资源纳管至Kubernetes。不允许将一个存储资源纳管多次和针对同一个存储资源进行并发删除/创建操作。
-   注释2 若用户的容器平台部署在虚拟化环境中，则仅支持iSCSI组网。
-   注释3 使用NVMe over RoCE或NVMe over FC时，worker节点nvme-cli工具版本不低于1.9，查询命令为：nvme version。
-   注释4 仅OceanStor/OceanStor Dorado 6.1.0及以后版本支持NFS。仅OceanStor/OceanStor Dorado 6.1.3及以后版本支持NFS 4.1，OceanStor/OceanStor Dorado 6.1.7及以后版本支持NFS over RDMA，OceanStor/OceanStor Dorado 6.1.8及以后版本支持NFS 4.2。
-   注释5 发放的volumeType为lun且accessModes为ReadOnlyMany的PVC不支持扩容。
-   注释6 仅系统用户支持配置QoS。
-   注释7 仅支持AA双活。
-   注释8 仅OceanStor/OceanStor Dorado 6.1.3及以后版本支持多租户。

华为CSI插件针对华为企业存储Dtree特性支持如下表所示。

**表 3**  Dtree支持的特性

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

**表 4**  Dtree支持的华为存储版本

<a name="table120mcpsimp"></a>
<table><thead align="left"><tr id="row126mcpsimp"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p128mcpsimp"><a name="p128mcpsimp"></a><a name="p128mcpsimp"></a>存储产品</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p130mcpsimp"><a name="p130mcpsimp"></a><a name="p130mcpsimp"></a>版本</p>
</th>
</tr>
</thead>
<tbody><tr id="row132mcpsimp"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p134mcpsimp"><a name="p134mcpsimp"></a><a name="p134mcpsimp"></a>OceanStor Dorado</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p136mcpsimp"><a name="p136mcpsimp"></a><a name="p136mcpsimp"></a>6.1.0, 6.1.2, 6.1.3, 6.1.5, 6.1.6, 6.1.7, 6.1.8, V700R001C00</p>
</td>
</tr>
</tbody>
</table>

