---
title: "StorageClass Parameters for Manage Volume Provisioning"
linkTitle: "StorageClass Parameters for Manage Volume Provisioning"
description: 
weight: 2
---

A  [StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/)  provides administrators with methods to describe a storage "class". Different types may map to a different group of capability definitions. Kubernetes cluster users can dynamically provision volumes based on a StorageClass.

A StorageClass supports the following parameters.

If SAN storage is used, refer to example file  **/examples/sc-lun.yaml**. If NAS storage is used, refer to example file  **/examples/sc-fs.yaml**.

**Table  1**  StorageClass configuration parameters

<a name="en-us_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="en-us_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="15%" id="mcps1.2.6.1.1"><p id="en-us_topic_0000001162111564_p875071122919"><a name="en-us_topic_0000001162111564_p875071122919"></a><a name="en-us_topic_0000001162111564_p875071122919"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="27%" id="mcps1.2.6.1.2"><p id="en-us_topic_0000001162111564_p17750131113295"><a name="en-us_topic_0000001162111564_p17750131113295"></a><a name="en-us_topic_0000001162111564_p17750131113295"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.6.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.6.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="28.000000000000004%" id="mcps1.2.6.1.5"><p id="en-us_topic_0000001162111564_p075011113295"><a name="en-us_topic_0000001162111564_p075011113295"></a><a name="en-us_topic_0000001162111564_p075011113295"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p4750141111292"><a name="en-us_topic_0000001162111564_p4750141111292"></a><a name="en-us_topic_0000001162111564_p4750141111292"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p475091120296"><a name="en-us_topic_0000001162111564_p475091120296"></a><a name="en-us_topic_0000001162111564_p475091120296"></a>User-defined name of a StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001162111564_p861713973915"><a name="en-us_topic_0000001162111564_p861713973915"></a><a name="en-us_topic_0000001162111564_p861713973915"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p8750161119299"><a name="en-us_topic_0000001162111564_p8750161119299"></a><a name="en-us_topic_0000001162111564_p8750161119299"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p15750201119295"><a name="en-us_topic_0000001162111564_p15750201119295"></a><a name="en-us_topic_0000001162111564_p15750201119295"></a>Name of the provisioner.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>Set this parameter to the driver name set during Huawei CSI installation.</p>
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>The value is the same as that of <strong id="b9443556506"><a name="b9443556506"></a><a name="b9443556506"></a>driverName</strong> in the <strong id="b13444205611014"><a name="b13444205611014"></a><a name="b13444205611014"></a>values.yaml</strong> file.</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p119108535312"><a name="p119108535312"></a><a name="p119108535312"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p16910135393118"><a name="p16910135393118"></a><a name="p16910135393118"></a>Reclamation policy. The following types are supported:</p>
<a name="ul5209917195517"></a><a name="ul5209917195517"></a><ul id="ul5209917195517"><li><strong id="b39881432511"><a name="b39881432511"></a><a name="b39881432511"></a>Delete</strong>: Resources are automatically reclaimed.</li><li><strong id="b15829858448"><a name="b15829858448"></a><a name="b15829858448"></a>Retain</strong>: Resources are manually reclaimed.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li><strong id="b48131861150"><a name="b48131861150"></a><a name="b48131861150"></a>Delete</strong>: When a PV/PVC is deleted, resources on the storage device are also deleted.</li><li><strong id="b52391026851"><a name="b52391026851"></a><a name="b52391026851"></a>Retain</strong>: When a PV/PVC is deleted, resources on the storage device are not deleted.</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p192771821155012"><a name="p192771821155012"></a><a name="p192771821155012"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p8277132112501"><a name="p8277132112501"></a><a name="p8277132112501"></a>Whether to allow volume expansion. If this parameter is set to <strong id="b494616718617"><a name="b494616718617"></a><a name="b494616718617"></a>true</strong>, the capacity of the PV that uses the StorageClass can be expanded.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p112771521135014"><a name="p112771521135014"></a><a name="p112771521135014"></a>This function can only be used to expand PV capacity but cannot be used to reduce PV capacity.</p>
<p id="p1999211201535"><a name="p1999211201535"></a><a name="p1999211201535"></a>The PV capacity expansion function is supported in Kubernetes 1.14 (alpha) and later versions.</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>Name of the backend where the resource to be created is located.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>If this parameter is not set, Huawei CSI will randomly select a backend that meets the capacity requirements to create resources.</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>You are advised to specify a backend to ensure that the created resource is located on the expected backend.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p1775061119292"><a name="en-us_topic_0000001162111564_p1775061119292"></a><a name="en-us_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p975011122920"><a name="en-us_topic_0000001162111564_p975011122920"></a><a name="en-us_topic_0000001162111564_p975011122920"></a>Type of the volume to be created. The following types are supported:</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li><strong id="b1733717591123"><a name="b1733717591123"></a><a name="b1733717591123"></a>lun</strong>: A LUN is provisioned on the storage side.</li><li><strong id="b10216124101312"><a name="b10216124101312"></a><a name="b10216124101312"></a>fs</strong>: A file system is provisioned on the storage side.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul15360173513251"></a><a name="ul15360173513251"></a><ul id="ul15360173513251"><li>If NAS storage is used, this parameter must be set to <strong id="b174281228185018"><a name="b174281228185018"></a><a name="b174281228185018"></a>fs</strong>.</li><li>If SAN storage is used, this parameter must be set to <strong id="b114971630195017"><a name="b114971630195017"></a><a name="b114971630195017"></a>lun</strong>.</li></ul>
</td>
</tr>
<tr id="row167642021133711"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p18750171111299"><a name="en-us_topic_0000001162111564_p18750171111299"></a><a name="en-us_topic_0000001162111564_p18750171111299"></a>parameters.fsType</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p19169191111571"><a name="p19169191111571"></a><a name="p19169191111571"></a>Type of a host file system. The supported types are:</p>
<a name="ul9614171916576"></a><a name="ul9614171916576"></a><ul id="ul9614171916576"><li>ext2</li><li>ext3</li><li>ext4</li><li>xfs</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p435413852915"><a name="p435413852915"></a><a name="p435413852915"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p9690143918526"><a name="p9690143918526"></a><a name="p9690143918526"></a>ext4</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001162111564_p8750311172910"><a name="en-us_topic_0000001162111564_p8750311172910"></a><a name="en-us_topic_0000001162111564_p8750311172910"></a>This parameter is valid only when <strong id="b191575431815"><a name="b191575431815"></a><a name="b191575431815"></a>volumeType</strong> of a StorageClass is set to <strong id="b128160171913"><a name="b128160171913"></a><a name="b128160171913"></a>lun</strong> and <strong id="b1027892201911"><a name="b1027892201911"></a><a name="b1027892201911"></a>volumeMode</strong> of a PVC is set to <strong id="b758414616192"><a name="b758414616192"></a><a name="b758414616192"></a>Filesystem</strong>.</p>
</td>
</tr>
<tr id="row1175164935614"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p133711471387"><a name="p133711471387"></a><a name="p133711471387"></a>parameters.applicationType</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p153378472388"><a name="p153378472388"></a><a name="p153378472388"></a>Application type name for creating a LUN or NAS when the backend is OceanStor Dorado.</p>
<div class="note" id="note161704482570"><a name="note161704482570"></a><a name="note161704482570"></a><span class="notetitle"> NOTE: </span><div class="notebody"><p id="p131701948105720"><a name="p131701948105720"></a><a name="p131701948105720"></a>If an application type has been configured before a volume is managed, the value of <strong id="b1219242511116"><a name="b1219242511116"></a><a name="b1219242511116"></a>applicationType</strong> must be the same as the configured application type.</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p193700711523"><a name="p193700711523"></a><a name="p193700711523"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p8398201010524"><a name="p8398201010524"></a><a name="p8398201010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul2082135095716"></a><a name="ul2082135095716"></a><ul id="ul2082135095716"><li>If the value of <strong id="b4235381716"><a name="b4235381716"></a><a name="b4235381716"></a>volumeType</strong> is <strong id="b142318381018"><a name="b142318381018"></a><a name="b142318381018"></a>lun</strong>, log in to DeviceManager and choose <strong id="b19236381410"><a name="b19236381410"></a><a name="b19236381410"></a>Services</strong> &gt; <strong id="b13241638813"><a name="b13241638813"></a><a name="b13241638813"></a>Block Service</strong> &gt; <strong id="b14245380118"><a name="b14245380118"></a><a name="b14245380118"></a>LUN Groups</strong> &gt; <strong id="b22493817112"><a name="b22493817112"></a><a name="b22493817112"></a>LUNs</strong> &gt; <strong id="b1325193814119"><a name="b1325193814119"></a><a name="b1325193814119"></a>Create</strong> to obtain the application type name.</li><li>If the value of <strong id="b271219563111"><a name="b271219563111"></a><a name="b271219563111"></a>volumeType</strong> is <strong id="b1671219565112"><a name="b1671219565112"></a><a name="b1671219565112"></a>fs</strong>, log in to DeviceManager and choose <strong id="b2713165616112"><a name="b2713165616112"></a><a name="b2713165616112"></a>Services</strong> &gt; <strong id="b47132561019"><a name="b47132561019"></a><a name="b47132561019"></a>File Service</strong> &gt; <strong id="b1371317561611"><a name="b1371317561611"></a><a name="b1371317561611"></a>File Systems</strong> &gt; <strong id="b14714155614119"><a name="b14714155614119"></a><a name="b14714155614119"></a>Create</strong> to obtain the application type name.</li></ul>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>Permission on the directory mounted to a container.</p>
<p id="p11862561310"><a name="p11862561310"></a><a name="p11862561310"></a></p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p99211326131"><a name="p99211326131"></a><a name="p99211326131"></a>For details about the configuration format, refer to the Linux permission settings, for example, 777 and 755.</p>
<p id="p248531271420"><a name="p248531271420"></a><a name="p248531271420"></a>All SAN storage devices are supported. Only the following NAS storage devices are supported: OceanStor Dorado, OceanStor, and OceanStor Pacific 8.1.2 and later versions.</p>
</td>
</tr>
<tr id="row1795755912408"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p1036995916474"><a name="p1036995916474"></a><a name="p1036995916474"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p16369105917476"><a name="p16369105917476"></a><a name="p16369105917476"></a>NFS mount option on the host. The following mount option is supported:</p>
<p id="p3366172411524"><a name="p3366172411524"></a><a name="p3366172411524"></a><strong id="b1829141763615"><a name="b1829141763615"></a><a name="b1829141763615"></a>nfsvers</strong>: protocol version for NFS mounting. The value can be <strong id="b13568714163911"><a name="b13568714163911"></a><a name="b13568714163911"></a>3</strong>, <strong id="b4568101433910"><a name="b4568101433910"></a><a name="b4568101433910"></a>4</strong>, <strong id="b19569114133911"><a name="b19569114133911"></a><a name="b19569114133911"></a>4.0</strong>, <strong id="b16569131463916"><a name="b16569131463916"></a><a name="b16569131463916"></a>4.1</strong>, or <strong id="b756931453916"><a name="b756931453916"></a><a name="b756931453916"></a>4.2</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p53719725212"><a name="p53719725212"></a><a name="p53719725212"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p13398141016526"><a name="p13398141016526"></a><a name="p13398141016526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p775515413439"><a name="p775515413439"></a><a name="p775515413439"></a>This parameter is optional after the <strong id="b17158349193611"><a name="b17158349193611"></a><a name="b17158349193611"></a>-o</strong> parameter when the <strong id="b19158549153613"><a name="b19158549153613"></a><a name="b19158549153613"></a>mount</strong> command is executed on the host. The value is in list format.</p>
<p id="p486929143316"><a name="p486929143316"></a><a name="p486929143316"></a>If the NFS version is specified for mounting, NFS 3, 4.0, 4.1, and 4.2 protocols are supported (the protocol must be supported and enabled on storage devices). If <strong id="b733146143816"><a name="b733146143816"></a><a name="b733146143816"></a>nfsvers</strong> is set to <strong id="b143311693811"><a name="b143311693811"></a><a name="b143311693811"></a>4</strong>, the latest protocol version NFS 4 may be used for mounting due to different OS configurations, for example, 4.2. If the 4.0 protocol is required, you are advised to set <strong id="b7342612383"><a name="b7342612383"></a><a name="b7342612383"></a>nfsver:ws</strong> to <strong id="b15357673814"><a name="b15357673814"></a><a name="b15357673814"></a>4.0</strong>.</p>
</td>
</tr>
<tr id="row122991419104113"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p743994313307"><a name="p743994313307"></a><a name="p743994313307"></a>mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p7439243173012"><a name="p7439243173012"></a><a name="p7439243173012"></a>The DPC namespace supports the ACL function. The DPC client supports POSIX ACL, NFSv4 ACL, and NT ACL authentication.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p18371167175218"><a name="p18371167175218"></a><a name="p18371167175218"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p5398121065216"><a name="p5398121065216"></a><a name="p5398121065216"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1451716198319"><a name="p1451716198319"></a><a name="p1451716198319"></a>The descriptions of <strong id="b15619152251820"><a name="b15619152251820"></a><a name="b15619152251820"></a>acl</strong>, <strong id="b17619722151811"><a name="b17619722151811"></a><a name="b17619722151811"></a>aclonlyposix</strong>, <strong id="b161922211184"><a name="b161922211184"></a><a name="b161922211184"></a>cnflush</strong>, and <strong id="b1161962219180"><a name="b1161962219180"></a><a name="b1161962219180"></a>cflush</strong> are for reference only. For details about the parameters, see <em id="i156201922161815"><a name="i156201922161815"></a><a name="i156201922161815"></a><a href="https://support.huawei.com/enterprise/en/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">OceanStor Pacific Series Product Documentation</a></em> and choose <strong id="b18620022101813"><a name="b18620022101813"></a><a name="b18620022101813"></a>Configuration</strong> &gt; <strong id="b196202229183"><a name="b196202229183"></a><a name="b196202229183"></a>Basic Service Configuration Guide for File</strong> &gt; <strong id="b106201522131818"><a name="b106201522131818"></a><a name="b106201522131818"></a>Configuring Basic Services (DPC Scenario)</strong> &gt; <strong id="b2620422141817"><a name="b2620422141817"></a><a name="b2620422141817"></a>Accessing a DPC Share on a Client</strong> &gt; <strong id="b9620172212186"><a name="b9620172212186"></a><a name="b9620172212186"></a>Step 2</strong>.</p>
</td>
</tr>
<tr id="row131796204428"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p184399439309"><a name="p184399439309"></a><a name="p184399439309"></a>mountOptions.aclonlyposix</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p13950103563719"><a name="p13950103563719"></a><a name="p13950103563719"></a>The DPC namespace supports POSIX ACL, and the DPC client supports POSIX ACL authentication.</p>
<p id="p1943913439308"><a name="p1943913439308"></a><a name="p1943913439308"></a>The following protocols support POSIX ACL: DPC, NFSv3, and HDFS. If NFSv4 ACL or NT ACL is used, the DPC client cannot identify the ACL of this type. As a result, the ACL of this type does not take effect.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p103711978523"><a name="p103711978523"></a><a name="p103711978523"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p639831014524"><a name="p639831014524"></a><a name="p639831014524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p718315423511"><a name="p718315423511"></a><a name="p718315423511"></a>If <strong id="b4962121204015"><a name="b4962121204015"></a><a name="b4962121204015"></a>aclonlyposix</strong> and <strong id="b9962721104015"><a name="b9962721104015"></a><a name="b9962721104015"></a>acl</strong> are used together, only <strong id="b6963172144010"><a name="b6963172144010"></a><a name="b6963172144010"></a>acl</strong> takes effect. That is, the namespace supports the ACL function.</p>
</td>
</tr>
<tr id="row10278171764220"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p867705717358"><a name="p867705717358"></a><a name="p867705717358"></a>mountOptions.cnflush</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p7533510163615"><a name="p7533510163615"></a><a name="p7533510163615"></a>Asynchronous disk flushing mode. That is, data is not flushed to disks immediately when files in the namespace are closed.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1537112711528"><a name="p1537112711528"></a><a name="p1537112711528"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p53981310175211"><a name="p53981310175211"></a><a name="p53981310175211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p46771657123516"><a name="p46771657123516"></a><a name="p46771657123516"></a>Asynchronous flushing mode: When a file is closed, data in the cache is not flushed to storage media in synchronous mode. Instead, data is written from the cache to the storage media in asynchronous flushing mode. After the write service is complete, data is flushed from the cache to disks periodically based on the flushing period. In a multi-client scenario, if concurrent operations are performed on the same file, the file size update is affected by the disk flushing period. That is, the file size is updated only after the disk flushing is complete. Generally, the update is completed within several seconds. Synchronous I/Os are not affected by the disk flushing period.</p>
</td>
</tr>
<tr id="row1645871414422"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p13444191520365"><a name="p13444191520365"></a><a name="p13444191520365"></a>mountOptions.cflush</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p194444156366"><a name="p194444156366"></a><a name="p194444156366"></a>Synchronous disk flushing mode. That is, data is flushed to disks immediately when files in the namespace are closed.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1837197175216"><a name="p1837197175216"></a><a name="p1837197175216"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p93981210155216"><a name="p93981210155216"></a><a name="p93981210155216"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p18444315183615"><a name="p18444315183615"></a><a name="p18444315183615"></a>By default, the synchronous disk flushing mode is used.</p>
</td>
</tr>
<tr id="row1510837583"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p13195284475"><a name="p13195284475"></a><a name="p13195284475"></a>mountOptions.sec</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p919162820478"><a name="p919162820478"></a><a name="p919162820478"></a>Kerberos 5 protocol for mounting NFS file systems.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1719152812473"><a name="p1719152812473"></a><a name="p1719152812473"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p181910281476"><a name="p181910281476"></a><a name="p181910281476"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul196241519175315"></a><a name="ul196241519175315"></a><ul id="ul196241519175315"><li>If Kerberos 5 is used, set this parameter to <strong id="b2843162417513"><a name="b2843162417513"></a><a name="b2843162417513"></a>krb5</strong>.</li><li>If Kerberos 5i is used, set this parameter to <strong id="b199331272517"><a name="b199331272517"></a><a name="b199331272517"></a>krb5i</strong>.</li><li>If Kerberos 5p is used, set this parameter to <strong id="b28462298511"><a name="b28462298511"></a><a name="b28462298511"></a>krb5p</strong>.</li><li>Kerberos supports only NFSv4.0 and later versions.</li><li>OceanStor Dorado and OceanStor 6.1.3 and later versions support Kerberos.</li></ul>
</td>
</tr>
<tr id="row128563915810"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p22011843373"><a name="p22011843373"></a><a name="p22011843373"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p120110433710"><a name="p120110433710"></a><a name="p120110433710"></a>Transmission protocol used for NFS mounting.</p>
<p id="p121419557439"><a name="p121419557439"></a><a name="p121419557439"></a>The value can be <strong id="b17875103717511"><a name="b17875103717511"></a><a name="b17875103717511"></a>rdma</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1520119410379"><a name="p1520119410379"></a><a name="p1520119410379"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p1201844372"><a name="p1201844372"></a><a name="p1201844372"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul197311816164015"></a><a name="ul197311816164015"></a><ul id="ul197311816164015"><li>Ensure that NFS over RDMA is enabled on the storage system.</li><li>For Huawei enterprise storage, NAS storage of OceanStor Dorado and OceanStor 6.1.7 and later is supported.</li><li>For Huawei distributed storage, NAS storage of OceanStor Pacific 8.2.0 and later is supported. If NFS over RDMA is used for distributed storage, <strong id="b4866112910519"><a name="b4866112910519"></a><a name="b4866112910519"></a>mountOptions.nfsvers</strong> must be set to <strong id="b980117322517"><a name="b980117322517"></a><a name="b980117322517"></a>3</strong>.</li></ul>
</td>
</tr>
<tr id="row17614421981"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p33347614411"><a name="p33347614411"></a><a name="p33347614411"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p285125974520"><a name="p285125974520"></a><a name="p285125974520"></a>Protocol port used for NFS mounting.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p7334269448"><a name="p7334269448"></a><a name="p7334269448"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p163341965441"><a name="p163341965441"></a><a name="p163341965441"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1233414615447"><a name="p1233414615447"></a><a name="p1233414615447"></a>If the transmission protocol is <strong id="b13741542066"><a name="b13741542066"></a><a name="b13741542066"></a>rdma</strong>, set this parameter to <strong id="b27421042669"><a name="b27421042669"></a><a name="b27421042669"></a>20049</strong>.</p>
</td>
</tr>
<tr id="row72168231837"><td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.1 "><p id="p612723262910"><a name="p612723262910"></a><a name="p612723262910"></a>mountOptions.discard</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.6.1.2 "><p id="p4127632172918"><a name="p4127632172918"></a><a name="p4127632172918"></a>Automatically triggers the Trim or Discard operation when a file system is mounted. This operation instructs a block device to release unused blocks.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p191271932182911"><a name="p191271932182911"></a><a name="p191271932182911"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.4 "><p id="p1712773232912"><a name="p1712773232912"></a><a name="p1712773232912"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p2127193210298"><a name="p2127193210298"></a><a name="p2127193210298"></a>The xfs and ext4 file systems are supported.</p>
</td>
</tr>
</tbody>
</table>

