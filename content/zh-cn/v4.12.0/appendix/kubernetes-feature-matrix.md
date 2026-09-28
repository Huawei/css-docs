---
title: "Kubernetes特性矩阵"
linkTitle: "Kubernetes特性矩阵"
description: 
weight: 4
---

本章节说明华为CSI在不同Kubernetes版本下支持的特性。

**表 1**  Kubernetes版本与支持的特性

<a name="table134589135522"></a>
<table><thead align="left"><tr id="row1945901325213"><th class="cellrowborder" valign="top" width="29.994001199760046%" id="mcps1.2.8.1.1"><p id="p83781092567"><a name="p83781092567"></a><a name="p83781092567"></a>特性</p>
</th>
<th class="cellrowborder" valign="top" width="11.667666466706658%" id="mcps1.2.8.1.2"><p id="p17588166145911"><a name="p17588166145911"></a><a name="p17588166145911"></a>V1.16</p>
</th>
<th class="cellrowborder" valign="top" width="11.667666466706658%" id="mcps1.2.8.1.3"><p id="p137085201169"><a name="p137085201169"></a><a name="p137085201169"></a>V1.17</p>
</th>
<th class="cellrowborder" valign="top" width="11.667666466706658%" id="mcps1.2.8.1.4"><p id="p618613574544"><a name="p618613574544"></a><a name="p618613574544"></a>V1.18</p>
</th>
<th class="cellrowborder" valign="top" width="11.667666466706658%" id="mcps1.2.8.1.5"><p id="p7693534134910"><a name="p7693534134910"></a><a name="p7693534134910"></a>V1.19</p>
</th>
<th class="cellrowborder" valign="top" width="11.667666466706658%" id="mcps1.2.8.1.6"><p id="p285993816495"><a name="p285993816495"></a><a name="p285993816495"></a>V1.20</p>
</th>
<th class="cellrowborder" valign="top" width="11.667666466706658%" id="mcps1.2.8.1.7"><p id="p5246429194918"><a name="p5246429194918"></a><a name="p5246429194918"></a>V1.21+</p>
</th>
</tr>
</thead>
<tbody><tr id="row7414194911250"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p20414124916251"><a name="p20414124916251"></a><a name="p20414124916251"></a><span>Static Provisioning</span></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p1632311263591"><a name="p1632311263591"></a><a name="p1632311263591"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p041424952517"><a name="p041424952517"></a><a name="p041424952517"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p11414549132514"><a name="p11414549132514"></a><a name="p11414549132514"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p19812181155116"><a name="p19812181155116"></a><a name="p19812181155116"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p148125114514"><a name="p148125114514"></a><a name="p148125114514"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p3812121125113"><a name="p3812121125113"></a><a name="p3812121125113"></a>√</p>
</td>
</tr>
<tr id="row530585202516"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p10305205212257"><a name="p10305205212257"></a><a name="p10305205212257"></a>Dynamic Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p2323202605919"><a name="p2323202605919"></a><a name="p2323202605919"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p2305205252513"><a name="p2305205252513"></a><a name="p2305205252513"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p63055525250"><a name="p63055525250"></a><a name="p63055525250"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p11306175117"><a name="p11306175117"></a><a name="p11306175117"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p413018155110"><a name="p413018155110"></a><a name="p413018155110"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p813081175110"><a name="p813081175110"></a><a name="p813081175110"></a>√</p>
</td>
</tr>
<tr id="row1416733918318"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p12167183910315"><a name="p12167183910315"></a><a name="p12167183910315"></a>Manage Provisioning<sup id="sup6278163510162"><a name="sup6278163510162"></a><a name="sup6278163510162"></a>1</sup></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p3323162675915"><a name="p3323162675915"></a><a name="p3323162675915"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p115151792612"><a name="p115151792612"></a><a name="p115151792612"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p915919515317"><a name="p915919515317"></a><a name="p915919515317"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p61591751193118"><a name="p61591751193118"></a><a name="p61591751193118"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p01591051103110"><a name="p01591051103110"></a><a name="p01591051103110"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p5159175110315"><a name="p5159175110315"></a><a name="p5159175110315"></a>√</p>
</td>
</tr>
<tr id="row71451715261"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p131411762619"><a name="p131411762619"></a><a name="p131411762619"></a><span>Expand Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p1323172665913"><a name="p1323172665913"></a><a name="p1323172665913"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p766711282268"><a name="p766711282268"></a><a name="p766711282268"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p6151617102617"><a name="p6151617102617"></a><a name="p6151617102617"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p26051001518"><a name="p26051001518"></a><a name="p26051001518"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p136056010510"><a name="p136056010510"></a><a name="p136056010510"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p36051504515"><a name="p36051504515"></a><a name="p36051504515"></a>√</p>
</td>
</tr>
<tr id="row26676286268"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p15996539154513"><a name="p15996539154513"></a><a name="p15996539154513"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p109151131185916"><a name="p109151131185916"></a><a name="p109151131185916"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p2066612317202"><a name="p2066612317202"></a><a name="p2066612317202"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p544920732018"><a name="p544920732018"></a><a name="p544920732018"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p1372141262019"><a name="p1372141262019"></a><a name="p1372141262019"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p165118017510"><a name="p165118017510"></a><a name="p165118017510"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p16519016511"><a name="p16519016511"></a><a name="p16519016511"></a>√</p>
</td>
</tr>
<tr id="row1278563072619"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p2785173042617"><a name="p2785173042617"></a><a name="p2785173042617"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p391413155913"><a name="p391413155913"></a><a name="p391413155913"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p171375192011"><a name="p171375192011"></a><a name="p171375192011"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p204591952012"><a name="p204591952012"></a><a name="p204591952012"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p148419132205"><a name="p148419132205"></a><a name="p148419132205"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p14460105995015"><a name="p14460105995015"></a><a name="p14460105995015"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p184607593500"><a name="p184607593500"></a><a name="p184607593500"></a>√</p>
</td>
</tr>
<tr id="row51715221276"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p181714222276"><a name="p181714222276"></a><a name="p181714222276"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p29141931105916"><a name="p29141931105916"></a><a name="p29141931105916"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p9381265204"><a name="p9381265204"></a><a name="p9381265204"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p18717181022010"><a name="p18717181022010"></a><a name="p18717181022010"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p1261451422015"><a name="p1261451422015"></a><a name="p1261451422015"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p15843165815018"><a name="p15843165815018"></a><a name="p15843165815018"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p58431587503"><a name="p58431587503"></a><a name="p58431587503"></a>√</p>
</td>
</tr>
<tr id="row16798323162714"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p979818232273"><a name="p979818232273"></a><a name="p979818232273"></a>Clone <span>Persistent Volume</span></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p5914731125917"><a name="p5914731125917"></a><a name="p5914731125917"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p1953193812814"><a name="p1953193812814"></a><a name="p1953193812814"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p12798162302711"><a name="p12798162302711"></a><a name="p12798162302711"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p1115535825018"><a name="p1115535825018"></a><a name="p1115535825018"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p1715585819502"><a name="p1715585819502"></a><a name="p1715585819502"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p161554584501"><a name="p161554584501"></a><a name="p161554584501"></a>√</p>
</td>
</tr>
<tr id="row184929161095"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p74931916095"><a name="p74931916095"></a><a name="p74931916095"></a>Modify Volume<sup id="sup8775184813915"><a name="sup8775184813915"></a><a name="sup8775184813915"></a>2</sup></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p349319165912"><a name="p349319165912"></a><a name="p349319165912"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p149301619912"><a name="p149301619912"></a><a name="p149301619912"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p104932164911"><a name="p104932164911"></a><a name="p104932164911"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p549310166915"><a name="p549310166915"></a><a name="p549310166915"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p1493191617913"><a name="p1493191617913"></a><a name="p1493191617913"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p10493131611915"><a name="p10493131611915"></a><a name="p10493131611915"></a>√</p>
</td>
</tr>
<tr id="row115311038172815"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p75311238132819"><a name="p75311238132819"></a><a name="p75311238132819"></a><a href="https://kubernetes-csi.github.io/docs/raw-block.html" target="_blank" rel="noopener noreferrer">Raw Block Volume</a></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p17323182695919"><a name="p17323182695919"></a><a name="p17323182695919"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p18749336204711"><a name="p18749336204711"></a><a name="p18749336204711"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p95311938182811"><a name="p95311938182811"></a><a name="p95311938182811"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p10693133484917"><a name="p10693133484917"></a><a name="p10693133484917"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p17859153804913"><a name="p17859153804913"></a><a name="p17859153804913"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p182471929184915"><a name="p182471929184915"></a><a name="p182471929184915"></a>√</p>
</td>
</tr>
<tr id="row151111106290"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p21111010132910"><a name="p21111010132910"></a><a name="p21111010132910"></a><a href="https://kubernetes-csi.github.io/docs/topology.html" target="_blank" rel="noopener noreferrer">Topology</a></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p153235267592"><a name="p153235267592"></a><a name="p153235267592"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p1174144210582"><a name="p1174144210582"></a><a name="p1174144210582"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p1174953611474"><a name="p1174953611474"></a><a name="p1174953611474"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p13012029135820"><a name="p13012029135820"></a><a name="p13012029135820"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p1330192916588"><a name="p1330192916588"></a><a name="p1330192916588"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p203011229185818"><a name="p203011229185818"></a><a name="p203011229185818"></a>√</p>
</td>
</tr>
<tr id="row1953774110581"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p1874104210582"><a name="p1874104210582"></a><a name="p1874104210582"></a><a href="https://kubernetes-csi.github.io/docs/ephemeral-local-volumes.html" target="_blank" rel="noopener noreferrer">Generic Ephemeral Inline Volumes</a></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p10323026135913"><a name="p10323026135913"></a><a name="p10323026135913"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p177085203613"><a name="p177085203613"></a><a name="p177085203613"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p174119421582"><a name="p174119421582"></a><a name="p174119421582"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p177416427580"><a name="p177416427580"></a><a name="p177416427580"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p6741242145810"><a name="p6741242145810"></a><a name="p6741242145810"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p1774164213588"><a name="p1774164213588"></a><a name="p1774164213588"></a>√</p>
</td>
</tr>
<tr id="row9212198995"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p0213168493"><a name="p0213168493"></a><a name="p0213168493"></a><a href="https://kubernetes-csi.github.io/docs/volume-limits.html#volume-limits" target="_blank" rel="noopener noreferrer">Volume Limits</a></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p22131788920"><a name="p22131788920"></a><a name="p22131788920"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p1375317112109"><a name="p1375317112109"></a><a name="p1375317112109"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p1375312191014"><a name="p1375312191014"></a><a name="p1375312191014"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p157531191015"><a name="p157531191015"></a><a name="p157531191015"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p67530117104"><a name="p67530117104"></a><a name="p67530117104"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p7753111161013"><a name="p7753111161013"></a><a name="p7753111161013"></a>√</p>
</td>
</tr>
<tr id="row121049413108"><td class="cellrowborder" valign="top" width="29.994001199760046%" headers="mcps1.2.8.1.1 "><p id="p1610414418106"><a name="p1610414418106"></a><a name="p1610414418106"></a><a href="https://kubernetes-csi.github.io/docs/support-fsgroup.html" target="_blank" rel="noopener noreferrer">FSGroup Support</a></p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.2 "><p id="p13104134121010"><a name="p13104134121010"></a><a name="p13104134121010"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.3 "><p id="p31051041151017"><a name="p31051041151017"></a><a name="p31051041151017"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.4 "><p id="p17105174101017"><a name="p17105174101017"></a><a name="p17105174101017"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.5 "><p id="p1610554110101"><a name="p1610554110101"></a><a name="p1610554110101"></a>x</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.6 "><p id="p32363315235"><a name="p32363315235"></a><a name="p32363315235"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="11.667666466706658%" headers="mcps1.2.8.1.7 "><p id="p6164194172310"><a name="p6164194172310"></a><a name="p6164194172310"></a>√</p>
</td>
</tr>
</tbody>
</table>

-   注释1 Manage Provisioning是华为CSI自定义的纳管卷特性，该特性支持将已有存储资源纳管至Kubernetes。不允许将一个存储资源纳管多次和针对同一个存储资源进行并发删除/创建操作。当同一个存储资源被多个集群纳管时，在单个集群中针对该纳管卷的操作仅在当前集群内生效，不会同步到其他集群中，需要使用者自行在其他集群中对该纳管卷进行数据同步操作。
-   注释2 Modify Volume是华为CSI自定义的PVC变更特性，该特性支持将普通卷变更为双活卷，使用该特性需要对接存储支持卷双活特性。

