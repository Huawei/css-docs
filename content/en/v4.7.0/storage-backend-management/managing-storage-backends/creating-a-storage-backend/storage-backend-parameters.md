---
title: "Storage Backend Parameters"
linkTitle: "Storage Backend Parameters"
description: 
weight: 2
---

An example template of the backend configuration file is  **/examples/backend/backend.yaml**. The following table lists the parameters.

**Table  1**  backend parameters

<a name="table9126101819192"></a>
<table><thead align="left"><tr id="row10127131813194"><th class="cellrowborder" valign="top" width="13.86138613861386%" id="mcps1.2.6.1.1"><p id="p5631154913199"><a name="p5631154913199"></a><a name="p5631154913199"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="32.67326732673267%" id="mcps1.2.6.1.2"><p id="p463104991916"><a name="p463104991916"></a><a name="p463104991916"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="13.86138613861386%" id="mcps1.2.6.1.3"><p id="p1463134917198"><a name="p1463134917198"></a><a name="p1463134917198"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="11.881188118811878%" id="mcps1.2.6.1.4"><p id="p6919415195119"><a name="p6919415195119"></a><a name="p6919415195119"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="27.72277227722772%" id="mcps1.2.6.1.5"><p id="p10631049171910"><a name="p10631049171910"></a><a name="p10631049171910"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row111271188193"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p1233915445454"><a name="en-us_topic_0000001324610777_p1233915445454"></a><a name="en-us_topic_0000001324610777_p1233915445454"></a>storage</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p3339204417453"><a name="en-us_topic_0000001324610777_p3339204417453"></a><a name="en-us_topic_0000001324610777_p3339204417453"></a>Storage service type.</p>
<a name="en-us_topic_0000001324610777_ul713574293420"></a><a name="en-us_topic_0000001324610777_ul713574293420"></a><ul id="en-us_topic_0000001324610777_ul713574293420"><li>If enterprise storage provides SAN, set this parameter to <strong id="b417813613303"><a name="b417813613303"></a><a name="b417813613303"></a>oceanstor-san</strong>.</li><li>If enterprise storage provides NAS, set this parameter to <strong id="b1231819107497"><a name="b1231819107497"></a><a name="b1231819107497"></a>oceanstor-nas</strong>.</li><li>If enterprise storage provides NAS of the Dtree type, set this parameter to <strong id="b514124355618"><a name="b514124355618"></a><a name="b514124355618"></a>oceanstor-dtree</strong>.</li><li>If distributed storage provides SAN, set this parameter to <strong id="b129589153306"><a name="b129589153306"></a><a name="b129589153306"></a>fusionstorage-san</strong>.</li><li>If distributed storage provides NAS, set this parameter to <strong id="b17628208309"><a name="b17628208309"></a><a name="b17628208309"></a>fusionstorage-nas</strong>.</li><li>If distributed storage provides NAS of the Dtree type, set this parameter to <strong id="b55310242292"><a name="b55310242292"></a><a name="b55310242292"></a>fusionstorage-dtree</strong>.</li><li>If OceanDisk storage is used, set this parameter to <strong id="b1899815485617"><a name="b1899815485617"></a><a name="b1899815485617"></a>oceandisk-san</strong>.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p533910449459"><a name="en-us_topic_0000001324610777_p533910449459"></a><a name="en-us_topic_0000001324610777_p533910449459"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p15919151545111"><a name="p15919151545111"></a><a name="p15919151545111"></a>oceanstor-nas</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001324610777_p17339174424512"><a name="en-us_topic_0000001324610777_p17339174424512"></a><a name="en-us_topic_0000001324610777_p17339174424512"></a>One backend can provide only one storage service. If a single Huawei storage system can provide both SAN and NAS storage services, you can configure multiple backends and use different storage service types for each backend.</p>
</td>
</tr>
<tr id="row15127618111910"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p733904424519"><a name="en-us_topic_0000001324610777_p733904424519"></a><a name="en-us_topic_0000001324610777_p733904424519"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p23903331109"><a name="en-us_topic_0000001324610777_p23903331109"></a><a name="en-us_topic_0000001324610777_p23903331109"></a>Storage backend name. The value can contain a maximum of 63 characters, including lowercase letters, digits, and hyphens (-). It must start with a letter or digit.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p18339944154510"><a name="en-us_topic_0000001324610777_p18339944154510"></a><a name="en-us_topic_0000001324610777_p18339944154510"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p18919015125112"><a name="p18919015125112"></a><a name="p18919015125112"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="p1874481011019"><a name="p1874481011019"></a><a name="p1874481011019"></a>Ensure that the storage backend name is unique.</p>
</td>
</tr>
<tr id="row765135132312"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="p1650357236"><a name="p1650357236"></a><a name="p1650357236"></a>namespace</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="p1466335142311"><a name="p1466335142311"></a><a name="p1466335142311"></a>Namespace.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="p176653592311"><a name="p176653592311"></a><a name="p176653592311"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p391981510517"><a name="p391981510517"></a><a name="p391981510517"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="p866103515237"><a name="p866103515237"></a><a name="p866103515237"></a>The storage backend must be in the same namespace as Huawei CSI.</p>
</td>
</tr>
<tr id="row184812161516"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="p38488211152"><a name="p38488211152"></a><a name="p38488211152"></a>vstoreName</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="p384813214151"><a name="p384813214151"></a><a name="p384813214151"></a>vStore name on the storage side. This parameter needs to be specified when the connected backend is OceanStor V5 and resources need to be provisioned under a specified vStore.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="p884812114157"><a name="p884812114157"></a><a name="p884812114157"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p16919131517511"><a name="p16919131517511"></a><a name="p16919131517511"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="p584814213151"><a name="p584814213151"></a><a name="p584814213151"></a>This parameter needs to be specified only when the backend is OceanStor V5 and vStores need to be supported.</p>
</td>
</tr>
<tr id="row1218054742718"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="p14180194702714"><a name="p14180194702714"></a><a name="p14180194702714"></a>accountName</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="p1518094762719"><a name="p1518094762719"></a><a name="p1518094762719"></a>Account name on the storage side. This parameter is mandatory when OceanStor Pacific NAS or an OceanStor Pacific dtree is connected and NAS resources need to be provisioned under a specified account.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="p14180547182717"><a name="p14180547182717"></a><a name="p14180547182717"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p20919715115120"><a name="p20919715115120"></a><a name="p20919715115120"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="p195481349369"><a name="p195481349369"></a><a name="p195481349369"></a>This parameter needs to be specified when the connected backend is OceanStor Pacific NAS or OceanStor Pacific dtree and accounts need to be supported.</p>
</td>
</tr>
<tr id="row1212714182196"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p153399449451"><a name="en-us_topic_0000001324610777_p153399449451"></a><a name="en-us_topic_0000001324610777_p153399449451"></a>urls</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p430691742216"><a name="en-us_topic_0000001324610777_p430691742216"></a><a name="en-us_topic_0000001324610777_p430691742216"></a>Management URLs of storage device. The value format is a list. The value can be a domain name or an IP address + port number. Only IPv4 addresses are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1233934484518"><a name="en-us_topic_0000001324610777_p1233934484518"></a><a name="en-us_topic_0000001324610777_p1233934484518"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p691916153512"><a name="p691916153512"></a><a name="p691916153512"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001324610777_p17339144114512"><a name="en-us_topic_0000001324610777_p17339144114512"></a><a name="en-us_topic_0000001324610777_p17339144114512"></a>If the connected backend is OceanStor or OceanStor Dorado storage and resources need to be provisioned under a specified vStore, set this parameter to the URL of the logical management port of the vStore.</p>
</td>
</tr>
<tr id="row7127101841917"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p17111241100"><a name="en-us_topic_0000001324610777_p17111241100"></a><a name="en-us_topic_0000001324610777_p17111241100"></a>pools</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p1671172411012"><a name="en-us_topic_0000001324610777_p1671172411012"></a><a name="en-us_topic_0000001324610777_p1671172411012"></a>Storage pools of storage devices. The value format is a list.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p971172414020"><a name="en-us_topic_0000001324610777_p971172414020"></a><a name="en-us_topic_0000001324610777_p971172414020"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p19191715195117"><a name="p19191715195117"></a><a name="p19191715195117"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001324610777_p117122413014"><a name="en-us_topic_0000001324610777_p117122413014"></a><a name="en-us_topic_0000001324610777_p117122413014"></a>This parameter is optional when <strong id="b61986510578"><a name="b61986510578"></a><a name="b61986510578"></a>storage</strong> is set to <strong id="b122531563571"><a name="b122531563571"></a><a name="b122531563571"></a>oceanstor-dtree</strong> or <strong id="b199181445103215"><a name="b199181445103215"></a><a name="b199181445103215"></a>fusionstorage-dtree</strong>.</p>
</td>
</tr>
<tr id="row1312711851911"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p20613155814116"><a name="en-us_topic_0000001324610777_p20613155814116"></a><a name="en-us_topic_0000001324610777_p20613155814116"></a>parameters.protocol</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p12810447425"><a name="en-us_topic_0000001324610777_p12810447425"></a><a name="en-us_topic_0000001324610777_p12810447425"></a>Storage protocol. The value is a character string.</p>
<a name="en-us_topic_0000001324610777_ul5584070363"></a><a name="en-us_topic_0000001324610777_ul5584070363"></a><ul id="en-us_topic_0000001324610777_ul5584070363"><li>iscsi</li><li>fc</li><li>roce</li><li>fc-nvme</li><li>nfs</li><li>nfs+</li><li>dpc</li><li>scsi</li></ul>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1261313581616"><a name="en-us_topic_0000001324610777_p1261313581616"></a><a name="en-us_topic_0000001324610777_p1261313581616"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p109191715115118"><a name="p109191715115118"></a><a name="p109191715115118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><a name="ul555819319152"></a><a name="ul555819319152"></a><ul id="ul555819319152"><li>If the value is set to <strong id="b1581639153417"><a name="b1581639153417"></a><a name="b1581639153417"></a>iscsi</strong>, ensure that an iSCSI client has been installed on the connected compute node.</li><li>If the value is set to <strong id="b11543345153412"><a name="b11543345153412"></a><a name="b11543345153412"></a>nfs</strong>, ensure that an NFS client tool has been installed on the connected compute node.</li><li>If the value is set to <strong id="b12512055911"><a name="b12512055911"></a><a name="b12512055911"></a>nfs+</strong>, ensure that an NFS+ client tool has been installed on the connected compute node.</li><li>If the value is set to <strong id="b1411754103416"><a name="b1411754103416"></a><a name="b1411754103416"></a>fc-nvme</strong> or <strong id="b1041145423414"><a name="b1041145423414"></a><a name="b1041145423414"></a>roce</strong>, ensure that the nvme-cli tool has been installed on the connected compute node. The tool version must be 1.<em id="i15258104899"><a name="i15258104899"></a><a name="i15258104899"></a>x</em> and not earlier than 1.9. </li><li>If the value is set to <strong id="b121961053520"><a name="b121961053520"></a><a name="b121961053520"></a>dpc</strong>, ensure that DPC has been installed on the connected compute node and the node has been added as a DPC compute node on the storage device to be connected.</li><li>If the value is set to <strong id="b208248618352"><a name="b208248618352"></a><a name="b208248618352"></a>scsi</strong>, ensure that a distributed storage VBS client has been installed on the connected compute node.</li></ul>
</td>
</tr>
<tr id="row61271618121913"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p12730821724"><a name="en-us_topic_0000001324610777_p12730821724"></a><a name="en-us_topic_0000001324610777_p12730821724"></a>parameters.portals</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p127300212214"><a name="en-us_topic_0000001324610777_p127300212214"></a><a name="en-us_topic_0000001324610777_p127300212214"></a>Service access port. Nodes will use this port to read and write storage resources. The value format is a list.</p>
<p id="en-us_topic_0000001324610777_p166476473917"><a name="en-us_topic_0000001324610777_p166476473917"></a><a name="en-us_topic_0000001324610777_p166476473917"></a>Multiple ports can be configured if the protocol is <strong id="b144501934125913"><a name="b144501934125913"></a><a name="b144501934125913"></a>iscsi</strong>, <strong id="b94501934195913"><a name="b94501934195913"></a><a name="b94501934195913"></a>roce</strong>, or <strong id="b14450134105911"><a name="b14450134105911"></a><a name="b14450134105911"></a>nfs+</strong>. Only one port can be configured if the protocol is <strong id="b645017349592"><a name="b645017349592"></a><a name="b645017349592"></a>nfs</strong>. Service ports do not need to be configured if the protocol is <strong id="b545133435918"><a name="b545133435918"></a><a name="b545133435918"></a>fc</strong>, <strong id="b9451143465915"><a name="b9451143465915"></a><a name="b9451143465915"></a>fc-nvme</strong>, or <strong id="b1451203425919"><a name="b1451203425919"></a><a name="b1451203425919"></a>dpc</strong>. If the protocol is <strong id="b645116341596"><a name="b645116341596"></a><a name="b645116341596"></a>scsi</strong>, the port is in dictionary format where the key indicates the host name and the value indicates the IP address (only IPv4 addresses are supported).</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p8730621026"><a name="en-us_topic_0000001324610777_p8730621026"></a><a name="en-us_topic_0000001324610777_p8730621026"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p15919101510519"><a name="p15919101510519"></a><a name="p15919101510519"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><a name="ul73520114122"></a><a name="ul73520114122"></a><ul id="ul73520114122"><li>If a vStore or account is used to connect to a backend, <strong id="b0208627007"><a name="b0208627007"></a><a name="b0208627007"></a>portals</strong> must be set to the logical port information of the vStore or account.</li><li>If <strong id="b174162555018"><a name="b174162555018"></a><a name="b174162555018"></a>nfs</strong> or <strong id="b8805196902"><a name="b8805196902"></a><a name="b8805196902"></a>nfs+</strong> is used, the value can be a domain name.</li></ul>
</td>
</tr>
<tr id="row159281476499"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="p2092814473495"><a name="p2092814473495"></a><a name="p2092814473495"></a>parameters.ALUA</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="p1292874710497"><a name="p1292874710497"></a><a name="p1292874710497"></a>ALUA configuration of the storage backend. If the worker node uses the native multipathing software provided by the OS and ALUA is enabled, you need to configure this parameter.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="p179281474494"><a name="p179281474494"></a><a name="p179281474494"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p159191115165113"><a name="p159191115165113"></a><a name="p159191115165113"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="p592814711497"><a name="p592814711497"></a><a name="p592814711497"></a>If ALUA is enabled for the host multipathing software, ensure that the backend ALUA configuration is the same as that of the host ALUA configuration.</p>
<p id="p9408545184515"><a name="p9408545184515"></a><a name="p9408545184515"></a>For details about the ALUA configuration, see <a href="/css-docs/en/v4.7.0/advanced-features/configuring-alua/configuring-alua-using-helm">Configuring ALUA Using Helm</a>.</p>
</td>
</tr>
<tr id="row69321538172918"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="p2932193817290"><a name="p2932193817290"></a><a name="p2932193817290"></a>parameters.parentname</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="p19753720163619"><a name="p19753720163619"></a><a name="p19753720163619"></a>Name of a file system on the current storage device. Dtree is created in the file system.</p>
<p id="p13753520153612"><a name="p13753520153612"></a><a name="p13753520153612"></a>This parameter is optional when <strong id="b5811194616312"><a name="b5811194616312"></a><a name="b5811194616312"></a>storage</strong> is set to <strong id="b8363649163110"><a name="b8363649163110"></a><a name="b8363649163110"></a>oceanstor-dtree</strong> or <strong id="b1515475210314"><a name="b1515475210314"></a><a name="b1515475210314"></a>fusionstorage-dtree</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="p7932338112916"><a name="p7932338112916"></a><a name="p7932338112916"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p593283812910"><a name="p593283812910"></a><a name="p593283812910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="p17932638112915"><a name="p17932638112915"></a><a name="p17932638112915"></a>Query the name on the <strong id="b158145262210"><a name="b158145262210"></a><a name="b158145262210"></a>File Systems</strong> page of DeviceManager.</p>
</td>
</tr>
<tr id="row158363112216"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001276213416_p1619335616176"><a name="en-us_topic_0000001276213416_p1619335616176"></a><a name="en-us_topic_0000001276213416_p1619335616176"></a>metrovStorePairID</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="p03781853135"><a name="p03781853135"></a><a name="p03781853135"></a>HyperMetro vStore pair ID.</p>
<p id="en-us_topic_0000001276213416_p17485124117179"><a name="en-us_topic_0000001276213416_p17485124117179"></a><a name="en-us_topic_0000001276213416_p17485124117179"></a>This parameter is mandatory when a PV to be created on the storage side needs to support the NAS HyperMetro feature. In this case, you need to enter the ID of the HyperMetro vStore pair to which the PV to be created belongs.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001276213416_p1448594113173"><a name="en-us_topic_0000001276213416_p1448594113173"></a><a name="en-us_topic_0000001276213416_p1448594113173"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p391981511519"><a name="p391981511519"></a><a name="p391981511519"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001276213416_p568210171458"><a name="en-us_topic_0000001276213416_p568210171458"></a><a name="en-us_topic_0000001276213416_p568210171458"></a>You can query the HyperMetro vStore pair ID on DeviceManager.</p>
</td>
</tr>
<tr id="row3332581728"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001276213416_p179320619189"><a name="en-us_topic_0000001276213416_p179320619189"></a><a name="en-us_topic_0000001276213416_p179320619189"></a>metroBackend</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001276213416_p3494125991718"><a name="en-us_topic_0000001276213416_p3494125991718"></a><a name="en-us_topic_0000001276213416_p3494125991718"></a>Backend name of the HyperMetro peer. The value is a character string.</p>
<p id="p19322352557"><a name="p19322352557"></a><a name="p19322352557"></a>This parameter is mandatory when a PV to be created on the storage side needs to support the NAS HyperMetro feature. In this case, you need to enter the name of the other backend to form a HyperMetro pair with the current backend.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001276213416_p649485911172"><a name="en-us_topic_0000001276213416_p649485911172"></a><a name="en-us_topic_0000001276213416_p649485911172"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p1791951575111"><a name="p1791951575111"></a><a name="p1791951575111"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001276213416_p768261754513"><a name="en-us_topic_0000001276213416_p768261754513"></a><a name="en-us_topic_0000001276213416_p768261754513"></a>The names of the two backends in the pair must be entered. After the two backends form a HyperMetro relationship, they cannot form a HyperMetro relationship with other backends.</p>
</td>
</tr>
<tr id="row36316121111"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="p2064181219115"><a name="p2064181219115"></a><a name="p2064181219115"></a>supportedTopologies</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="p18642127115"><a name="p18642127115"></a><a name="p18642127115"></a>Storage topology awareness configuration. The parameter format is JSON of the list type.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="p864111251119"><a name="p864111251119"></a><a name="p864111251119"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p1191961545114"><a name="p1191961545114"></a><a name="p1191961545114"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="p176418120111"><a name="p176418120111"></a><a name="p176418120111"></a>This parameter is mandatory if storage topology awareness is enabled. For details, see <a href="/css-docs/en/v4.7.0/advanced-features/configuring-storage-topology-awareness/configuring-storage-topology-awareness-using-helm">Configuring Storage Topology Awareness Using Helm</a>.</p>
</td>
</tr>
<tr id="row11363104441311"><td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.1 "><p id="p0363164461310"><a name="p0363164461310"></a><a name="p0363164461310"></a>maxClientThreads</p>
</td>
<td class="cellrowborder" valign="top" width="32.67326732673267%" headers="mcps1.2.6.1.2 "><p id="p1236374461311"><a name="p1236374461311"></a><a name="p1236374461311"></a>Maximum number of concurrent connections to a storage backend.</p>
</td>
<td class="cellrowborder" valign="top" width="13.86138613861386%" headers="mcps1.2.6.1.3 "><p id="p43631344161310"><a name="p43631344161310"></a><a name="p43631344161310"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="11.881188118811878%" headers="mcps1.2.6.1.4 "><p id="p16919715145113"><a name="p16919715145113"></a><a name="p16919715145113"></a>30</p>
</td>
<td class="cellrowborder" valign="top" width="27.72277227722772%" headers="mcps1.2.6.1.5 "><p id="p7363204412133"><a name="p7363204412133"></a><a name="p7363204412133"></a>The value ranges from 1 to 30. If this parameter is not set or the value is not in the specified range, the default value 30 is used.</p>
</td>
</tr>
</tbody>
</table>

