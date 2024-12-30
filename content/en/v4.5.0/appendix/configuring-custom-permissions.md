---
title: "Configuring Custom Permissions"
linkTitle: "Configuring Custom Permissions"
description: 
weight: 5
---

## User-defined Role Configurations{#section366214517918}

For different storage resources, refer to the following configurations:

-   For NAS resources, configure the minimum permissions by referring to  [Table 1](#table66121923174916).
-   For SAN resources, configure the minimum permissions by referring to  [Table 2](#table51362243359).

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>For details about how to configure permissions for user-defined roles, see  [OceanStor Dorado 6000, Dorado 18000 Series Product Documentation](https://support.huawei.com/hedex/hdx.do?docid=EDOC1100214756&id=EN-US_TOPIC_0000001640708705&lang=en).

**Table  1**  Minimum permissions for NAS resources

<a name="table66121923174916"></a>
<table><thead align="left"><tr id="row1612162310490"><th class="cellrowborder" valign="top" width="21.967803219678032%" id="mcps1.2.5.1.1"><p id="p166121323144918"><a name="p166121323144918"></a><a name="p166121323144918"></a>Permission Object</p>
</th>
<th class="cellrowborder" valign="top" width="29.007099290070997%" id="mcps1.2.5.1.2"><p id="p11559358145215"><a name="p11559358145215"></a><a name="p11559358145215"></a>Parent Object</p>
</th>
<th class="cellrowborder" valign="top" width="18.1981801819818%" id="mcps1.2.5.1.3"><p id="p1612102310496"><a name="p1612102310496"></a><a name="p1612102310496"></a>Read/Write Permission</p>
</th>
<th class="cellrowborder" valign="top" width="30.826917308269174%" id="mcps1.2.5.1.4"><p id="p861292394912"><a name="p861292394912"></a><a name="p861292394912"></a>Function</p>
</th>
</tr>
</thead>
<tbody><tr id="row461218235491"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p15800171825819"><a name="p15800171825819"></a><a name="p15800171825819"></a>workload_type</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p028032475815"><a name="p028032475815"></a><a name="p028032475815"></a>file_storage_service</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p1531915352582"><a name="p1531915352582"></a><a name="p1531915352582"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p0741144175820"><a name="p0741144175820"></a><a name="p0741144175820"></a>Queries the workload type.</p>
</td>
</tr>
<tr id="row15613122317494"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p3800518205819"><a name="p3800518205819"></a><a name="p3800518205819"></a>file_system</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p2280824105812"><a name="p2280824105812"></a><a name="p2280824105812"></a>file_storage_service</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p1231973575817"><a name="p1231973575817"></a><a name="p1231973575817"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p774194116586"><a name="p774194116586"></a><a name="p774194116586"></a>Manages file systems.</p>
</td>
</tr>
<tr id="row133271317296"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p1780031875813"><a name="p1780031875813"></a><a name="p1780031875813"></a>fs_snapshot</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p18280162420586"><a name="p18280162420586"></a><a name="p18280162420586"></a>file_storage_service</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p231983511582"><a name="p231983511582"></a><a name="p231983511582"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p97410411589"><a name="p97410411589"></a><a name="p97410411589"></a>Manages file system snapshots.</p>
</td>
</tr>
<tr id="row189011018135012"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p480091835810"><a name="p480091835810"></a><a name="p480091835810"></a>quota</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p172800244581"><a name="p172800244581"></a><a name="p172800244581"></a>file_storage_service</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p14319133555819"><a name="p14319133555819"></a><a name="p14319133555819"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p127411241155812"><a name="p127411241155812"></a><a name="p127411241155812"></a>Manages file system quotas.</p>
</td>
</tr>
<tr id="row184220812291"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p1180020187580"><a name="p1180020187580"></a><a name="p1180020187580"></a>nfs_service</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p1828072413585"><a name="p1828072413585"></a><a name="p1828072413585"></a>file_storage_service</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p33197358587"><a name="p33197358587"></a><a name="p33197358587"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p274144165819"><a name="p274144165819"></a><a name="p274144165819"></a>Queries NFS services.</p>
</td>
</tr>
<tr id="row1072519161290"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p1280051865818"><a name="p1280051865818"></a><a name="p1280051865818"></a>share</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p15280182465811"><a name="p15280182465811"></a><a name="p15280182465811"></a>file_storage_service</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p53191235175817"><a name="p53191235175817"></a><a name="p53191235175817"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p157411141145814"><a name="p157411141145814"></a><a name="p157411141145814"></a>Manages NFS shares.</p>
</td>
</tr>
<tr id="row8401220142914"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p1280021815813"><a name="p1280021815813"></a><a name="p1280021815813"></a>dtree</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p132802024115820"><a name="p132802024115820"></a><a name="p132802024115820"></a>file_storage_service</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p931943517580"><a name="p931943517580"></a><a name="p931943517580"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p197411341165819"><a name="p197411341165819"></a><a name="p197411341165819"></a>Manages dtrees.</p>
</td>
</tr>
<tr id="row6711112282918"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p2080031845810"><a name="p2080031845810"></a><a name="p2080031845810"></a>hyper_metro_pair</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p192808245586"><a name="p192808245586"></a><a name="p192808245586"></a>hyper_metro</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p43191435165812"><a name="p43191435165812"></a><a name="p43191435165812"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p18741194155810"><a name="p18741194155810"></a><a name="p18741194155810"></a>Creates file system HyperMetro pairs.</p>
</td>
</tr>
<tr id="row1384682811295"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p58006183582"><a name="p58006183582"></a><a name="p58006183582"></a>hyper_metro_domain</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p132801524185816"><a name="p132801524185816"></a><a name="p132801524185816"></a>hyper_metro</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p2031983545816"><a name="p2031983545816"></a><a name="p2031983545816"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p107411841175819"><a name="p107411841175819"></a><a name="p107411841175819"></a>Queries information about file system HyperMetro domains.</p>
</td>
</tr>
<tr id="row1660510710431"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p3800151818586"><a name="p3800151818586"></a><a name="p3800151818586"></a>remote_device</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p128092411589"><a name="p128092411589"></a><a name="p128092411589"></a>local_data_protection</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p203196351587"><a name="p203196351587"></a><a name="p203196351587"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p6741164145811"><a name="p6741164145811"></a><a name="p6741164145811"></a>Queries remote device information.</p>
</td>
</tr>
<tr id="row16483417151719"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p1680017189584"><a name="p1680017189584"></a><a name="p1680017189584"></a>storage_pool</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p1428012435811"><a name="p1428012435811"></a><a name="p1428012435811"></a>pool</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p15319935185818"><a name="p15319935185818"></a><a name="p15319935185818"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p97410413588"><a name="p97410413588"></a><a name="p97410413588"></a>Queries storage pool information.</p>
</td>
</tr>
<tr id="row15552195717479"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p1680012189585"><a name="p1680012189585"></a><a name="p1680012189585"></a>smart_qos</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p1928072419585"><a name="p1928072419585"></a><a name="p1928072419585"></a>resource_performance_tuning</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p1731923511582"><a name="p1731923511582"></a><a name="p1731923511582"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p874113412581"><a name="p874113412581"></a><a name="p874113412581"></a>Manages SmartQoS policies.</p>
</td>
</tr>
<tr id="row77444516397"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p180021845818"><a name="p180021845818"></a><a name="p180021845818"></a>system</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p32801724145814"><a name="p32801724145814"></a><a name="p32801724145814"></a>system</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p53191357583"><a name="p53191357583"></a><a name="p53191357583"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p13741341175813"><a name="p13741341175813"></a><a name="p13741341175813"></a>Queries storage device information (this object needs to be configured only when the owning group is the system group).</p>
</td>
</tr>
<tr id="row4116121513515"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p1280091810589"><a name="p1280091810589"></a><a name="p1280091810589"></a>vstore</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p192806244585"><a name="p192806244585"></a><a name="p192806244585"></a>vstore</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p1231953555810"><a name="p1231953555810"></a><a name="p1231953555810"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p127417412584"><a name="p127417412584"></a><a name="p127417412584"></a>Queries vStore information.</p>
</td>
</tr>
<tr id="row1041646183410"><td class="cellrowborder" valign="top" width="21.967803219678032%" headers="mcps1.2.5.1.1 "><p id="p1392344963412"><a name="p1392344963412"></a><a name="p1392344963412"></a>port</p>
</td>
<td class="cellrowborder" valign="top" width="29.007099290070997%" headers="mcps1.2.5.1.2 "><p id="p992374916346"><a name="p992374916346"></a><a name="p992374916346"></a>network</p>
</td>
<td class="cellrowborder" valign="top" width="18.1981801819818%" headers="mcps1.2.5.1.3 "><p id="p179231649173415"><a name="p179231649173415"></a><a name="p179231649173415"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.826917308269174%" headers="mcps1.2.5.1.4 "><p id="p1392334963419"><a name="p1392334963419"></a><a name="p1392334963419"></a>Queries logical port information.</p>
</td>
</tr>
</tbody>
</table>

**Table  2**  Minimum permissions for SAN resources

<a name="table51362243359"></a>
<table><thead align="left"><tr id="row1613618243354"><th class="cellrowborder" valign="top" width="21.897810218978098%" id="mcps1.2.5.1.1"><p id="p165151535193511"><a name="p165151535193511"></a><a name="p165151535193511"></a>Permission Object</p>
</th>
<th class="cellrowborder" valign="top" width="28.95710428957104%" id="mcps1.2.5.1.2"><p id="p24022055195516"><a name="p24022055195516"></a><a name="p24022055195516"></a>Parent Object</p>
</th>
<th class="cellrowborder" valign="top" width="18.30816918308169%" id="mcps1.2.5.1.3"><p id="p16515133518352"><a name="p16515133518352"></a><a name="p16515133518352"></a>Read/Write Permission</p>
</th>
<th class="cellrowborder" valign="top" width="30.836916308369155%" id="mcps1.2.5.1.4"><p id="p16515335133516"><a name="p16515335133516"></a><a name="p16515335133516"></a>Function</p>
</th>
</tr>
</thead>
<tbody><tr id="row13136142417353"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p78979195591"><a name="p78979195591"></a><a name="p78979195591"></a>remote_device</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p123961128105915"><a name="p123961128105915"></a><a name="p123961128105915"></a>local_data_protection</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p34361934185916"><a name="p34361934185916"></a><a name="p34361934185916"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p557634013597"><a name="p557634013597"></a><a name="p557634013597"></a>Queries remote device information.</p>
</td>
</tr>
<tr id="row613692413518"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p98973193597"><a name="p98973193597"></a><a name="p98973193597"></a>hyper_clone</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p239622875910"><a name="p239622875910"></a><a name="p239622875910"></a>local_data_protection</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p18436153425916"><a name="p18436153425916"></a><a name="p18436153425916"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p1357615400599"><a name="p1357615400599"></a><a name="p1357615400599"></a>Manages clone pairs.</p>
</td>
</tr>
<tr id="row213692411351"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p889710193599"><a name="p889710193599"></a><a name="p889710193599"></a>lun_snapshot</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p73961928165918"><a name="p73961928165918"></a><a name="p73961928165918"></a>local_data_protection</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p843619345597"><a name="p843619345597"></a><a name="p843619345597"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p55761040155919"><a name="p55761040155919"></a><a name="p55761040155919"></a>Manages LUN snapshots.</p>
</td>
</tr>
<tr id="row192988133513"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p689711912592"><a name="p689711912592"></a><a name="p689711912592"></a>workload_type</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p83967282593"><a name="p83967282593"></a><a name="p83967282593"></a>lun</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p74361034115914"><a name="p74361034115914"></a><a name="p74361034115914"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p45767402590"><a name="p45767402590"></a><a name="p45767402590"></a>Queries the workload type.</p>
</td>
</tr>
<tr id="row151368247352"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p19897101915917"><a name="p19897101915917"></a><a name="p19897101915917"></a>lun</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p103961428185916"><a name="p103961428185916"></a><a name="p103961428185916"></a>lun</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p11436163410593"><a name="p11436163410593"></a><a name="p11436163410593"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p75764406597"><a name="p75764406597"></a><a name="p75764406597"></a>Manages LUNs.</p>
</td>
</tr>
<tr id="row0136524113514"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p989713193592"><a name="p989713193592"></a><a name="p989713193592"></a>host</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p18396828195919"><a name="p18396828195919"></a><a name="p18396828195919"></a>mapping_view</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p34361434145911"><a name="p34361434145911"></a><a name="p34361434145911"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p45763403593"><a name="p45763403593"></a><a name="p45763403593"></a>Manages hosts.</p>
</td>
</tr>
<tr id="row8334715363"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p10897131995911"><a name="p10897131995911"></a><a name="p10897131995911"></a>host_group</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p193968286597"><a name="p193968286597"></a><a name="p193968286597"></a>mapping_view</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p164366347595"><a name="p164366347595"></a><a name="p164366347595"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p1257674095914"><a name="p1257674095914"></a><a name="p1257674095914"></a>Manages host groups.</p>
</td>
</tr>
<tr id="row96239106365"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p9897201918592"><a name="p9897201918592"></a><a name="p9897201918592"></a>initiator</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p15396128175913"><a name="p15396128175913"></a><a name="p15396128175913"></a>mapping_view</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p443633465910"><a name="p443633465910"></a><a name="p443633465910"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p1157624025915"><a name="p1157624025915"></a><a name="p1157624025915"></a>Manages initiators.</p>
</td>
</tr>
<tr id="row1567081723612"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p48971019155913"><a name="p48971019155913"></a><a name="p48971019155913"></a>lun_group</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p1539618282592"><a name="p1539618282592"></a><a name="p1539618282592"></a>mapping_view</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p17436113412595"><a name="p17436113412595"></a><a name="p17436113412595"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p125761340175914"><a name="p125761340175914"></a><a name="p125761340175914"></a>Manages LUN groups.</p>
</td>
</tr>
<tr id="row19858131563616"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p2897919145918"><a name="p2897919145918"></a><a name="p2897919145918"></a>mapping_view</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p039632818599"><a name="p039632818599"></a><a name="p039632818599"></a>mapping_view</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p14436133412592"><a name="p14436133412592"></a><a name="p14436133412592"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p2057614409591"><a name="p2057614409591"></a><a name="p2057614409591"></a>Manages mapping views.</p>
</td>
</tr>
<tr id="row1330101243617"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p1489741914598"><a name="p1489741914598"></a><a name="p1489741914598"></a>target</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p13396192865919"><a name="p13396192865919"></a><a name="p13396192865919"></a>mapping_view</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p1436103435912"><a name="p1436103435912"></a><a name="p1436103435912"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p457613407592"><a name="p457613407592"></a><a name="p457613407592"></a>Queries iSCSI initiators.</p>
</td>
</tr>
<tr id="row1197715816362"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p98975190599"><a name="p98975190599"></a><a name="p98975190599"></a>port</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p1739662816594"><a name="p1739662816594"></a><a name="p1739662816594"></a>network</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p184361344594"><a name="p184361344594"></a><a name="p184361344594"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p357614075919"><a name="p357614075919"></a><a name="p357614075919"></a>Queries logical ports.</p>
</td>
</tr>
<tr id="row79492130362"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p2897101910594"><a name="p2897101910594"></a><a name="p2897101910594"></a>storage_pool</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p8396172895919"><a name="p8396172895919"></a><a name="p8396172895919"></a>pool</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p144369341599"><a name="p144369341599"></a><a name="p144369341599"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p25767405595"><a name="p25767405595"></a><a name="p25767405595"></a>Queries storage pool information.</p>
</td>
</tr>
<tr id="row813682418355"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p389751975918"><a name="p389751975918"></a><a name="p389751975918"></a>smart_qos</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p43961528145919"><a name="p43961528145919"></a><a name="p43961528145919"></a>resource_performance_tuning</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p7436173419597"><a name="p7436173419597"></a><a name="p7436173419597"></a>Read and write</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p16576114019590"><a name="p16576114019590"></a><a name="p16576114019590"></a>Manages SmartQoS policies.</p>
</td>
</tr>
<tr id="row91361624183520"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p208971519105914"><a name="p208971519105914"></a><a name="p208971519105914"></a>system</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p14396628155920"><a name="p14396628155920"></a><a name="p14396628155920"></a>system</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p114361347597"><a name="p114361347597"></a><a name="p114361347597"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p6576840185916"><a name="p6576840185916"></a><a name="p6576840185916"></a>Queries storage device information (this object needs to be configured only when the owning group is the system group).</p>
</td>
</tr>
<tr id="row837403919498"><td class="cellrowborder" valign="top" width="21.897810218978098%" headers="mcps1.2.5.1.1 "><p id="p4897171917591"><a name="p4897171917591"></a><a name="p4897171917591"></a>vstore</p>
</td>
<td class="cellrowborder" valign="top" width="28.95710428957104%" headers="mcps1.2.5.1.2 "><p id="p13396182805917"><a name="p13396182805917"></a><a name="p13396182805917"></a>vstore</p>
</td>
<td class="cellrowborder" valign="top" width="18.30816918308169%" headers="mcps1.2.5.1.3 "><p id="p34371334165916"><a name="p34371334165916"></a><a name="p34371334165916"></a>Read-only</p>
</td>
<td class="cellrowborder" valign="top" width="30.836916308369155%" headers="mcps1.2.5.1.4 "><p id="p12576164017592"><a name="p12576164017592"></a><a name="p12576164017592"></a>Queries vStore information.</p>
</td>
</tr>
</tbody>
</table>

