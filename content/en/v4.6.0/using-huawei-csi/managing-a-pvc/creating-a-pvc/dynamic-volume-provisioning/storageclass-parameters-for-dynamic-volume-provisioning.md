---
title: "StorageClass Parameters for Dynamic Volume Provisioning"
linkTitle: "StorageClass Parameters for Dynamic Volume Provisioning"
description: 
weight: 2
---

**Table  1**  StorageClass configuration parameters

<a name="en-us_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="en-us_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="16%" id="mcps1.2.6.1.1"><p id="en-us_topic_0000001162111564_p875071122919"><a name="en-us_topic_0000001162111564_p875071122919"></a><a name="en-us_topic_0000001162111564_p875071122919"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="28.000000000000004%" id="mcps1.2.6.1.2"><p id="en-us_topic_0000001162111564_p17750131113295"><a name="en-us_topic_0000001162111564_p17750131113295"></a><a name="en-us_topic_0000001162111564_p17750131113295"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="15%" id="mcps1.2.6.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="13%" id="mcps1.2.6.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="28.000000000000004%" id="mcps1.2.6.1.5"><p id="en-us_topic_0000001162111564_p075011113295"><a name="en-us_topic_0000001162111564_p075011113295"></a><a name="en-us_topic_0000001162111564_p075011113295"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p4750141111292"><a name="en-us_topic_0000001162111564_p4750141111292"></a><a name="en-us_topic_0000001162111564_p4750141111292"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p475091120296"><a name="en-us_topic_0000001162111564_p475091120296"></a><a name="en-us_topic_0000001162111564_p475091120296"></a>User-defined name of a StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001162111564_p861713973915"><a name="en-us_topic_0000001162111564_p861713973915"></a><a name="en-us_topic_0000001162111564_p861713973915"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p8750161119299"><a name="en-us_topic_0000001162111564_p8750161119299"></a><a name="en-us_topic_0000001162111564_p8750161119299"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p15750201119295"><a name="en-us_topic_0000001162111564_p15750201119295"></a><a name="en-us_topic_0000001162111564_p15750201119295"></a>Name of the provisioner.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>Set this parameter to the driver name set during Huawei CSI installation.</p>
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>The value is the same as that of <strong id="b1223814278013"><a name="b1223814278013"></a><a name="b1223814278013"></a>driverName</strong> in the <strong id="b1649220321700"><a name="b1649220321700"></a><a name="b1649220321700"></a>values.yaml</strong> file.</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p119108535312"><a name="p119108535312"></a><a name="p119108535312"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p16910135393118"><a name="p16910135393118"></a><a name="p16910135393118"></a>Reclamation policy. The following types are supported:</p>
<a name="ul5209917195517"></a><a name="ul5209917195517"></a><ul id="ul5209917195517"><li><strong id="b39881432511"><a name="b39881432511"></a><a name="b39881432511"></a>Delete</strong>: Resources are automatically reclaimed.</li><li><strong id="b15829858448"><a name="b15829858448"></a><a name="b15829858448"></a>Retain</strong>: Resources are manually reclaimed.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li><strong id="b48131861150"><a name="b48131861150"></a><a name="b48131861150"></a>Delete</strong>: When a PV/PVC is deleted, resources on the storage device are also deleted.</li><li><strong id="b52391026851"><a name="b52391026851"></a><a name="b52391026851"></a>Retain</strong>: When a PV/PVC is deleted, resources on the storage device are not deleted.</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p192771821155012"><a name="p192771821155012"></a><a name="p192771821155012"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p8277132112501"><a name="p8277132112501"></a><a name="p8277132112501"></a>Whether to allow volume expansion. If this parameter is set to <strong id="b494616718617"><a name="b494616718617"></a><a name="b494616718617"></a>true</strong>, the capacity of the PV that uses the StorageClass can be expanded.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p13923171118495"><a name="p13923171118495"></a><a name="p13923171118495"></a>This function can only be used to expand PV capacity but cannot be used to reduce PV capacity.</p>
<p id="p1999211201535"><a name="p1999211201535"></a><a name="p1999211201535"></a>The PV capacity expansion function is supported in Kubernetes 1.14 (alpha) and later versions.</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>Name of the backend where the resource to be created is located.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>If this parameter is not set, Huawei CSI will randomly select a backend that meets the capacity requirements to create resources.</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>You are advised to specify a backend to ensure that the created resource is located on the expected backend.</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p395711171674"><a name="p395711171674"></a><a name="p395711171674"></a>parameters.pool</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p119571517771"><a name="p119571517771"></a><a name="p119571517771"></a>Name of the storage resource pool where the resource to be created is located. If this parameter is set, <strong id="b109899222081"><a name="b109899222081"></a><a name="b109899222081"></a>parameters.backend</strong> must also be specified.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p43701077524"><a name="p43701077524"></a><a name="p43701077524"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p12398310135213"><a name="p12398310135213"></a><a name="p12398310135213"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p99571317978"><a name="p99571317978"></a><a name="p99571317978"></a>If this parameter is not set, Huawei CSI will randomly select a storage pool that meets the capacity requirements from the selected backend to create resources. You are advised to specify a storage pool to ensure that the created resource is located in the expected storage pool.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p1775061119292"><a name="en-us_topic_0000001162111564_p1775061119292"></a><a name="en-us_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p975011122920"><a name="en-us_topic_0000001162111564_p975011122920"></a><a name="en-us_topic_0000001162111564_p975011122920"></a>Type of the volume to be created. The following types are supported:</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li><strong id="b1733717591123"><a name="b1733717591123"></a><a name="b1733717591123"></a>lun</strong>: A LUN is provisioned on the storage side.</li><li><strong id="b10216124101312"><a name="b10216124101312"></a><a name="b10216124101312"></a>fs</strong>: A file system is provisioned on the storage side.</li><li><strong id="b1412435781313"><a name="b1412435781313"></a><a name="b1412435781313"></a>dtree</strong>: A volume of the Dtree type is provisioned on the storage side.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul15360173513251"></a><a name="ul15360173513251"></a><ul id="ul15360173513251"><li>If NAS storage is used, this parameter must be set to <strong id="b37001010173115"><a name="b37001010173115"></a><a name="b37001010173115"></a>fs</strong>.</li><li>If SAN storage is used, this parameter must be set to <strong id="b42448214314"><a name="b42448214314"></a><a name="b42448214314"></a>lun</strong>.</li><li>If NAS storage of the Dtree type is used, this parameter must be set to <strong id="b209472521079"><a name="b209472521079"></a><a name="b209472521079"></a>dtree</strong>.</li></ul>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p13750171110290"><a name="en-us_topic_0000001162111564_p13750171110290"></a><a name="en-us_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p67501211102911"><a name="en-us_topic_0000001162111564_p67501211102911"></a><a name="en-us_topic_0000001162111564_p67501211102911"></a>Allocation type of the volume to be created. The following types are supported:</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li><strong id="b0621115111132"><a name="b0621115111132"></a><a name="b0621115111132"></a>thin</strong>: Not all required space is allocated during creation. Instead, the space is dynamically allocated based on the usage.</li><li><strong id="b1051217771412"><a name="b1051217771412"></a><a name="b1051217771412"></a>thick</strong>: All required space is allocated during creation.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001162111564_p57502011142910"><a name="en-us_topic_0000001162111564_p57502011142910"></a><a name="en-us_topic_0000001162111564_p57502011142910"></a>If this parameter is not specified, <strong id="b7399769818"><a name="b7399769818"></a><a name="b7399769818"></a>thin</strong> will be used. Not all required space is allocated during creation. Instead, the space is dynamically allocated based on the usage.</p>
<p id="p371813715289"><a name="p371813715289"></a><a name="p371813715289"></a>OceanStor Dorado/OceanStor Dorado V3 does not support <strong id="b13346103634718"><a name="b13346103634718"></a><a name="b13346103634718"></a>thick</strong>.</p>
</td>
</tr>
<tr id="row167642021133711"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p18750171111299"><a name="en-us_topic_0000001162111564_p18750171111299"></a><a name="en-us_topic_0000001162111564_p18750171111299"></a>parameters.fsType</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p19169191111571"><a name="p19169191111571"></a><a name="p19169191111571"></a>Type of a host file system. The supported types are:</p>
<a name="ul9614171916576"></a><a name="ul9614171916576"></a><ul id="ul9614171916576"><li>ext2</li><li>ext3</li><li>ext4</li><li>xfs</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p937047165217"><a name="p937047165217"></a><a name="p937047165217"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p1439871055220"><a name="p1439871055220"></a><a name="p1439871055220"></a>ext4</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001162111564_p8750311172910"><a name="en-us_topic_0000001162111564_p8750311172910"></a><a name="en-us_topic_0000001162111564_p8750311172910"></a>This parameter is valid only when <strong id="b191575431815"><a name="b191575431815"></a><a name="b191575431815"></a>volumeType</strong> of a StorageClass is set to <strong id="b128160171913"><a name="b128160171913"></a><a name="b128160171913"></a>lun</strong> and <strong id="b1027892201911"><a name="b1027892201911"></a><a name="b1027892201911"></a>volumeMode</strong> of a PVC is set to <strong id="b758414616192"><a name="b758414616192"></a><a name="b758414616192"></a>Filesystem</strong>.</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p499022713590"><a name="p499022713590"></a><a name="p499022713590"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p2990182715594"><a name="p2990182715594"></a><a name="p2990182715594"></a>IP address of the NFS client that can access the volume. This parameter is mandatory when <strong id="b33096265194"><a name="b33096265194"></a><a name="b33096265194"></a>volumeType</strong> is set to <strong id="b814562814199"><a name="b814562814199"></a><a name="b814562814199"></a>fs</strong>.</p>
<p id="p1246510319510"><a name="p1246510319510"></a><a name="p1246510319510"></a>You can enter the client host name (a full domain name is recommended), client IP address, or client IP address segment.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1637013765210"><a name="p1637013765210"></a><a name="p1637013765210"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p113981010185211"><a name="p113981010185211"></a><a name="p113981010185211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p466615315578"><a name="p466615315578"></a><a name="p466615315578"></a>The asterisk (*) can be used to indicate any client. If you are not sure about the IP address of the access client, you are advised to use the asterisk (*) to prevent the client access from being rejected by the storage system.</p>
<p id="p164521752175617"><a name="p164521752175617"></a><a name="p164521752175617"></a>If the client host name is used, you are advised to use the full domain name.</p>
<p id="p20828214135714"><a name="p20828214135714"></a><a name="p20828214135714"></a>The IP addresses can be IPv4 addresses, IPv6 addresses, or a combination of IPv4 and IPv6 addresses.</p>
<p id="p208641555185710"><a name="p208641555185710"></a><a name="p208641555185710"></a>You can enter multiple host names, IP addresses, or IP address segments and separate them with semicolons (;) or spaces or by pressing <strong id="b143841457211"><a name="b143841457211"></a><a name="b143841457211"></a>Enter</strong>. Example: <strong id="b1791131414223"><a name="b1791131414223"></a><a name="b1791131414223"></a>192.168.0.10;192.168.0.0/24;myserver1.test</strong></p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row475081162913"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p187501311122918"><a name="en-us_topic_0000001162111564_p187501311122918"></a><a name="en-us_topic_0000001162111564_p187501311122918"></a>parameters.cloneSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p77501911192918"><a name="en-us_topic_0000001162111564_p77501911192918"></a><a name="en-us_topic_0000001162111564_p77501911192918"></a>Cloning speed. The value ranges from 1 to 4.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p20370157155213"><a name="p20370157155213"></a><a name="p20370157155213"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p2398810105211"><a name="p2398810105211"></a><a name="p2398810105211"></a>3</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001162111564_p1775091110298"><a name="en-us_topic_0000001162111564_p1775091110298"></a><a name="en-us_topic_0000001162111564_p1775091110298"></a><strong id="b176541499232"><a name="b176541499232"></a><a name="b176541499232"></a>4</strong> indicates the highest speed. This parameter is available when you clone a PVC or create a PVC using a snapshot. For details, see <a href="/css-docs/en/v4.6.0/using-huawei-csi/managing-a-pvc/cloning-a-pvc">Cloning a PVC</a> or <a href="/css-docs/en/v4.6.0/using-huawei-csi/managing-a-pvc/creating-a-pvc-using-a-snapshot">Creating a PVC Using a Snapshot</a>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750161119295"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p133711471387"><a name="p133711471387"></a><a name="p133711471387"></a>parameters.applicationType</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p153378472388"><a name="p153378472388"></a><a name="p153378472388"></a>Application type name for creating a LUN or NAS when the backend is OceanStor Dorado.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p193700711523"><a name="p193700711523"></a><a name="p193700711523"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p8398201010524"><a name="p8398201010524"></a><a name="p8398201010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul2082135095716"></a><a name="ul2082135095716"></a><ul id="ul2082135095716"><li>If the value of <strong id="b5482191814267"><a name="b5482191814267"></a><a name="b5482191814267"></a>volumeType</strong> is <strong id="b19100162522617"><a name="b19100162522617"></a><a name="b19100162522617"></a>lun</strong>, log in to DeviceManager and choose <strong id="b5787165272514"><a name="b5787165272514"></a><a name="b5787165272514"></a>Services</strong> &gt; <strong id="b778745272512"><a name="b778745272512"></a><a name="b778745272512"></a>Block Service</strong> &gt; <strong id="b4788452122517"><a name="b4788452122517"></a><a name="b4788452122517"></a>LUN Groups</strong> &gt; <strong id="b7788452142520"><a name="b7788452142520"></a><a name="b7788452142520"></a>LUNs</strong> &gt; <strong id="b978845212254"><a name="b978845212254"></a><a name="b978845212254"></a>Create</strong> to obtain the application type name.</li><li>If the value of <strong id="b182924592619"><a name="b182924592619"></a><a name="b182924592619"></a>volumeType</strong> is <strong id="b18880342102610"><a name="b18880342102610"></a><a name="b18880342102610"></a>fs</strong>, log in to DeviceManager and choose <strong id="b421011305263"><a name="b421011305263"></a><a name="b421011305263"></a>Services</strong> &gt; <strong id="b4210730192612"><a name="b4210730192612"></a><a name="b4210730192612"></a>File Service</strong> &gt; <strong id="b192111530132614"><a name="b192111530132614"></a><a name="b192111530132614"></a>File Systems</strong> &gt; <strong id="b19211153032614"><a name="b19211153032614"></a><a name="b19211153032614"></a>Create</strong> to obtain the application type name.</li></ul>
</td>
</tr>
<tr id="row15478113119190"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p18478163131914"><a name="p18478163131914"></a><a name="p18478163131914"></a>parameters.qos</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p15525175120211"><a name="p15525175120211"></a><a name="p15525175120211"></a>LUN/NAS QoS settings of the PV on the storage side.</p>
<p id="p12218174732111"><a name="p12218174732111"></a><a name="p12218174732111"></a>The value of the parameter is JSON character strings in dictionary format. A character string is enclosed by single quotation marks and the dictionary key by double quotation marks. Example: <strong id="b1246522122814"><a name="b1246522122814"></a><a name="b1246522122814"></a>'{"maxMBPS": 999, "maxIOPS": 999}'</strong></p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p03704715211"><a name="p03704715211"></a><a name="p03704715211"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p1439818100526"><a name="p1439818100526"></a><a name="p1439818100526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p24789316192"><a name="p24789316192"></a><a name="p24789316192"></a>For details about the supported QoS configurations, see <a href="#table74841513116">Table 2</a>.</p>
</td>
</tr>
<tr id="row1713161417388"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p513251416380"><a name="p513251416380"></a><a name="p513251416380"></a>parameters.storageQuota</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p613221412389"><a name="p613221412389"></a><a name="p613221412389"></a>Quota of a PV on the storage device. This parameter is valid only when NAS is used for connecting to OceanStor Pacific series storage.</p>
<p id="p7371208112220"><a name="p7371208112220"></a><a name="p7371208112220"></a>The value of the parameter is JSON character strings in dictionary format. A character string is enclosed by single quotation marks and the dictionary key by double quotation marks. Example: <strong id="b12299131202918"><a name="b12299131202918"></a><a name="b12299131202918"></a>'{"spaceQuota": "softQuota", "gracePeriod": 100}'</strong></p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p73707715210"><a name="p73707715210"></a><a name="p73707715210"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p639812105526"><a name="p639812105526"></a><a name="p639812105526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p21321014103814"><a name="p21321014103814"></a><a name="p21321014103814"></a>For details about the supported quota configurations, see <a href="#table2083974632312">Table 3</a>.</p>
</td>
</tr>
<tr id="row87671018115219"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p74248684617"><a name="p74248684617"></a><a name="p74248684617"></a>parameters.hyperMetro</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p84244684616"><a name="p84244684616"></a><a name="p84244684616"></a>Whether a HyperMetro volume is to be created. This parameter needs to be configured when the backend is of the HyperMetro type.</p>
<a name="ul196431227165817"></a><a name="ul196431227165817"></a><ul id="ul196431227165817"><li><strong id="b1186395342913"><a name="b1186395342913"></a><a name="b1186395342913"></a>"true"</strong>: The created volume is a HyperMetro volume. If the storage backend is a HyperMetro backend, the value must be <strong id="b18666174053310"><a name="b18666174053310"></a><a name="b18666174053310"></a>true</strong>.</li><li><strong id="b1793395719290"><a name="b1793395719290"></a><a name="b1793395719290"></a>"false"</strong>: The created volume is a common volume.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p03705765218"><a name="p03705765218"></a><a name="p03705765218"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p12398101013527"><a name="p12398101013527"></a><a name="p12398101013527"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p5697340175314"><a name="p5697340175314"></a><a name="p5697340175314"></a>When the used backend is a HyperMetro backend and a HyperMetro volume needs to be provisioned, set this parameter to <strong id="b3841359359"><a name="b3841359359"></a><a name="b3841359359"></a>true</strong>. If this parameter is set to <strong id="b17408597355"><a name="b17408597355"></a><a name="b17408597355"></a>false</strong>, services may be interrupted if the logical management port connected to the backend fails over.</p>
</td>
</tr>
<tr id="row5571122410231"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p13571162414233"><a name="p13571162414233"></a><a name="p13571162414233"></a>parameters.metroPairSyncSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p85711524172312"><a name="p85711524172312"></a><a name="p85711524172312"></a>Data synchronization speed of a HyperMetro pair. The value ranges from 1 to 4.</p>
<p id="p34101616202511"><a name="p34101616202511"></a><a name="p34101616202511"></a>The value can be:</p>
<a name="ul15591625182515"></a><a name="ul15591625182515"></a><ul id="ul15591625182515"><li><strong id="b1816990202917"><a name="b1816990202917"></a><a name="b1816990202917"></a>1</strong>: low</li><li><strong id="b9407476297"><a name="b9407476297"></a><a name="b9407476297"></a>2</strong>: medium</li><li><strong id="b7486255298"><a name="b7486255298"></a><a name="b7486255298"></a>3</strong>: high</li><li><strong id="b95921290298"><a name="b95921290298"></a><a name="b95921290298"></a>4</strong>: highest</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p15716241239"><a name="p15716241239"></a><a name="p15716241239"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p1957172422315"><a name="p1957172422315"></a><a name="p1957172422315"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1557114243237"><a name="p1557114243237"></a><a name="p1557114243237"></a>The configuration takes effect when a HyperMetro volume is created.</p>
<p id="p688744685818"><a name="p688744685818"></a><a name="p688744685818"></a>Note:</p>
<a name="ul35821048175812"></a><a name="ul35821048175812"></a><ul id="ul35821048175812"><li>If this parameter is not configured, the storage speed of the HyperMetro pair is determined by the storage device.</li><li>The highest synchronization speed may increase the host latency.</li></ul>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>Permission on the directory mounted to a container.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>For details about the configuration format, refer to the Linux permission settings, for example, 777 and 755.</p>
<p id="p1551794755015"><a name="p1551794755015"></a><a name="p1551794755015"></a>All SAN storage devices are supported. Only the following NAS storage devices are supported: OceanStor Dorado, OceanStor, and OceanStor Pacific 8.1.2 and later versions.</p>
</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p6718844173115"><a name="p6718844173115"></a><a name="p6718844173115"></a>parameters.rootSquash</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p07183448314"><a name="p07183448314"></a><a name="p07183448314"></a>Controls the <strong id="b677565983115"><a name="b677565983115"></a><a name="b677565983115"></a>root</strong> permission of the client.</p>
<p id="p129442384148"><a name="p129442384148"></a><a name="p129442384148"></a>The value can be:</p>
<a name="ul124031949175810"></a><a name="ul124031949175810"></a><ul id="ul124031949175810"><li><strong id="b4742203910327"><a name="b4742203910327"></a><a name="b4742203910327"></a>root_squash</strong>: The client cannot access the storage system as user <strong id="b8742193953219"><a name="b8742193953219"></a><a name="b8742193953219"></a>root</strong>. If a client accesses the storage system as user <strong id="b1774216396326"><a name="b1774216396326"></a><a name="b1774216396326"></a>root</strong>, the client will be mapped as an anonymous user.</li><li><strong id="b1629216953320"><a name="b1629216953320"></a><a name="b1629216953320"></a>no_root_squash</strong>: A client can access the storage system as user <strong id="b1429279123310"><a name="b1429279123310"></a><a name="b1429279123310"></a>root</strong> and has the permission of user <strong id="b929320911332"><a name="b929320911332"></a><a name="b929320911332"></a>root</strong>.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p73701479521"><a name="p73701479521"></a><a name="p73701479521"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p13981710165217"><a name="p13981710165217"></a><a name="p13981710165217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p57181444183118"><a name="p57181444183118"></a><a name="p57181444183118"></a>Only NAS storage is supported.</p>
</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p14519141410508"><a name="p14519141410508"></a><a name="p14519141410508"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p3644133462719"><a name="p3644133462719"></a><a name="p3644133462719"></a>Whether to retain the user ID (UID) and group ID (GID) of a shared directory.</p>
<p id="p19519161416501"><a name="p19519161416501"></a><a name="p19519161416501"></a>The value can be:</p>
<a name="ul14691584594"></a><a name="ul14691584594"></a><ul id="ul14691584594"><li><strong id="b1996694383314"><a name="b1996694383314"></a><a name="b1996694383314"></a>all_squash</strong>: The UID and GID of the shared directory are mapped to anonymous users.</li><li><strong id="b108734512335"><a name="b108734512335"></a><a name="b108734512335"></a>no_all_squash</strong>: The UID and GID of the shared directory are retained.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p163702712526"><a name="p163702712526"></a><a name="p163702712526"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p7398121045211"><a name="p7398121045211"></a><a name="p7398121045211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p618494455518"><a name="p618494455518"></a><a name="p618494455518"></a>Only NAS storage is supported.</p>
</td>
</tr>
<tr id="row4779143834112"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p6779173815418"><a name="p6779173815418"></a><a name="p6779173815418"></a>parameters.accesskrb5</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p159171449164417"><a name="p159171449164417"></a><a name="p159171449164417"></a>Configures the krb5 security protocol.</p>
<a name="ul957213141953"></a><a name="ul957213141953"></a><ul id="ul957213141953"><li><strong id="b18789162612508"><a name="b18789162612508"></a><a name="b18789162612508"></a>read_only</strong>: read-only</li><li><strong id="b090243019503"><a name="b090243019503"></a><a name="b090243019503"></a>read_write</strong>: read and write</li><li><strong id="b1731815356507"><a name="b1731815356507"></a><a name="b1731815356507"></a>none</strong>: no permission</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p577912382417"><a name="p577912382417"></a><a name="p577912382417"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p9779193814412"><a name="p9779193814412"></a><a name="p9779193814412"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p15292191316454"><a name="p15292191316454"></a><a name="p15292191316454"></a>During mounting, you can specify the <strong id="b655174415014"><a name="b655174415014"></a><a name="b655174415014"></a>sec</strong> parameter in <strong id="b12405104713508"><a name="b12405104713508"></a><a name="b12405104713508"></a>mountOptions</strong>.</p>
</td>
</tr>
<tr id="row99331045154111"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p933031214424"><a name="p933031214424"></a><a name="p933031214424"></a>parameters.accesskrb5i</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p7359241154"><a name="p7359241154"></a><a name="p7359241154"></a>Configures the krb5i security protocol.</p>
<a name="ul149421336953"></a><a name="ul149421336953"></a><ul id="ul149421336953"><li><strong id="b43471279502"><a name="b43471279502"></a><a name="b43471279502"></a>read_only</strong>: read-only</li><li><strong id="b1089724215"><a name="b1089724215"></a><a name="b1089724215"></a>read_write</strong>: read and write</li><li><strong id="b730091191"><a name="b730091191"></a><a name="b730091191"></a>none</strong>: no permission</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p129331245154111"><a name="p129331245154111"></a><a name="p129331245154111"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p96976291391"><a name="p96976291391"></a><a name="p96976291391"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p787455154620"><a name="p787455154620"></a><a name="p787455154620"></a>During mounting, you can specify the <strong id="b104521919145114"><a name="b104521919145114"></a><a name="b104521919145114"></a>sec</strong> parameter in <strong id="b184521519185112"><a name="b184521519185112"></a><a name="b184521519185112"></a>mountOptions</strong>.</p>
</td>
</tr>
<tr id="row47801443164117"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p11892181264220"><a name="p11892181264220"></a><a name="p11892181264220"></a>parameters.accesskrb5p</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p19699145314447"><a name="p19699145314447"></a><a name="p19699145314447"></a>Configures the krb5p security protocol.</p>
<a name="ul1713519393512"></a><a name="ul1713519393512"></a><ul id="ul1713519393512"><li><strong id="b1335072755019"><a name="b1335072755019"></a><a name="b1335072755019"></a>read_only</strong>: read-only</li><li><strong id="b1988855912"><a name="b1988855912"></a><a name="b1988855912"></a>read_write</strong>: read and write</li><li><strong id="b896429942"><a name="b896429942"></a><a name="b896429942"></a>none</strong>: no permission</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1780134314118"><a name="p1780134314118"></a><a name="p1780134314118"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p14114173118919"><a name="p14114173118919"></a><a name="p14114173118919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1132519619463"><a name="p1132519619463"></a><a name="p1132519619463"></a>During mounting, you can specify the <strong id="b16756502505"><a name="b16756502505"></a><a name="b16756502505"></a>sec</strong> parameter in <strong id="b11751509503"><a name="b11751509503"></a><a name="b11751509503"></a>mountOptions</strong>.</p>
</td>
</tr>
<tr id="row446717321624"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p204682321028"><a name="p204682321028"></a><a name="p204682321028"></a>parameters.snapshotDirectoryVisibility</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p124681932122"><a name="p124681932122"></a><a name="p124681932122"></a>Whether the snapshot directory is visible.</p>
<p id="p445010115419"><a name="p445010115419"></a><a name="p445010115419"></a>The value can be:</p>
<a name="ul129350148597"></a><a name="ul129350148597"></a><ul id="ul129350148597"><li><strong id="b2154143563513"><a name="b2154143563513"></a><a name="b2154143563513"></a>visible</strong>: The snapshot directory is visible.</li><li><strong id="b184508441358"><a name="b184508441358"></a><a name="b184508441358"></a>invisible</strong>: The snapshot directory is invisible.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p23707785219"><a name="p23707785219"></a><a name="p23707785219"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p14398210185219"><a name="p14398210185219"></a><a name="p14398210185219"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1346853212219"><a name="p1346853212219"></a><a name="p1346853212219"></a>Only NAS storage is supported.</p>
</td>
</tr>
<tr id="row102662571219"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p526715711214"><a name="p526715711214"></a><a name="p526715711214"></a>parameters.reservedSnapshotSpaceRatio</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p18267205722111"><a name="p18267205722111"></a><a name="p18267205722111"></a>Configures reserved snapshot space.</p>
<p id="p31927526212"><a name="p31927526212"></a><a name="p31927526212"></a>Value type: character string</p>
<p id="p1010918514227"><a name="p1010918514227"></a><a name="p1010918514227"></a>Value range: 0 to 50</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p3370167175211"><a name="p3370167175211"></a><a name="p3370167175211"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p5398131019522"><a name="p5398131019522"></a><a name="p5398131019522"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p826718573213"><a name="p826718573213"></a><a name="p826718573213"></a>OceanStor Dorado 6.1.5+ and OceanStor 6.1.5+ NAS storage devices are supported.</p>
</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a>parameters.disableVerifyCapacity</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p1899222312222"><a name="p1899222312222"></a><a name="p1899222312222"></a>Whether to disable volume capacity verification. After this function is disabled, the system will not verify whether the volume capacity is an integer multiple of the sector size.</p>
<p id="p4236912172515"><a name="p4236912172515"></a><a name="p4236912172515"></a>The value can be:</p>
<a name="ul7370193012510"></a><a name="ul7370193012510"></a><ul id="ul7370193012510"><li>"true": disables volume capacity verification.</li><li>"false": enables volume capacity verification.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"false"</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul199806344293"></a><a name="ul199806344293"></a><ul id="ul199806344293"><li>For OceanStor Dorado and OceanStor storage, the sector size is 512 B.</li><li>For OceanStor Pacific storage, the sector size is 1 MiB.</li></ul>
</td>
</tr>
<tr id="row4937192492016"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p1893710249209"><a name="p1893710249209"></a><a name="p1893710249209"></a>parameters.description</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p20937182432010"><a name="p20937182432010"></a><a name="p20937182432010"></a>Configures the description of the created file system or LUN.</p>
<p id="p259255182110"><a name="p259255182110"></a><a name="p259255182110"></a>Value type: character string</p>
<p id="p8541312112118"><a name="p8541312112118"></a><a name="p8541312112118"></a>The value contains 0 to 255 characters.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p15370175529"><a name="p15370175529"></a><a name="p15370175529"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p17398151010524"><a name="p17398151010524"></a><a name="p17398151010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p8937624182011"><a name="p8937624182011"></a><a name="p8937624182011"></a>Only enterprise storage file systems and LUNs are supported.</p>
</td>
</tr>
<tr id="row1795755912408"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p1036995916474"><a name="p1036995916474"></a><a name="p1036995916474"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p16369105917476"><a name="p16369105917476"></a><a name="p16369105917476"></a>NFS mount option on the host. The following mount option is supported:</p>
<p id="p3366172411524"><a name="p3366172411524"></a><a name="p3366172411524"></a><strong id="b1829141763615"><a name="b1829141763615"></a><a name="b1829141763615"></a>nfsvers</strong>: protocol version for NFS mounting. The value can be <strong id="b1677134312360"><a name="b1677134312360"></a><a name="b1677134312360"></a>3</strong>, <strong id="b15848443362"><a name="b15848443362"></a><a name="b15848443362"></a>4</strong>, <strong id="b813154612361"><a name="b813154612361"></a><a name="b813154612361"></a>4.0</strong>, <strong id="b979851623714"><a name="b979851623714"></a><a name="b979851623714"></a>4.1</strong>, or <strong id="b10691247183619"><a name="b10691247183619"></a><a name="b10691247183619"></a>4.2</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p53719725212"><a name="p53719725212"></a><a name="p53719725212"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p13398141016526"><a name="p13398141016526"></a><a name="p13398141016526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p775515413439"><a name="p775515413439"></a><a name="p775515413439"></a>This parameter is optional after the <strong id="b17158349193611"><a name="b17158349193611"></a><a name="b17158349193611"></a>-o</strong> parameter when the <strong id="b19158549153613"><a name="b19158549153613"></a><a name="b19158549153613"></a>mount</strong> command is executed on the host. The value is in list format.</p>
<p id="p486929143316"><a name="p486929143316"></a><a name="p486929143316"></a>If the NFS version is specified for mounting, NFS 3, 4.0, 4.1, and 4.2 protocols are supported (the protocol must be supported and enabled on storage devices). If <strong id="b733146143816"><a name="b733146143816"></a><a name="b733146143816"></a>nfsvers</strong> is set to <strong id="b143311693811"><a name="b143311693811"></a><a name="b143311693811"></a>4</strong>, the latest protocol version NFS 4 may be used for mounting due to different OS configurations, for example, 4.2. If the 4.0 protocol is required, you are advised to set <strong id="b7342612383"><a name="b7342612383"></a><a name="b7342612383"></a>nfsvers</strong> to <strong id="b15357673814"><a name="b15357673814"></a><a name="b15357673814"></a>4.0</strong>.</p>
</td>
</tr>
<tr id="row122991419104113"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p743994313307"><a name="p743994313307"></a><a name="p743994313307"></a>mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p7439243173012"><a name="p7439243173012"></a><a name="p7439243173012"></a>The DPC namespace supports the ACL function. The DPC client supports POSIX ACL, NFSv4 ACL, and NT ACL authentication.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p18371167175218"><a name="p18371167175218"></a><a name="p18371167175218"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p5398121065216"><a name="p5398121065216"></a><a name="p5398121065216"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1451716198319"><a name="p1451716198319"></a><a name="p1451716198319"></a>The descriptions of <strong id="b174671246105310"><a name="b174671246105310"></a><a name="b174671246105310"></a>acl</strong>, <strong id="b8467194645310"><a name="b8467194645310"></a><a name="b8467194645310"></a>aclonlyposix</strong>, <strong id="b124671946125312"><a name="b124671946125312"></a><a name="b124671946125312"></a>cnflush</strong>, and <strong id="b1146724617534"><a name="b1146724617534"></a><a name="b1146724617534"></a>cflush</strong> are for reference only. For details about the parameters, see <em id="i1646819463535"><a name="i1646819463535"></a><a name="i1646819463535"></a><a href="https://support.huawei.com/enterprise/en/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">OceanStor Pacific Series Product Documentation</a></em> and choose <strong id="b1046834613530"><a name="b1046834613530"></a><a name="b1046834613530"></a>Configuration</strong> &gt; <strong id="b14468174665317"><a name="b14468174665317"></a><a name="b14468174665317"></a>Basic Service Configuration Guide for File</strong> &gt; <strong id="b17468144625314"><a name="b17468144625314"></a><a name="b17468144625314"></a>Configuring Basic Services (DPC Scenario)</strong> &gt; <strong id="b946844675316"><a name="b946844675316"></a><a name="b946844675316"></a>Accessing a DPC Share on a Client</strong> &gt; <strong id="b1846811463533"><a name="b1846811463533"></a><a name="b1846811463533"></a>Step 2</strong>.</p>
</td>
</tr>
<tr id="row131796204428"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p184399439309"><a name="p184399439309"></a><a name="p184399439309"></a>mountOptions.aclonlyposix</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p13950103563719"><a name="p13950103563719"></a><a name="p13950103563719"></a>The DPC namespace supports POSIX ACL, and the DPC client supports POSIX ACL authentication.</p>
<p id="p1943913439308"><a name="p1943913439308"></a><a name="p1943913439308"></a>The following protocols support POSIX ACL: DPC, NFSv3, and HDFS. If NFSv4 ACL or NT ACL is used, the DPC client cannot identify the ACL of this type. As a result, the ACL of this type does not take effect.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p103711978523"><a name="p103711978523"></a><a name="p103711978523"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p639831014524"><a name="p639831014524"></a><a name="p639831014524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p718315423511"><a name="p718315423511"></a><a name="p718315423511"></a>If <strong id="b4962121204015"><a name="b4962121204015"></a><a name="b4962121204015"></a>aclonlyposix</strong> and <strong id="b9962721104015"><a name="b9962721104015"></a><a name="b9962721104015"></a>acl</strong> are used together, only <strong id="b6963172144010"><a name="b6963172144010"></a><a name="b6963172144010"></a>acl</strong> takes effect. That is, the namespace supports the ACL function.</p>
</td>
</tr>
<tr id="row10278171764220"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p867705717358"><a name="p867705717358"></a><a name="p867705717358"></a>mountOptions.cnflush</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p7533510163615"><a name="p7533510163615"></a><a name="p7533510163615"></a>Asynchronous disk flushing mode. That is, data is not flushed to disks immediately when files in the namespace are closed.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1537112711528"><a name="p1537112711528"></a><a name="p1537112711528"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p53981310175211"><a name="p53981310175211"></a><a name="p53981310175211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p46771657123516"><a name="p46771657123516"></a><a name="p46771657123516"></a>Asynchronous flushing mode: When a file is closed, data in the cache is not flushed to storage media in synchronous mode. Instead, data is written from the cache to the storage media in asynchronous flushing mode. After the write service is complete, data is flushed from the cache to disks periodically based on the flushing period. In a multi-client scenario, if concurrent operations are performed on the same file, the file size update is affected by the disk flushing period. That is, the file size is updated only after the disk flushing is complete. Generally, the update is completed within several seconds. Synchronous I/Os are not affected by the disk flushing period.</p>
</td>
</tr>
<tr id="row1645871414422"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p13444191520365"><a name="p13444191520365"></a><a name="p13444191520365"></a>mountOptions.cflush</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p194444156366"><a name="p194444156366"></a><a name="p194444156366"></a>Synchronous disk flushing mode. That is, data is flushed to disks immediately when files in the namespace are closed.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1837197175216"><a name="p1837197175216"></a><a name="p1837197175216"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p93981210155216"><a name="p93981210155216"></a><a name="p93981210155216"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p18444315183615"><a name="p18444315183615"></a><a name="p18444315183615"></a>By default, the synchronous disk flushing mode is used.</p>
</td>
</tr>
<tr id="row17198283474"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p13195284475"><a name="p13195284475"></a><a name="p13195284475"></a>mountOptions.sec</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p919162820478"><a name="p919162820478"></a><a name="p919162820478"></a>Kerberos 5 protocol for mounting NFS file systems.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1719152812473"><a name="p1719152812473"></a><a name="p1719152812473"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p181910281476"><a name="p181910281476"></a><a name="p181910281476"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul196241519175315"></a><a name="ul196241519175315"></a><ul id="ul196241519175315"><li>If Kerberos 5 is used, set this parameter to <strong id="b1435135952518"><a name="b1435135952518"></a><a name="b1435135952518"></a>krb5</strong>.</li><li>If Kerberos 5i is used, set this parameter to <strong id="b79148018262"><a name="b79148018262"></a><a name="b79148018262"></a>krb5i</strong>.</li><li>If Kerberos 5p is used, set this parameter to <strong id="b1916811982618"><a name="b1916811982618"></a><a name="b1916811982618"></a>krb5p</strong>.</li><li>Kerberos supports only NFSv4.0 and later versions.</li><li>OceanStor Dorado and OceanStor 6.1.3 and later versions support Kerberos.</li></ul>
</td>
</tr>
<tr id="row16497949175212"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p22011843373"><a name="p22011843373"></a><a name="p22011843373"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p120110433710"><a name="p120110433710"></a><a name="p120110433710"></a>Transmission protocol used for NFS mounting.</p>
<p id="p121419557439"><a name="p121419557439"></a><a name="p121419557439"></a>The value can be <strong id="b11371339115410"><a name="b11371339115410"></a><a name="b11371339115410"></a>rdma</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p1520119410379"><a name="p1520119410379"></a><a name="p1520119410379"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p1201844372"><a name="p1201844372"></a><a name="p1201844372"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><a name="ul197311816164015"></a><a name="ul197311816164015"></a><ul id="ul197311816164015"><li>Ensure that NFS over RDMA is enabled on the storage system.</li><li>For Huawei enterprise storage, NAS storage of OceanStor Dorado and OceanStor 6.1.7 and later is supported.</li><li>For Huawei distributed storage, NAS storage of OceanStor Pacific 8.2.0 and later is supported. If NFS over RDMA is used for distributed storage, <strong id="b1315673395715"><a name="b1315673395715"></a><a name="b1315673395715"></a>mountOptions.nfsvers</strong> must be set to <strong id="b1115711331570"><a name="b1115711331570"></a><a name="b1115711331570"></a>3</strong>.</li></ul>
</td>
</tr>
<tr id="row33343664415"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p33347614411"><a name="p33347614411"></a><a name="p33347614411"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p285125974520"><a name="p285125974520"></a><a name="p285125974520"></a>Protocol port used for NFS mounting.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p7334269448"><a name="p7334269448"></a><a name="p7334269448"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p163341965441"><a name="p163341965441"></a><a name="p163341965441"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1233414615447"><a name="p1233414615447"></a><a name="p1233414615447"></a>If the transmission protocol is <strong id="b698755172717"><a name="b698755172717"></a><a name="b698755172717"></a>rdma</strong>, set this parameter to <strong id="b1080767142715"><a name="b1080767142715"></a><a name="b1080767142715"></a>20049</strong>.</p>
</td>
</tr>
<tr id="row11127032122910"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p612723262910"><a name="p612723262910"></a><a name="p612723262910"></a>mountOptions.discard</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p4127632172918"><a name="p4127632172918"></a><a name="p4127632172918"></a>Automatically triggers the Trim or Discard operation when a file system is mounted. This operation instructs a block device to release unused blocks.</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.2.6.1.3 "><p id="p191271932182911"><a name="p191271932182911"></a><a name="p191271932182911"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13%" headers="mcps1.2.6.1.4 "><p id="p1712773232912"><a name="p1712773232912"></a><a name="p1712773232912"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p2127193210298"><a name="p2127193210298"></a><a name="p2127193210298"></a>The xfs and ext4 file systems are supported.</p>
</td>
</tr>
</tbody>
</table>

**Table  2**  Supported QoS configurations

<a name="table74841513116"></a>
<table><thead align="left"><tr id="row74844518118"><th class="cellrowborder" valign="top" width="16%" id="mcps1.2.5.1.1"><p id="p2579113031316"><a name="p2579113031316"></a><a name="p2579113031316"></a>Storage Type</p>
</th>
<th class="cellrowborder" valign="top" width="16%" id="mcps1.2.5.1.2"><p id="p1643904313015"><a name="p1643904313015"></a><a name="p1643904313015"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="27%" id="mcps1.2.5.1.3"><p id="p164391543143020"><a name="p164391543143020"></a><a name="p164391543143020"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="41%" id="mcps1.2.5.1.4"><p id="p34393439301"><a name="p34393439301"></a><a name="p34393439301"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row18484951131113"><td class="cellrowborder" rowspan="6" valign="top" width="16%" headers="mcps1.2.5.1.1 "><p id="p35795302132"><a name="p35795302132"></a><a name="p35795302132"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.5.1.2 "><p id="p18524175292"><a name="p18524175292"></a><a name="p18524175292"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p05251782913"><a name="p05251782913"></a><a name="p05251782913"></a>Read/write type.</p>
</td>
<td class="cellrowborder" valign="top" width="41%" headers="mcps1.2.5.1.4 "><p id="p152017102914"><a name="p152017102914"></a><a name="p152017102914"></a>This parameter is optional. If it is not specified, the default value of the storage backend is used. For details, see related storage documents.</p>
<p id="p85218172294"><a name="p85218172294"></a><a name="p85218172294"></a>The value can be:</p>
<a name="ul5521517142918"></a><a name="ul5521517142918"></a><ul id="ul5521517142918"><li><strong id="b1996635010414"><a name="b1996635010414"></a><a name="b1996635010414"></a>0</strong>: read I/O</li><li><strong id="b1795565594114"><a name="b1795565594114"></a><a name="b1795565594114"></a>1</strong>: write I/O</li><li><strong id="b656215064213"><a name="b656215064213"></a><a name="b656215064213"></a>2</strong>: read and write I/Os</li></ul>
</td>
</tr>
<tr id="row1548485117111"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p155211732919"><a name="p155211732919"></a><a name="p155211732919"></a>MAXBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p952111772918"><a name="p952111772918"></a><a name="p952111772918"></a>Maximum bandwidth. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p352171716294"><a name="p352171716294"></a><a name="p352171716294"></a>The value is an integer greater than 0, expressed in MB/s.</p>
</td>
</tr>
<tr id="row124848513110"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p9522175292"><a name="p9522175292"></a><a name="p9522175292"></a>MINBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p19522171298"><a name="p19522171298"></a><a name="p19522171298"></a>Minimum bandwidth. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p2052141711297"><a name="p2052141711297"></a><a name="p2052141711297"></a>The value is an integer greater than 0, expressed in MB/s.</p>
</td>
</tr>
<tr id="row74854512113"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1052417132916"><a name="p1052417132916"></a><a name="p1052417132916"></a>MAXIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p352117102912"><a name="p352117102912"></a><a name="p352117102912"></a>Maximum IOPS. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p165211714296"><a name="p165211714296"></a><a name="p165211714296"></a>The value is an integer greater than 0.</p>
</td>
</tr>
<tr id="row1816819710019"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1316813713016"><a name="p1316813713016"></a><a name="p1316813713016"></a>MINIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p0521917172915"><a name="p0521917172915"></a><a name="p0521917172915"></a>Minimum IOPS. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p105201742914"><a name="p105201742914"></a><a name="p105201742914"></a>The value is an integer greater than 0.</p>
</td>
</tr>
<tr id="row1448555120112"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1952517192913"><a name="p1952517192913"></a><a name="p1952517192913"></a>LATENCY</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p85211722911"><a name="p85211722911"></a><a name="p85211722911"></a>Maximum latency. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p352161718293"><a name="p352161718293"></a><a name="p352161718293"></a>The value is an integer greater than 0, expressed in ms.</p>
</td>
</tr>
<tr id="row183095010142"><td class="cellrowborder" rowspan="3" valign="top" width="16%" headers="mcps1.2.5.1.1 "><p id="p38301350131417"><a name="p38301350131417"></a><a name="p38301350131417"></a>OceanStor Dorado V3</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.5.1.2 "><p id="p1752194493315"><a name="p1752194493315"></a><a name="p1752194493315"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1252144463312"><a name="p1252144463312"></a><a name="p1252144463312"></a>Read/write type.</p>
</td>
<td class="cellrowborder" valign="top" width="41%" headers="mcps1.2.5.1.4 "><p id="p12521944143313"><a name="p12521944143313"></a><a name="p12521944143313"></a>The value can be:</p>
<a name="ul25214449332"></a><a name="ul25214449332"></a><ul id="ul25214449332"><li><strong id="b78146864311"><a name="b78146864311"></a><a name="b78146864311"></a>2</strong>: read and write I/Os</li></ul>
</td>
</tr>
<tr id="row2083035031413"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p135211344193310"><a name="p135211344193310"></a><a name="p135211344193310"></a>MAXBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p552117445334"><a name="p552117445334"></a><a name="p552117445334"></a>Maximum bandwidth. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p11931954144519"><a name="p11931954144519"></a><a name="p11931954144519"></a>The value is an integer ranging from 1 to 999999999, expressed in MB/s.</p>
</td>
</tr>
<tr id="row68311950201411"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p55218447336"><a name="p55218447336"></a><a name="p55218447336"></a>MAXIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p052114442338"><a name="p052114442338"></a><a name="p052114442338"></a>Maximum IOPS. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p4756182510457"><a name="p4756182510457"></a><a name="p4756182510457"></a>The value is an integer ranging from 100 to 999999999.</p>
</td>
</tr>
<tr id="row3455115971517"><td class="cellrowborder" rowspan="6" valign="top" width="16%" headers="mcps1.2.5.1.1 "><p id="p74551059151512"><a name="p74551059151512"></a><a name="p74551059151512"></a>OceanStor Dorado/OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.5.1.2 "><p id="p17819135614331"><a name="p17819135614331"></a><a name="p17819135614331"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p981913567333"><a name="p981913567333"></a><a name="p981913567333"></a>Read/write type.</p>
</td>
<td class="cellrowborder" valign="top" width="41%" headers="mcps1.2.5.1.4 "><p id="p14819125620331"><a name="p14819125620331"></a><a name="p14819125620331"></a>The value can be:</p>
<a name="ul17819115611331"></a><a name="ul17819115611331"></a><ul id="ul17819115611331"><li><strong id="b803954689"><a name="b803954689"></a><a name="b803954689"></a>2</strong>: read and write I/Os</li></ul>
</td>
</tr>
<tr id="row545565991517"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p681925616337"><a name="p681925616337"></a><a name="p681925616337"></a>MAXBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1381975613317"><a name="p1381975613317"></a><a name="p1381975613317"></a>Maximum bandwidth. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p4819155623311"><a name="p4819155623311"></a><a name="p4819155623311"></a>The value is an integer ranging from 1 to 999999999, expressed in MB/s.</p>
</td>
</tr>
<tr id="row1145610595158"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p7819115610339"><a name="p7819115610339"></a><a name="p7819115610339"></a>MINBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p14819145633314"><a name="p14819145633314"></a><a name="p14819145633314"></a>Minimum bandwidth. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p1281945614333"><a name="p1281945614333"></a><a name="p1281945614333"></a>The value is an integer ranging from 1 to 999999999, expressed in MB/s.</p>
</td>
</tr>
<tr id="row34568596153"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p15819165612334"><a name="p15819165612334"></a><a name="p15819165612334"></a>MAXIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p18819185623315"><a name="p18819185623315"></a><a name="p18819185623315"></a>Maximum IOPS. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p15990244424"><a name="p15990244424"></a><a name="p15990244424"></a>The value is an integer ranging from 100 to 999999999.</p>
</td>
</tr>
<tr id="row11456959111513"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p178191156163318"><a name="p178191156163318"></a><a name="p178191156163318"></a>MINIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p11819185643319"><a name="p11819185643319"></a><a name="p11819185643319"></a>Minimum IOPS. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p943173717425"><a name="p943173717425"></a><a name="p943173717425"></a>The value is an integer ranging from 100 to 999999999.</p>
</td>
</tr>
<tr id="row81499500175"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p736119112181"><a name="p736119112181"></a><a name="p736119112181"></a>LATENCY</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p0361191131815"><a name="p0361191131815"></a><a name="p0361191131815"></a>Maximum latency. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p33621115182"><a name="p33621115182"></a><a name="p33621115182"></a>The value can be <strong id="b635674414410"><a name="b635674414410"></a><a name="b635674414410"></a>0.5</strong> or <strong id="b5357174420445"><a name="b5357174420445"></a><a name="b5357174420445"></a>1.5</strong>, expressed in ms.</p>
</td>
</tr>
<tr id="row2172155111816"><td class="cellrowborder" rowspan="2" valign="top" width="16%" headers="mcps1.2.5.1.1 "><p id="p13172105116189"><a name="p13172105116189"></a><a name="p13172105116189"></a>FusionStorage/OceanStor Pacific series</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0273440106_p743994313307"><a name="en-us_topic_0273440106_p743994313307"></a><a name="en-us_topic_0273440106_p743994313307"></a>maxMBPS</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0273440106_p7439243173012"><a name="en-us_topic_0273440106_p7439243173012"></a><a name="en-us_topic_0273440106_p7439243173012"></a>Maximum bandwidth. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" width="41%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0273440106_p184391143133017"><a name="en-us_topic_0273440106_p184391143133017"></a><a name="en-us_topic_0273440106_p184391143133017"></a>This parameter is mandatory. The value is an integer greater than 0, expressed in MB/s. For details about the maximum value, see the actual limit of the storage device. For example, the maximum value of OceanStor Pacific NAS is 1073741824.</p>
</td>
</tr>
<tr id="row1734105531812"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0273440106_p184399439309"><a name="en-us_topic_0273440106_p184399439309"></a><a name="en-us_topic_0273440106_p184399439309"></a>maxIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0273440106_p1943913439308"><a name="en-us_topic_0273440106_p1943913439308"></a><a name="en-us_topic_0273440106_p1943913439308"></a>Maximum IOPS. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0273440106_p14439114315304"><a name="en-us_topic_0273440106_p14439114315304"></a><a name="en-us_topic_0273440106_p14439114315304"></a>This parameter is mandatory. The value is an integer greater than 0. For details about the maximum value, see the actual limit of the storage device. For example, the maximum value of OceanStor Pacific NAS is 1073741824000.</p>
</td>
</tr>
</tbody>
</table>

**Table  3**  Supported quota configurations

<a name="table2083974632312"></a>
<table><thead align="left"><tr id="row68394463230"><th class="cellrowborder" valign="top" width="20.202020202020204%" id="mcps1.2.4.1.1"><p id="en-us_topic_0000001218368853_p1643904313015"><a name="en-us_topic_0000001218368853_p1643904313015"></a><a name="en-us_topic_0000001218368853_p1643904313015"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="31.313131313131315%" id="mcps1.2.4.1.2"><p id="en-us_topic_0000001218368853_p164391543143020"><a name="en-us_topic_0000001218368853_p164391543143020"></a><a name="en-us_topic_0000001218368853_p164391543143020"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="48.484848484848484%" id="mcps1.2.4.1.3"><p id="en-us_topic_0000001218368853_p34393439301"><a name="en-us_topic_0000001218368853_p34393439301"></a><a name="en-us_topic_0000001218368853_p34393439301"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row58391646142313"><td class="cellrowborder" valign="top" width="20.202020202020204%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001218368853_p10540642195814"><a name="en-us_topic_0000001218368853_p10540642195814"></a><a name="en-us_topic_0000001218368853_p10540642195814"></a>spaceQuota</p>
</td>
<td class="cellrowborder" valign="top" width="31.313131313131315%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001218368853_p7439243173012"><a name="en-us_topic_0000001218368853_p7439243173012"></a><a name="en-us_topic_0000001218368853_p7439243173012"></a>File quota type.</p>
</td>
<td class="cellrowborder" valign="top" width="48.484848484848484%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001218368853_p184391143133017"><a name="en-us_topic_0000001218368853_p184391143133017"></a><a name="en-us_topic_0000001218368853_p184391143133017"></a>This parameter is mandatory. Only <span class="parmvalue" id="parmvalue1275164274510"><a name="parmvalue1275164274510"></a><a name="parmvalue1275164274510"></a><b>softQuota</b></span> or <span class="parmvalue" id="parmvalue19751142154517"><a name="parmvalue19751142154517"></a><a name="parmvalue19751142154517"></a><b>hardQuota</b></span> can be configured.</p>
</td>
</tr>
<tr id="row13839124642310"><td class="cellrowborder" valign="top" width="20.202020202020204%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001218368853_p184399439309"><a name="en-us_topic_0000001218368853_p184399439309"></a><a name="en-us_topic_0000001218368853_p184399439309"></a>gracePeriod</p>
</td>
<td class="cellrowborder" valign="top" width="31.313131313131315%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001218368853_p1943913439308"><a name="en-us_topic_0000001218368853_p1943913439308"></a><a name="en-us_topic_0000001218368853_p1943913439308"></a>Grace period allowed when the soft quota is configured.</p>
</td>
<td class="cellrowborder" valign="top" width="48.484848484848484%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001218368853_p1540512282024"><a name="en-us_topic_0000001218368853_p1540512282024"></a><a name="en-us_topic_0000001218368853_p1540512282024"></a>This parameter is conditionally optional only when <span class="parmname" id="parmname682317528456"><a name="parmname682317528456"></a><a name="parmname682317528456"></a><b>spaceQuota</b></span> is set to <span class="parmvalue" id="parmvalue68238521459"><a name="parmvalue68238521459"></a><a name="parmvalue68238521459"></a><b>softQuota</b></span>.</p>
<p id="en-us_topic_0000001218368853_p14439114315304"><a name="en-us_topic_0000001218368853_p14439114315304"></a><a name="en-us_topic_0000001218368853_p14439114315304"></a>The value is an integer ranging from 0 to 4294967294.</p>
</td>
</tr>
</tbody>
</table>

