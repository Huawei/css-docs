---
title: "Compatibility with Huawei Enterprise Storage"
linkTitle: "Compatibility with Huawei Enterprise Storage"
description: 
weight: 3
---

Huawei CSI plug-in is compatible with Huawei OceanStor series all-flash storage and hybrid flash storage. The following table lists the supported storage versions.

**Table  1**  Supported Huawei enterprise storage

<a name="table993123194920"></a>
<table><thead align="left"><tr id="row1893163144911"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="en-us_topic_0150885201_p85821945142912"><a name="en-us_topic_0150885201_p85821945142912"></a><a name="en-us_topic_0150885201_p85821945142912"></a>Storage Product</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="en-us_topic_0150885201_p458218450291"><a name="en-us_topic_0150885201_p458218450291"></a><a name="en-us_topic_0150885201_p458218450291"></a>Version</p>
</th>
</tr>
</thead>
<tbody><tr id="row093253164916"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="en-us_topic_0150885201_p194271510143119"><a name="en-us_topic_0150885201_p194271510143119"></a><a name="en-us_topic_0150885201_p194271510143119"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="en-us_topic_0150885201_p16427151073111"><a name="en-us_topic_0150885201_p16427151073111"></a><a name="en-us_topic_0150885201_p16427151073111"></a>V500R007, V500R007 Kunpeng</p>
</td>
</tr>
<tr id="row169322032493"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p958616149499"><a name="p958616149499"></a><a name="p958616149499"></a>OceanStor Dorado V3</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p05854142497"><a name="p05854142497"></a><a name="p05854142497"></a>V300R002</p>
</td>
</tr>
<tr id="row096032118493"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="en-us_topic_0150885201_p112034513115"><a name="en-us_topic_0150885201_p112034513115"></a><a name="en-us_topic_0150885201_p112034513115"></a>OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="en-us_topic_0150885201_p612014452314"><a name="en-us_topic_0150885201_p612014452314"></a><a name="en-us_topic_0150885201_p612014452314"></a>6.1.3, 6.1.5, 6.1.6, 6.1.7, 6.1.8</p>
</td>
</tr>
<tr id="row17366171818495"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p193661118204917"><a name="p193661118204917"></a><a name="p193661118204917"></a>OceanStor Dorado</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p3366618184918"><a name="p3366618184918"></a><a name="p3366618184918"></a>6.1.0, 6.1.2, 6.1.3, 6.1.5, 6.1.6, 6.1.7, 6.1.8</p>
</td>
</tr>
</tbody>
</table>

Huawei CSI plug-in supports the following features for Huawei enterprise storage.

**Table  2**  Features supported by Huawei enterprise storage and constraints

<a name="table14995183994515"></a>
<table><thead align="left"><tr id="row6996173914451"><th class="cellrowborder" valign="top" width="19.88%" id="mcps1.2.6.1.1"><p id="p199961439154519"><a name="p199961439154519"></a><a name="p199961439154519"></a>Feature</p>
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
<tbody><tr id="row1899683984519"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p899653994514"><a name="p899653994514"></a><a name="p899653994514"></a>Static Provisioning</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p86732141719"><a name="p86732141719"></a><a name="p86732141719"></a>SAN: FC/iSCSI<sup id="sup777718253598"><a name="sup777718253598"></a><a name="sup777718253598"></a>2</sup></p>
<p id="p9633201715"><a name="p9633201715"></a><a name="p9633201715"></a>NAS: NFS 3</p>
<p id="p1957941763215"><a name="p1957941763215"></a><a name="p1957941763215"></a></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p3996103915451"><a name="p3996103915451"></a><a name="p3996103915451"></a>SAN: FC/iSCSI<sup id="sup107073234594"><a name="sup107073234594"></a><a name="sup107073234594"></a>2</sup></p>
<p id="p11579201753211"><a name="p11579201753211"></a><a name="p11579201753211"></a></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p12996173920456"><a name="p12996173920456"></a><a name="p12996173920456"></a>SAN: FC/iSCSI/NVMe over RoCE/NVMe over FC<sup id="sup144069810307"><a name="sup144069810307"></a><a name="sup144069810307"></a>3</sup></p>
<p id="p20838142381814"><a name="p20838142381814"></a><a name="p20838142381814"></a>NAS: NFS 3/4.0/4.1</p>
<p id="p7579181715326"><a name="p7579181715326"></a><a name="p7579181715326"></a></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p115594419186"><a name="p115594419186"></a><a name="p115594419186"></a>SAN: FC/iSCSI/NVMe over RoCE/NVMe over FC<sup id="sup19167519194320"><a name="sup19167519194320"></a><a name="sup19167519194320"></a>3</sup></p>
<p id="p12839143282719"><a name="p12839143282719"></a><a name="p12839143282719"></a>NAS: NFS 3/4.0/4.1<sup id="sup5839532102713"><a name="sup5839532102713"></a><a name="sup5839532102713"></a>4</sup></p>
<p id="p757919176329"><a name="p757919176329"></a><a name="p757919176329"></a></p>
</td>
</tr>
<tr id="row49961039174517"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p9996173974516"><a name="p9996173974516"></a><a name="p9996173974516"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row55791517133218"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p3579151783219"><a name="p3579151783219"></a><a name="p3579151783219"></a>Manage Provisioning<sup id="sup113201739217"><a name="sup113201739217"></a><a name="sup113201739217"></a>1</sup></p>
</td>
</tr>
<tr id="row8996539144513"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p49961939194517"><a name="p49961939194517"></a><a name="p49961939194517"></a>Expand Persistent Volume<sup id="sup745085319811"><a name="sup745085319811"></a><a name="sup745085319811"></a>5</sup></p>
</td>
<td class="cellrowborder" colspan="4" valign="top" headers="mcps1.2.6.1.2 mcps1.2.6.1.3 mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p071645145119"><a name="p071645145119"></a><a name="p071645145119"></a>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
</tr>
<tr id="row14996173944518"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p280819372253"><a name="p280819372253"></a><a name="p280819372253"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="4" valign="top" headers="mcps1.2.6.1.2 mcps1.2.6.1.3 mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p1771745145117"><a name="p1771745145117"></a><a name="p1771745145117"></a>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
</tr>
<tr id="row1599693916456"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p49961939184516"><a name="p49961939184516"></a><a name="p49961939184516"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p2996153934511"><a name="p2996153934511"></a><a name="p2996153934511"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p1499616398455"><a name="p1499616398455"></a><a name="p1499616398455"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p10996183911451"><a name="p10996183911451"></a><a name="p10996183911451"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p111601529121812"><a name="p111601529121812"></a><a name="p111601529121812"></a>Supported</p>
</td>
</tr>
<tr id="row15996173994516"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p15997133914455"><a name="p15997133914455"></a><a name="p15997133914455"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p149971339154511"><a name="p149971339154511"></a><a name="p149971339154511"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p29971639124518"><a name="p29971639124518"></a><a name="p29971639124518"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p199713910459"><a name="p199713910459"></a><a name="p199713910459"></a>SAN: supported</p>
<p id="p33033201414"><a name="p33033201414"></a><a name="p33033201414"></a>NAS: supported only in 6.1.5 and later versions</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p193754331128"><a name="p193754331128"></a><a name="p193754331128"></a>SAN: supported</p>
<p id="p153757331127"><a name="p153757331127"></a><a name="p153757331127"></a>NAS: supported only in 6.1.5 and later versions</p>
</td>
</tr>
<tr id="row19976393452"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p1799710394452"><a name="p1799710394452"></a><a name="p1799710394452"></a>Clone Persistent Volume</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.6.1.2 mcps1.2.6.1.3 "><p id="p197114535118"><a name="p197114535118"></a><a name="p197114535118"></a>Non-HyperMetro volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p17444111738"><a name="p17444111738"></a><a name="p17444111738"></a>SAN: supports non-HyperMetro volumes created in Dynamic Provisioning or Manage Provisioning mode.</p>
<p id="p17444611332"><a name="p17444611332"></a><a name="p17444611332"></a>NAS: Only 6.1.5 and later versions support volumes created in Dynamic Provisioning or Manage Provisioning mode.</p>
</td>
</tr>
<tr id="row253813281571"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p105391828872"><a name="p105391828872"></a><a name="p105391828872"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p7539162811719"><a name="p7539162811719"></a><a name="p7539162811719"></a>Only SAN volumes are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p12539162810713"><a name="p12539162810713"></a><a name="p12539162810713"></a>Only SAN volumes are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p1353952811711"><a name="p1353952811711"></a><a name="p1353952811711"></a>Only SAN volumes are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p153913281879"><a name="p153913281879"></a><a name="p153913281879"></a>Only SAN volumes are supported.</p>
</td>
</tr>
<tr id="row76671821015"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p146673811105"><a name="p146673811105"></a><a name="p146673811105"></a>Topology</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p18667138181019"><a name="p18667138181019"></a><a name="p18667138181019"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p1566710821013"><a name="p1566710821013"></a><a name="p1566710821013"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p106676821018"><a name="p106676821018"></a><a name="p106676821018"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p166671688101"><a name="p166671688101"></a><a name="p166671688101"></a>Supported</p>
</td>
</tr>
<tr id="row91081351378"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p1423525343819"><a name="p1423525343819"></a><a name="p1423525343819"></a>Generic Ephemeral Volumes</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p2091319219390"><a name="p2091319219390"></a><a name="p2091319219390"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p15913152193911"><a name="p15913152193911"></a><a name="p15913152193911"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p1691418293913"><a name="p1691418293913"></a><a name="p1691418293913"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p18914028397"><a name="p18914028397"></a><a name="p18914028397"></a>Supported</p>
</td>
</tr>
<tr id="row59655172115"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p996591717110"><a name="p996591717110"></a><a name="p996591717110"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" colspan="4" valign="top" headers="mcps1.2.6.1.2 mcps1.2.6.1.3 mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p69001214125219"><a name="p69001214125219"></a><a name="p69001214125219"></a>RWO/ROX/RWOP: supported by all types of volumes. RWOP is supported only by Kubernetes 1.22 and later versions.</p>
<p id="p1390021412527"><a name="p1390021412527"></a><a name="p1390021412527"></a>RWX: supported only by Raw Block volumes and NFS volumes.</p>
</td>
</tr>
<tr id="row4749123262619"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p274993211262"><a name="p274993211262"></a><a name="p274993211262"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p1374918324264"><a name="p1374918324264"></a><a name="p1374918324264"></a>Supported<sup id="sup112641622162312"><a name="sup112641622162312"></a><a name="sup112641622162312"></a>6</sup></p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p4749123216266"><a name="p4749123216266"></a><a name="p4749123216266"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p8749203242620"><a name="p8749203242620"></a><a name="p8749203242620"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p19749123216264"><a name="p19749123216264"></a><a name="p19749123216264"></a>Supported</p>
</td>
</tr>
<tr id="row13606622132720"><td class="cellrowborder" valign="top" width="19.88%" headers="mcps1.2.6.1.1 "><p id="p1760612292716"><a name="p1760612292716"></a><a name="p1760612292716"></a>Application type</p>
</td>
<td class="cellrowborder" valign="top" width="18.759999999999998%" headers="mcps1.2.6.1.2 "><p id="p1960652212711"><a name="p1960652212711"></a><a name="p1960652212711"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="19.42%" headers="mcps1.2.6.1.3 "><p id="p136063224270"><a name="p136063224270"></a><a name="p136063224270"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="20.59%" headers="mcps1.2.6.1.4 "><p id="p1360619224273"><a name="p1360619224273"></a><a name="p1360619224273"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="21.349999999999998%" headers="mcps1.2.6.1.5 "><p id="p1960622242718"><a name="p1960622242718"></a><a name="p1960622242718"></a>Supported</p>
</td>
</tr>
<tr id="row17943182222817"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p79432225287"><a name="p79432225287"></a><a name="p79432225287"></a>Volume HyperMetro<sup id="sup3481527112310"><a name="sup3481527112310"></a><a name="sup3481527112310"></a>7</sup></p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="p09431322152815"><a name="p09431322152815"></a><a name="p09431322152815"></a>Not supported</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="p5943522142818"><a name="p5943522142818"></a><a name="p5943522142818"></a>N/A</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p794313221284"><a name="p794313221284"></a><a name="p794313221284"></a>Only NAS volumes are supported.</p>
</td>
</tr>
<tr id="row8191849183619"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="p81912491363"><a name="p81912491363"></a><a name="p81912491363"></a>Storage multi-tenant</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="p177194510519"><a name="p177194510519"></a><a name="p177194510519"></a>Only NAS volumes are supported.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="p219124920369"><a name="p219124920369"></a><a name="p219124920369"></a>N/A</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.6.1.4 mcps1.2.6.1.5 "><p id="p15191349103613"><a name="p15191349103613"></a><a name="p15191349103613"></a>Only NAS volumes are supported.<sup id="sup17837133182311"><a name="sup17837133182311"></a><a name="sup17837133182311"></a>8</sup></p>
</td>
</tr>
</tbody>
</table>

-   Note 1: Manage Provisioning is a volume management feature customized by Huawei CSI. This feature allows existing storage resources to be managed by Kubernetes. You are not allowed to manage a storage resource for multiple times and concurrently delete or create a storage resource.
-   Note 2: If the user's container platform is deployed in a virtualization environment, only iSCSI networking is supported.
-   Note 3: If NVMe over RoCE or NVMe over FC is used, the version of the nvme-cli tool on worker nodes must be 1.9 or later. To query the version, run the  **nvme version**  command.
-   Note 4: Only OceanStor Dorado 6.1.0 and later versions support NFS. Only OceanStor Dorado 6.1.3 and later versions support NFS 4.1. OceanStor Dorado 6.1.7 and later versions support NFS over RDMA.
-   Note 5: The provisioned PVC whose  **volumeType**  is  **lun**  and  **accessModes**  is  **ReadOnlyMany**  does not support capacity expansion.
-   Note 6: Only system users can configure QoS.
-   Note 7: Only the active-active \(AA\) mode is supported.
-   Note 8: Only OceanStor Dorado 6.1.3 and later versions support multi-tenant.

Huawei CSI plug-in supports the following Dtree features for Huawei enterprise storage.

**Table  3**  Features supported by Dtree

<a name="table17535153417812"></a>
<table><thead align="left"><tr id="row753517341082"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p1053517341819"><a name="p1053517341819"></a><a name="p1053517341819"></a>Feature</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p453514341681"><a name="p453514341681"></a><a name="p453514341681"></a>Supported</p>
</th>
</tr>
</thead>
<tbody><tr id="row1541413531981"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p151mcpsimp"><a name="p151mcpsimp"></a><a name="p151mcpsimp"></a>Static Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p154mcpsimp"><a name="p154mcpsimp"></a><a name="p154mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row241417531381"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p157mcpsimp"><a name="p157mcpsimp"></a><a name="p157mcpsimp"></a>Dynamic Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p159mcpsimp"><a name="p159mcpsimp"></a><a name="p159mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row341412531489"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p162mcpsimp"><a name="p162mcpsimp"></a><a name="p162mcpsimp"></a>Expand Persistent Volume</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p165mcpsimp"><a name="p165mcpsimp"></a><a name="p165mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row104141753384"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p168mcpsimp"><a name="p168mcpsimp"></a><a name="p168mcpsimp"></a>Access Mode</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p170mcpsimp"><a name="p170mcpsimp"></a><a name="p170mcpsimp"></a>√ (RWX/RWO/ROX/RWOP: Kubernetes 1.22 or later supports RWOP.)</p>
</td>
</tr>
<tr id="row7414145315813"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p174mcpsimp"><a name="p174mcpsimp"></a><a name="p174mcpsimp"></a>Multi-tenancy</p>
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
<tr id="row2041411533814"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p194mcpsimp"><a name="p194mcpsimp"></a><a name="p194mcpsimp"></a>Clone Persistent Volume</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p197mcpsimp"><a name="p197mcpsimp"></a><a name="p197mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row1441414539814"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p200mcpsimp"><a name="p200mcpsimp"></a><a name="p200mcpsimp"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p202mcpsimp"><a name="p202mcpsimp"></a><a name="p202mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row04141953984"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p205mcpsimp"><a name="p205mcpsimp"></a><a name="p205mcpsimp"></a>Volume HyperMetro</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p207mcpsimp"><a name="p207mcpsimp"></a><a name="p207mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row84129531881"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p210mcpsimp"><a name="p210mcpsimp"></a><a name="p210mcpsimp"></a>Application type</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p212mcpsimp"><a name="p212mcpsimp"></a><a name="p212mcpsimp"></a>X</p>
</td>
</tr>
</tbody>
</table>

**Table  4**  Huawei storage versions supported by Dtree

<a name="table120mcpsimp"></a>
<table><thead align="left"><tr id="row126mcpsimp"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p128mcpsimp"><a name="p128mcpsimp"></a><a name="p128mcpsimp"></a>Storage Product</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p130mcpsimp"><a name="p130mcpsimp"></a><a name="p130mcpsimp"></a>Version</p>
</th>
</tr>
</thead>
<tbody><tr id="row132mcpsimp"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p134mcpsimp"><a name="p134mcpsimp"></a><a name="p134mcpsimp"></a>OceanStor Dorado</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p136mcpsimp"><a name="p136mcpsimp"></a><a name="p136mcpsimp"></a>6.1.0, 6.1.2, 6.1.3, 6.1.5, 6.1.6, 6.1.7, 6.1.8</p>
</td>
</tr>
</tbody>
</table>

