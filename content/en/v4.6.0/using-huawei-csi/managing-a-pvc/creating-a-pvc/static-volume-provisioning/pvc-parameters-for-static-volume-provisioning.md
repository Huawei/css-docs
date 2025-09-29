---
title: "PVC Parameters for Static Volume Provisioning"
linkTitle: "PVC Parameters for Static Volume Provisioning"
description: 
weight: 2
---

**Table  1**  PVC parameters

<a name="table195731435604"></a>
<table><thead align="left"><tr id="row35732351904"><th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.1"><p id="p1257333517017"><a name="p1257333517017"></a><a name="p1257333517017"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="27%" id="mcps1.2.6.1.2"><p id="p1457323512015"><a name="p1457323512015"></a><a name="p1457323512015"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="14.000000000000002%" id="mcps1.2.6.1.3"><p id="p1223918284404"><a name="p1223918284404"></a><a name="p1223918284404"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="12%" id="mcps1.2.6.1.4"><p id="p193751530154015"><a name="p193751530154015"></a><a name="p193751530154015"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="33%" id="mcps1.2.6.1.5"><p id="p85734352017"><a name="p85734352017"></a><a name="p85734352017"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row5573635907"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="p3573335305"><a name="p3573335305"></a><a name="p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p205736355017"><a name="p205736355017"></a><a name="p205736355017"></a>User-defined name of a PVC object.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p15360547910"><a name="p15360547910"></a><a name="p15360547910"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p1637510306406"><a name="p1637510306406"></a><a name="p1637510306406"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33%" headers="mcps1.2.6.1.5 "><p id="p179301591191"><a name="p179301591191"></a><a name="p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="row10874152212484"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p1657333515012"><a name="en-us_topic_0150885187_p1657333515012"></a><a name="en-us_topic_0150885187_p1657333515012"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p51122302293"><a name="p51122302293"></a><a name="p51122302293"></a>Access mode of the volume.</p>
<a name="ul18620120655"></a><a name="ul18620120655"></a><ul id="ul18620120655"><li><strong id="b2062211291309"><a name="b2062211291309"></a><a name="b2062211291309"></a>RWO</strong> (ReadWriteOnce): A volume can be mounted to a node in read/write mode. This mode also allows multiple Pods running on the same node to access the volume.</li><li><strong id="b682416318301"><a name="b682416318301"></a><a name="b682416318301"></a>ROX</strong> (ReadOnlyMany): A volume can be mounted to multiple nodes in read-only mode.</li><li><strong id="b13775173263019"><a name="b13775173263019"></a><a name="b13775173263019"></a>RWX</strong> (ReadWriteMany): A volume can be mounted to multiple nodes in read/write mode.</li><li><strong id="b19735193373016"><a name="b19735193373016"></a><a name="b19735193373016"></a>RWOP</strong> (ReadWriteOncePod): A volume can only be mounted to a single Pod in read/write mode. Kubernetes 1.22 and later versions support this feature.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p1823972854011"><a name="p1823972854011"></a><a name="p1823972854011"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p18375123074018"><a name="p18375123074018"></a><a name="p18375123074018"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="33%" headers="mcps1.2.6.1.5 "><a name="ul096872054"></a><a name="ul096872054"></a><ul id="ul096872054"><li>RWO/ROX/RWOP: supported by all types of volumes. RWOP is supported only by Kubernetes 1.22 and later versions. For versions earlier than Kubernetes 1.29, you need to enable this feature by following the instructions in <a href="/css-docs/en/v4.6.0/common-operations/enabling-the-readwriteoncepod-feature-gate">Enabling the ReadWriteOncePod Feature Gate</a>.</li><li>The support for RWX is as follows:<a name="ul201701421154515"></a><a name="ul201701421154515"></a><ul id="ul201701421154515"><li><a href="/css-docs/en/v4.6.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#li277121152812">NAS storage</a>: supported by all volumes</li><li><a href="/css-docs/en/v4.6.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#en-us_topic_0000001324610777_li5135242193418">SAN storage</a>: supported only by volumes whose <strong id="b554333115510"><a name="b554333115510"></a><a name="b554333115510"></a>volumeMode</strong> is set to <strong id="b155433316558"><a name="b155433316558"></a><a name="b155433316558"></a>Block</strong></li></ul>
</li></ul>
</td>
</tr>
<tr id="row696316316238"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="p1896393118231"><a name="p1896393118231"></a><a name="p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p1996311317238"><a name="p1996311317238"></a><a name="p1996311317238"></a>Volume mode.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p8239182864010"><a name="p8239182864010"></a><a name="p8239182864010"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p1237553064011"><a name="p1237553064011"></a><a name="p1237553064011"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="33%" headers="mcps1.2.6.1.5 "><p id="p10963143119234"><a name="p10963143119234"></a><a name="p10963143119234"></a>This parameter is optional. The value can be <strong id="b1950217454301"><a name="b1950217454301"></a><a name="b1950217454301"></a>Filesystem</strong> or <strong id="b3502445163020"><a name="b3502445163020"></a><a name="b3502445163020"></a>Block</strong>. The default value is <strong id="b175031145163015"><a name="b175031145163015"></a><a name="b175031145163015"></a>Filesystem</strong>. This parameter takes effect when a Pod is created. <strong id="b122791854203017"><a name="b122791854203017"></a><a name="b122791854203017"></a>Filesystem</strong> indicates that a file system is created on a PVC to access the storage. <strong id="b142791654143010"><a name="b142791654143010"></a><a name="b142791654143010"></a>Block</strong> indicates that a raw volume is used to access the storage.</p>
</td>
</tr>
<tr id="row18428153715212"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="p94281537112112"><a name="p94281537112112"></a><a name="p94281537112112"></a>spec.resources.requests.storage</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p124283376211"><a name="p124283376211"></a><a name="p124283376211"></a>Size of the volume to be created.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p1623917289400"><a name="p1623917289400"></a><a name="p1623917289400"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p1375730144016"><a name="p1375730144016"></a><a name="p1375730144016"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0150885187_p1573183510015"><a name="en-us_topic_0150885187_p1573183510015"></a><a name="en-us_topic_0150885187_p1573183510015"></a>Size of the volume to be created. The format is ***Gi and the unit is GiB.</p>
<p id="p1525217519276"><a name="p1525217519276"></a><a name="p1525217519276"></a>The PVC capacity depends on storage specifications and host specifications. For example, OceanStor Dorado 6.1.2 or OceanStor Pacific series 8.1.0 is connected to CentOS 7. If ext4 file systems are used, see <a href="/css-docs/en/v4.6.0/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning#en-us_topic_0150885187_table178824527142">Table 2</a>. If XFS file systems are used, see <a href="/css-docs/en/v4.6.0/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning#en-us_topic_0150885187_table101951367104">Table 3</a>. If NFS or raw devices are used, the capacity must meet the specifications of the used Huawei storage device model and version.</p>
<p id="p63667162711"><a name="p63667162711"></a><a name="p63667162711"></a>If the PVC capacity does not meet the specifications, a PVC or Pod may fail to be created due to the limitations of storage specifications or host file system specifications.</p>
<p id="p14102426144517"><a name="p14102426144517"></a><a name="p14102426144517"></a>When a PVC is created using a static PV and the PVC capacity is smaller than the capacity of the bound PV, the PVC capacity is set to the capacity of the bound PV. If the PVC capacity is greater than the capacity of the bound PV, the PVC cannot be created.</p>
</td>
</tr>
<tr id="row25733352019"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="p2820143513433"><a name="p2820143513433"></a><a name="p2820143513433"></a>spec.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p38203355433"><a name="p38203355433"></a><a name="p38203355433"></a>Name of the PV object.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p16239128124013"><a name="p16239128124013"></a><a name="p16239128124013"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p193751301406"><a name="p193751301406"></a><a name="p193751301406"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33%" headers="mcps1.2.6.1.5 "><p id="p2082083524316"><a name="p2082083524316"></a><a name="p2082083524316"></a>This parameter is mandatory when a PVC is created statically.</p>
</td>
</tr>
<tr id="row1346813210239"><td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.1 "><p id="p16469332162317"><a name="p16469332162317"></a><a name="p16469332162317"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p135732351909"><a name="en-us_topic_0150885187_p135732351909"></a><a name="en-us_topic_0150885187_p135732351909"></a>Name of the StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="14.000000000000002%" headers="mcps1.2.6.1.3 "><p id="p15469113232316"><a name="p15469113232316"></a><a name="p15469113232316"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="12%" headers="mcps1.2.6.1.4 "><p id="p124691932162310"><a name="p124691932162310"></a><a name="p124691932162310"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33%" headers="mcps1.2.6.1.5 "><p id="p1469332112312"><a name="p1469332112312"></a><a name="p1469332112312"></a>When a PVC is created, an empty character string is transferred. If this parameter is not set, the default StorageClass object name will be used.</p>
</td>
</tr>
</tbody>
</table>

