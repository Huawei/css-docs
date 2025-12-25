---
title: "华为CSI"
linkTitle: "华为CSI"
description: 
weight: 1
---

**表 1**  华为存储支持的特性及约束

<a name="table14995183994515"></a>
<table><thead align="left"><tr id="row6996173914451"><th class="cellrowborder" valign="top" width="20.192019201920193%" id="mcps1.2.5.1.1"><p id="p199961439154519"><a name="p199961439154519"></a><a name="p199961439154519"></a>特性</p>
</th>
<th class="cellrowborder" valign="top" width="21.98219821982198%" id="mcps1.2.5.1.2"><p id="p09961739124513"><a name="p09961739124513"></a><a name="p09961739124513"></a>OceanStor V5</p>
</th>
<th class="cellrowborder" valign="top" width="29.282928292829286%" id="mcps1.2.5.1.3"><p id="p1699615397457"><a name="p1699615397457"></a><a name="p1699615397457"></a>OceanStor</p>
</th>
<th class="cellrowborder" valign="top" width="28.542854285428543%" id="mcps1.2.5.1.4"><p id="p11601298188"><a name="p11601298188"></a><a name="p11601298188"></a>OceanStor Dorado</p>
</th>
</tr>
</thead>
<tbody><tr id="row1899683984519"><td class="cellrowborder" valign="top" width="20.192019201920193%" headers="mcps1.2.5.1.1 "><p id="p899653994514"><a name="p899653994514"></a><a name="p899653994514"></a><span>Static Provisioning</span></p>
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
<tr id="row8996539144513"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p49961939194517"><a name="p49961939194517"></a><a name="p49961939194517"></a><span>Expand Persistent Volume</span></p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><a name="ul39682022151411"></a><a name="ul39682022151411"></a><ul id="ul39682022151411"><li><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</li><li>发放的volumeType为lun且accessModes为ReadOnlyMany的PVC不支持扩容</li></ul>
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
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p149971339154511"><a name="p149971339154511"></a><a name="p149971339154511"></a>支持</p>
</td>
</tr>
<tr id="row19976393452"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1799710394452"><a name="p1799710394452"></a><a name="p1799710394452"></a>Clone <span>Persistent Volume</span></p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p197114535118"><a name="p197114535118"></a><a name="p197114535118"></a><span>支持</span>使用Dynamic Provisioning，Manage Provisioning方式创建的卷</p>
</td>
</tr>
<tr id="row253813281571"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p105391828872"><a name="p105391828872"></a><a name="p105391828872"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p7539162811719"><a name="p7539162811719"></a><a name="p7539162811719"></a>支持</p>
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
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><a name="ul1819361818817"></a><a name="ul1819361818817"></a><ul id="ul1819361818817"><li><span>RWO/ROX/RWOP：</span>支持，<span>RWOP</span>需<span>Kubernetes 1.22</span>版本以上支持。</li><li><span>RWX</span>：仅Raw Block卷支持</li></ul>
</td>
</tr>
<tr id="row4749123262619"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p274993211262"><a name="p274993211262"></a><a name="p274993211262"></a>QoS</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p19749123216264"><a name="p19749123216264"></a><a name="p19749123216264"></a>支持，仅系统用户支持配置QoS</p>
</td>
</tr>
<tr id="row13606622132720"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1760612292716"><a name="p1760612292716"></a><a name="p1760612292716"></a>应用类型</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1960652212711"><a name="p1960652212711"></a><a name="p1960652212711"></a>不支持</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p1360619224273"><a name="p1360619224273"></a><a name="p1360619224273"></a>支持</p>
</td>
</tr>
<tr id="row17943182222817"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p79432225287"><a name="p79432225287"></a><a name="p79432225287"></a>卷双活</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p09431322152815"><a name="p09431322152815"></a><a name="p09431322152815"></a>不支持</p>
</td>
</tr>
<tr id="row8191849183619"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p81912491363"><a name="p81912491363"></a><a name="p81912491363"></a>存储多租户</p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p112016213919"><a name="p112016213919"></a><a name="p112016213919"></a>不支持</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>-   若客户的容器平台部署在虚拟化平台上，CSI对接SAN存储时建议使用iSCSI协议。
>-   若客户要求使用FC/NVMe over FC/NVMe over RoCE协议，需要对虚拟化平台进行特定配置，需客户侧的虚拟化团队提供技术支持。
>-   使用NVMe over RoCE或NVMe over FC时，支持的nvme-cli工具版本为1.9及以上，查询命令为：nvme version。

