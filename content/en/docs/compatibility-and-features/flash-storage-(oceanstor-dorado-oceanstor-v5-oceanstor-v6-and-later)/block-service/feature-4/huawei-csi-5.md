---
title: "Huawei CSI"
linkTitle: "Huawei CSI"
description: 
weight: 1
---

**Table  1**  Features supported by Huawei storage and constraints

<a name="table14995183994515"></a>
<table><thead align="left"><tr id="row6996173914451"><th class="cellrowborder" valign="top" width="20.192019201920193%" id="mcps1.2.5.1.1"><p id="p199961439154519"><a name="p199961439154519"></a><a name="p199961439154519"></a>Feature</p>
</th>
<th class="cellrowborder" valign="top" width="21.98219821982198%" id="mcps1.2.5.1.2"><p id="p09961739124513"><a name="p09961739124513"></a><a name="p09961739124513"></a>OceanStor V5</p>
</th>
<th class="cellrowborder" valign="top" width="29.282928292829286%" id="mcps1.2.5.1.3"><p id="p1699615397457"><a name="p1699615397457"></a><a name="p1699615397457"></a>OceanStor</p>
</th>
<th class="cellrowborder" valign="top" width="28.542854285428543%" id="mcps1.2.5.1.4"><p id="p11601298188"><a name="p11601298188"></a><a name="p11601298188"></a>OceanStor Dorado</p>
</th>
</tr>
</thead>
<tbody><tr id="row1899683984519"><td class="cellrowborder" valign="top" width="20.192019201920193%" headers="mcps1.2.5.1.1 "><p id="p899653994514"><a name="p899653994514"></a><a name="p899653994514"></a>Static Provisioning</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="21.98219821982198%" headers="mcps1.2.5.1.2 "><p id="p86732141719"><a name="p86732141719"></a><a name="p86732141719"></a>FC/iSCSI</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="29.282928292829286%" headers="mcps1.2.5.1.3 "><p id="p12996173920456"><a name="p12996173920456"></a><a name="p12996173920456"></a>FC/iSCSI/NVMe over RoCE/NVMe over FC</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="28.542854285428543%" headers="mcps1.2.5.1.4 "><p id="p115594419186"><a name="p115594419186"></a><a name="p115594419186"></a>FC/iSCSI/NVMe over RoCE/NVMe over FC</p>
</td>
</tr>
<tr id="row49961039174517"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p9996173974516"><a name="p9996173974516"></a><a name="p9996173974516"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row55791517133218"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p3579151783219"><a name="p3579151783219"></a><a name="p3579151783219"></a>Manage Provisioning</p>
</td>
</tr>
<tr id="row8996539144513"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p49961939194517"><a name="p49961939194517"></a><a name="p49961939194517"></a>Expand Persistent Volume</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><a name="ul39682022151411"></a><a name="ul39682022151411"></a><ul id="ul39682022151411"><li>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</li><li>The provisioned PVC whose <strong id="b416913311425"><a name="b416913311425"></a><a name="b416913311425"></a>volumeType</strong> is <strong id="b12169193164215"><a name="b12169193164215"></a><a name="b12169193164215"></a>lun</strong> and <strong id="b101695394215"><a name="b101695394215"></a><a name="b101695394215"></a>accessModes</strong> is <strong id="b016919334210"><a name="b016919334210"></a><a name="b016919334210"></a>ReadOnlyMany</strong> does not support capacity expansion.</li></ul>
</td>
</tr>
<tr id="row14996173944518"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p280819372253"><a name="p280819372253"></a><a name="p280819372253"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p1771745145117"><a name="p1771745145117"></a><a name="p1771745145117"></a>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
</tr>
<tr id="row1599693916456"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p49961939184516"><a name="p49961939184516"></a><a name="p49961939184516"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p2996153934511"><a name="p2996153934511"></a><a name="p2996153934511"></a>Supported</p>
</td>
</tr>
<tr id="row15996173994516"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p15997133914455"><a name="p15997133914455"></a><a name="p15997133914455"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p149971339154511"><a name="p149971339154511"></a><a name="p149971339154511"></a>Supported</p>
</td>
</tr>
<tr id="row19976393452"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1799710394452"><a name="p1799710394452"></a><a name="p1799710394452"></a>Clone Persistent Volume</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p197114535118"><a name="p197114535118"></a><a name="p197114535118"></a>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
</tr>
<tr id="row253813281571"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p105391828872"><a name="p105391828872"></a><a name="p105391828872"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p7539162811719"><a name="p7539162811719"></a><a name="p7539162811719"></a>Supported</p>
</td>
</tr>
<tr id="row76671821015"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p146673811105"><a name="p146673811105"></a><a name="p146673811105"></a>Topology</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p18667138181019"><a name="p18667138181019"></a><a name="p18667138181019"></a>Supported</p>
</td>
</tr>
<tr id="row91081351378"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1423525343819"><a name="p1423525343819"></a><a name="p1423525343819"></a>Generic Ephemeral Volumes</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p2091319219390"><a name="p2091319219390"></a><a name="p2091319219390"></a>Supported</p>
</td>
</tr>
<tr id="row59655172115"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p996591717110"><a name="p996591717110"></a><a name="p996591717110"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><a name="ul1819361818817"></a><a name="ul1819361818817"></a><ul id="ul1819361818817"><li>RWO/ROX/RWOP: supported. RWOP is supported only in Kubernetes 1.22 or later.</li><li>RWX: supported only by Raw Block volumes</li></ul>
</td>
</tr>
<tr id="row4749123262619"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p274993211262"><a name="p274993211262"></a><a name="p274993211262"></a>QoS</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p19749123216264"><a name="p19749123216264"></a><a name="p19749123216264"></a>Supported. Only system users can configure QoS.</p>
</td>
</tr>
<tr id="row13606622132720"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1760612292716"><a name="p1760612292716"></a><a name="p1760612292716"></a>Application type</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1960652212711"><a name="p1960652212711"></a><a name="p1960652212711"></a>Not supported</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p1360619224273"><a name="p1360619224273"></a><a name="p1360619224273"></a>Supported</p>
</td>
</tr>
<tr id="row17943182222817"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p79432225287"><a name="p79432225287"></a><a name="p79432225287"></a>Volume HyperMetro</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p09431322152815"><a name="p09431322152815"></a><a name="p09431322152815"></a>Not supported</p>
</td>
</tr>
<tr id="row8191849183619"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p81912491363"><a name="p81912491363"></a><a name="p81912491363"></a>Storage multi-tenant</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p112016213919"><a name="p112016213919"></a><a name="p112016213919"></a>Not supported</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   If a container platform is deployed on a virtualization platform, you are advised to use the iSCSI protocol when the CSI is connected to SAN storage.
>-   If the customer requires the FC, NVMe over FC, or NVMe over RoCE protocol, the virtualization platform needs to be configured. In this case, the customer's virtualization team needs to provide technical support.
>-   When NVMe over RoCE or NVMe over FC is used, the supported nvme-cli tool version is 1.9 or later. To query the version, run the  **nvme version**  command.

