---
title: "PVC Parameters for Dynamic Volume Provisioning"
linkTitle: "PVC Parameters for Dynamic Volume Provisioning"
description: 
weight: 3
---

After configuring a StorageClass, you can use the StorageClass to configure a PVC. For details about the PVC configuration template, see example file  **pvc**_\*_**.yaml**  in the  **examples**  directory in Huawei CSI software package.

**Table  1**  Parameters in the pvc\*.yaml file

<a name="en-us_topic_0150885187_table195731435604"></a>
<table><thead align="left"><tr id="en-us_topic_0150885187_row35732351904"><th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.1"><p id="en-us_topic_0150885187_p1257333517017"><a name="en-us_topic_0150885187_p1257333517017"></a><a name="en-us_topic_0150885187_p1257333517017"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26%" id="mcps1.2.6.1.2"><p id="en-us_topic_0150885187_p1457323512015"><a name="en-us_topic_0150885187_p1457323512015"></a><a name="en-us_topic_0150885187_p1457323512015"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.3"><p id="p1173514981420"><a name="p1173514981420"></a><a name="p1173514981420"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="12%" id="mcps1.2.6.1.4"><p id="p1589881291419"><a name="p1589881291419"></a><a name="p1589881291419"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="34%" id="mcps1.2.6.1.5"><p id="en-us_topic_0150885187_p85734352017"><a name="en-us_topic_0150885187_p85734352017"></a><a name="en-us_topic_0150885187_p85734352017"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0150885187_row5573635907"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p3573335305"><a name="en-us_topic_0150885187_p3573335305"></a><a name="en-us_topic_0150885187_p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p205736355017"><a name="en-us_topic_0150885187_p205736355017"></a><a name="en-us_topic_0150885187_p205736355017"></a>User-defined name of a PVC object.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p7736109151413"><a name="p7736109151413"></a><a name="p7736109151413"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p1589841231412"><a name="p1589841231412"></a><a name="p1589841231412"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0150885187_p179301591191"><a name="en-us_topic_0150885187_p179301591191"></a><a name="en-us_topic_0150885187_p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row696316316238"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p1896393118231"><a name="en-us_topic_0150885187_p1896393118231"></a><a name="en-us_topic_0150885187_p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p1610614478451"><a name="p1610614478451"></a><a name="p1610614478451"></a>Volume mode. This parameter is optional. When LUN volumes are used, the following types are supported:</p>
<a name="ul823916101324"></a><a name="ul823916101324"></a><ul id="ul823916101324"><li><strong id="b899015017514"><a name="b899015017514"></a><a name="b899015017514"></a>Filesystem</strong>: local file system.</li><li><strong id="b14568105754"><a name="b14568105754"></a><a name="b14568105754"></a>Block</strong>: raw device.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p1373612911410"><a name="p1373612911410"></a><a name="p1373612911410"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p0898191211148"><a name="p0898191211148"></a><a name="p0898191211148"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="34%" headers="mcps1.2.6.1.5 "><p id="p62045214421"><a name="p62045214421"></a><a name="p62045214421"></a>This parameter takes effect when a PV is mounted. The default value is <strong id="b1897751416513"><a name="b1897751416513"></a><a name="b1897751416513"></a>Filesystem</strong>.</p>
<a name="ul1518211174214"></a><a name="ul1518211174214"></a><ul id="ul1518211174214"><li><strong id="b834212453617"><a name="b834212453617"></a><a name="b834212453617"></a>Filesystem</strong> indicates that a container accesses a PV using a local file system. The local file system type is specified by the <strong id="b17483535103618"><a name="b17483535103618"></a><a name="b17483535103618"></a>fsType</strong> field in the specified StorageClass. Storage of the Dtree type also uses this parameter.</li><li><strong id="b131506591954"><a name="b131506591954"></a><a name="b131506591954"></a>Block</strong> indicates that a PV is accessed in raw volume mode.</li></ul>
</td>
</tr>
<tr id="en-us_topic_0150885187_row25733352019"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p357320351304"><a name="en-us_topic_0150885187_p357320351304"></a><a name="en-us_topic_0150885187_p357320351304"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p135732351909"><a name="en-us_topic_0150885187_p135732351909"></a><a name="en-us_topic_0150885187_p135732351909"></a>Name of the StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p127361496143"><a name="p127361496143"></a><a name="p127361496143"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p1989831211414"><a name="p1989831211414"></a><a name="p1989831211414"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34%" headers="mcps1.2.6.1.5 "><p id="p1521791621216"><a name="p1521791621216"></a><a name="p1521791621216"></a>Name of the StorageClass object required by services.</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row1157316351102"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p9573035309"><a name="en-us_topic_0150885187_p9573035309"></a><a name="en-us_topic_0150885187_p9573035309"></a>spec.resources.requests.storage</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p1573183510015"><a name="en-us_topic_0150885187_p1573183510015"></a><a name="en-us_topic_0150885187_p1573183510015"></a>Size of the volume to be created. The format is ***Gi and the unit is GiB. The size must be an integer multiple of 512 bytes.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p87363981412"><a name="p87363981412"></a><a name="p87363981412"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p489841251410"><a name="p489841251410"></a><a name="p489841251410"></a>10Gi</p>
</td>
<td class="cellrowborder" valign="top" width="34%" headers="mcps1.2.6.1.5 "><p id="p1525217519276"><a name="p1525217519276"></a><a name="p1525217519276"></a>The PVC capacity depends on storage specifications and host specifications. For example, OceanStor Dorado 6.1.2 or OceanStor Pacific series 8.1.0 is connected to CentOS 7. If ext4 file systems are used, see <a href="#en-us_topic_0150885187_table178824527142">Table 2</a>. If XFS file systems are used, see <a href="#en-us_topic_0150885187_table101951367104">Table 3</a>. If NFS or raw devices are used, the capacity must meet the specifications of the used Huawei storage device model and version.</p>
<p id="p63667162711"><a name="p63667162711"></a><a name="p63667162711"></a>If the PVC capacity does not meet the specifications, a PVC or Pod may fail to be created due to the limitations of storage specifications or host file system specifications.</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row6573635502"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p1657333515012"><a name="en-us_topic_0150885187_p1657333515012"></a><a name="en-us_topic_0150885187_p1657333515012"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="26%" headers="mcps1.2.6.1.2 "><p id="p51122302293"><a name="p51122302293"></a><a name="p51122302293"></a>Access mode of the volume.</p>
<a name="ul69743301323"></a><a name="ul69743301323"></a><ul id="ul69743301323"><li><strong id="b1777118191889"><a name="b1777118191889"></a><a name="b1777118191889"></a>RWO</strong> (ReadWriteOnce): A volume can be mounted to a node in read/write mode. This mode also allows multiple Pods running on the same node to access the volume.</li><li><strong id="b143841840999"><a name="b143841840999"></a><a name="b143841840999"></a>ROX</strong> (ReadOnlyMany): A volume can be mounted to multiple nodes in read-only mode.</li><li><strong id="b184245131017"><a name="b184245131017"></a><a name="b184245131017"></a>RWX</strong> (ReadWriteMany): A volume can be mounted to multiple nodes in read/write mode.</li><li><strong id="b14167203017109"><a name="b14167203017109"></a><a name="b14167203017109"></a>RWOP</strong> (ReadWriteOncePod): A volume can only be mounted to a single Pod in read/write mode. Kubernetes 1.22 and later versions support this feature.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p87361891145"><a name="p87361891145"></a><a name="p87361891145"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p1589841251413"><a name="p1589841251413"></a><a name="p1589841251413"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="34%" headers="mcps1.2.6.1.5 "><a name="ul16793434324"></a><a name="ul16793434324"></a><ul id="ul16793434324"><li>RWO/ROX/RWOP: supported by all types of volumes. RWOP is supported only by Kubernetes 1.22 and later versions. For versions earlier than Kubernetes 1.29, you need to enable this feature by following the instructions in <a href="/css-docs/en/v4.6.0/common-operations/enabling-the-readwriteoncepod-feature-gate">Enabling the ReadWriteOncePod Feature Gate</a>.</li><li>The support for RWX is as follows:<a name="ul201701421154515"></a><a name="ul201701421154515"></a><ul id="ul201701421154515"><li><a href="/css-docs/en/v4.6.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#li277121152812">NAS storage</a>: supported by all volumes</li><li><a href="/css-docs/en/v4.6.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#en-us_topic_0000001324610777_li5135242193418">SAN storage</a>: supported only by volumes whose <strong id="b143575715820"><a name="b143575715820"></a><a name="b143575715820"></a>volumeMode</strong> is set to <strong id="b13525711580"><a name="b13525711580"></a><a name="b13525711580"></a>Block</strong></li></ul>
</li></ul>
</td>
</tr>
</tbody>
</table>

**Table  2**  ext4 capacity specifications

<a name="en-us_topic_0150885187_table178824527142"></a>
<table><thead align="left"><tr id="en-us_topic_0150885187_row12882145215140"><th class="cellrowborder" valign="top" width="33.23%" id="mcps1.2.5.1.1"><p id="en-us_topic_0150885187_p18826529140"><a name="en-us_topic_0150885187_p18826529140"></a><a name="en-us_topic_0150885187_p18826529140"></a>Storage Type</p>
</th>
<th class="cellrowborder" valign="top" width="19.89%" id="mcps1.2.5.1.2"><p id="en-us_topic_0150885187_p28820526146"><a name="en-us_topic_0150885187_p28820526146"></a><a name="en-us_topic_0150885187_p28820526146"></a>Storage Specifications</p>
</th>
<th class="cellrowborder" valign="top" width="23.44%" id="mcps1.2.5.1.3"><p id="en-us_topic_0150885187_p58821552161412"><a name="en-us_topic_0150885187_p58821552161412"></a><a name="en-us_topic_0150885187_p58821552161412"></a>ext4 Specifications</p>
</th>
<th class="cellrowborder" valign="top" width="23.44%" id="mcps1.2.5.1.4"><p id="en-us_topic_0150885187_p9882252201418"><a name="en-us_topic_0150885187_p9882252201418"></a><a name="en-us_topic_0150885187_p9882252201418"></a>CSI Specifications</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0150885187_row11882205261417"><td class="cellrowborder" valign="top" width="33.23%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0150885187_p1788211526142"><a name="en-us_topic_0150885187_p1788211526142"></a><a name="en-us_topic_0150885187_p1788211526142"></a>OceanStor Dorado</p>
</td>
<td class="cellrowborder" valign="top" width="19.89%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0150885187_p265163441310"><a name="en-us_topic_0150885187_p265163441310"></a><a name="en-us_topic_0150885187_p265163441310"></a>512 Ki to 256 Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.44%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0150885187_p1988245219141"><a name="en-us_topic_0150885187_p1988245219141"></a><a name="en-us_topic_0150885187_p1988245219141"></a>50 Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.44%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0150885187_p15882185241416"><a name="en-us_topic_0150885187_p15882185241416"></a><a name="en-us_topic_0150885187_p15882185241416"></a>512 Ki to 50 Ti</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row1230184492014"><td class="cellrowborder" valign="top" width="33.23%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0150885187_p9499133571212"><a name="en-us_topic_0150885187_p9499133571212"></a><a name="en-us_topic_0150885187_p9499133571212"></a>OceanStor Pacific series</p>
</td>
<td class="cellrowborder" valign="top" width="19.89%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0150885187_p7650193417133"><a name="en-us_topic_0150885187_p7650193417133"></a><a name="en-us_topic_0150885187_p7650193417133"></a>64 Mi to 512 Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.44%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0150885187_p1424338151414"><a name="en-us_topic_0150885187_p1424338151414"></a><a name="en-us_topic_0150885187_p1424338151414"></a>50 Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.44%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0150885187_p138617554183"><a name="en-us_topic_0150885187_p138617554183"></a><a name="en-us_topic_0150885187_p138617554183"></a>64 Mi to 50 Ti</p>
</td>
</tr>
</tbody>
</table>

**Table  3**  XFS capacity specifications

<a name="en-us_topic_0150885187_table101951367104"></a>
<table><thead align="left"><tr id="en-us_topic_0150885187_row17195566105"><th class="cellrowborder" valign="top" width="33.07330733073307%" id="mcps1.2.5.1.1"><p id="en-us_topic_0150885187_p51951067101"><a name="en-us_topic_0150885187_p51951067101"></a><a name="en-us_topic_0150885187_p51951067101"></a>Storage Type</p>
</th>
<th class="cellrowborder" valign="top" width="20.412041204120417%" id="mcps1.2.5.1.2"><p id="en-us_topic_0150885187_p141951062104"><a name="en-us_topic_0150885187_p141951062104"></a><a name="en-us_topic_0150885187_p141951062104"></a>Storage Specifications</p>
</th>
<th class="cellrowborder" valign="top" width="23.512351235123514%" id="mcps1.2.5.1.3"><p id="en-us_topic_0150885187_p17195136151010"><a name="en-us_topic_0150885187_p17195136151010"></a><a name="en-us_topic_0150885187_p17195136151010"></a>XFS Specifications</p>
</th>
<th class="cellrowborder" valign="top" width="23.002300230023007%" id="mcps1.2.5.1.4"><p id="en-us_topic_0150885187_p1819520616108"><a name="en-us_topic_0150885187_p1819520616108"></a><a name="en-us_topic_0150885187_p1819520616108"></a>CSI Specifications</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0150885187_row12195156161015"><td class="cellrowborder" valign="top" width="33.07330733073307%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0150885187_p1919526121011"><a name="en-us_topic_0150885187_p1919526121011"></a><a name="en-us_topic_0150885187_p1919526121011"></a>OceanStor Dorado</p>
</td>
<td class="cellrowborder" valign="top" width="20.412041204120417%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0150885187_p131951613101"><a name="en-us_topic_0150885187_p131951613101"></a><a name="en-us_topic_0150885187_p131951613101"></a>512 Ki to 256 Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.512351235123514%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0150885187_p919518613107"><a name="en-us_topic_0150885187_p919518613107"></a><a name="en-us_topic_0150885187_p919518613107"></a>500 Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.002300230023007%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0150885187_p15195865109"><a name="en-us_topic_0150885187_p15195865109"></a><a name="en-us_topic_0150885187_p15195865109"></a>512 Ki to 500 Ti</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row171951969107"><td class="cellrowborder" valign="top" width="33.07330733073307%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0150885187_p1519514631010"><a name="en-us_topic_0150885187_p1519514631010"></a><a name="en-us_topic_0150885187_p1519514631010"></a>OceanStor Pacific series</p>
</td>
<td class="cellrowborder" valign="top" width="20.412041204120417%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0150885187_p1619519612104"><a name="en-us_topic_0150885187_p1619519612104"></a><a name="en-us_topic_0150885187_p1619519612104"></a>64 Mi to 512 Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.512351235123514%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0150885187_p171963681017"><a name="en-us_topic_0150885187_p171963681017"></a><a name="en-us_topic_0150885187_p171963681017"></a>500 Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.002300230023007%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0150885187_p3196126121011"><a name="en-us_topic_0150885187_p3196126121011"></a><a name="en-us_topic_0150885187_p3196126121011"></a>64 Mi to 500 Ti</p>
</td>
</tr>
</tbody>
</table>

