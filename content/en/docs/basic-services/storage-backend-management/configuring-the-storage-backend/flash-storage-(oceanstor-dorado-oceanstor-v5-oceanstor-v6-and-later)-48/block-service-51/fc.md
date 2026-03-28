---
title: "FC"
linkTitle: "FC"
description: 
weight: 2
---

This section describes how to create a storage backend of the FC protocol type.

## Configuration Item Description{#section2854172414476}

**Table  1**  backend parameters

<a name="table9126101819192"></a>
<table><thead align="left"><tr id="row10127131813194"><th class="cellrowborder" valign="top" width="16.504854368932037%" id="mcps1.2.6.1.1"><p id="p5631154913199"><a name="p5631154913199"></a><a name="p5631154913199"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="27.18446601941747%" id="mcps1.2.6.1.2"><p id="p463104991916"><a name="p463104991916"></a><a name="p463104991916"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="16.504854368932037%" id="mcps1.2.6.1.3"><p id="p1463134917198"><a name="p1463134917198"></a><a name="p1463134917198"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="14.563106796116502%" id="mcps1.2.6.1.4"><p id="p6919415195119"><a name="p6919415195119"></a><a name="p6919415195119"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="25.242718446601938%" id="mcps1.2.6.1.5"><p id="p10631049171910"><a name="p10631049171910"></a><a name="p10631049171910"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row111271188193"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p1233915445454"><a name="en-us_topic_0000001324610777_p1233915445454"></a><a name="en-us_topic_0000001324610777_p1233915445454"></a>storage</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p3339204417453"><a name="en-us_topic_0000001324610777_p3339204417453"></a><a name="en-us_topic_0000001324610777_p3339204417453"></a>Storage service type.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p533910449459"><a name="en-us_topic_0000001324610777_p533910449459"></a><a name="en-us_topic_0000001324610777_p533910449459"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p15919151545111"><a name="p15919151545111"></a><a name="p15919151545111"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001324610777_p17339174424512"><a name="en-us_topic_0000001324610777_p17339174424512"></a><a name="en-us_topic_0000001324610777_p17339174424512"></a>The value is fixed at <strong id="b8818928112620"><a name="b8818928112620"></a><a name="b8818928112620"></a>oceanstor-san</strong>.</p>
</td>
</tr>
<tr id="row15127618111910"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p733904424519"><a name="en-us_topic_0000001324610777_p733904424519"></a><a name="en-us_topic_0000001324610777_p733904424519"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p23903331109"><a name="en-us_topic_0000001324610777_p23903331109"></a><a name="en-us_topic_0000001324610777_p23903331109"></a>Storage backend name. The value can contain a maximum of 63 characters, including lowercase letters, digits, and hyphens (-). It must start with a letter or digit.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p18339944154510"><a name="en-us_topic_0000001324610777_p18339944154510"></a><a name="en-us_topic_0000001324610777_p18339944154510"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p18919015125112"><a name="p18919015125112"></a><a name="p18919015125112"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="p1874481011019"><a name="p1874481011019"></a><a name="p1874481011019"></a>Ensure that the storage backend name is unique.</p>
</td>
</tr>
<tr id="row765135132312"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="p1650357236"><a name="p1650357236"></a><a name="p1650357236"></a>namespace</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="p1466335142311"><a name="p1466335142311"></a><a name="p1466335142311"></a>Namespace.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="p176653592311"><a name="p176653592311"></a><a name="p176653592311"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p391981510517"><a name="p391981510517"></a><a name="p391981510517"></a>huawei-csi</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="p866103515237"><a name="p866103515237"></a><a name="p866103515237"></a>The storage backend must be in the same namespace as Huawei CSI.</p>
</td>
</tr>
<tr id="row1212714182196"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p153399449451"><a name="en-us_topic_0000001324610777_p153399449451"></a><a name="en-us_topic_0000001324610777_p153399449451"></a>urls</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p430691742216"><a name="en-us_topic_0000001324610777_p430691742216"></a><a name="en-us_topic_0000001324610777_p430691742216"></a>Management URLs of the storage device. The value format is a list. The value can be a domain name or an IP address + port number.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1233934484518"><a name="en-us_topic_0000001324610777_p1233934484518"></a><a name="en-us_topic_0000001324610777_p1233934484518"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p691916153512"><a name="p691916153512"></a><a name="p691916153512"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><a name="ul96961628201612"></a><a name="ul96961628201612"></a><ul id="ul96961628201612"><li>If the management URL is of the IPv6 type, the URL format is <strong id="b16075115435658"><a name="b16075115435658"></a><a name="b16075115435658"></a>https://[</strong><em id="i189203311035658"><a name="i189203311035658"></a><a name="i189203311035658"></a>IPv6 address</em><strong id="b204307326835658"><a name="b204307326835658"></a><a name="b204307326835658"></a>]:</strong><em id="i2157677235658"><a name="i2157677235658"></a><a name="i2157677235658"></a>Port number</em>.</li></ul>
</td>
</tr>
<tr id="row7127101841917"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p17111241100"><a name="en-us_topic_0000001324610777_p17111241100"></a><a name="en-us_topic_0000001324610777_p17111241100"></a>pools</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p1671172411012"><a name="en-us_topic_0000001324610777_p1671172411012"></a><a name="en-us_topic_0000001324610777_p1671172411012"></a>Storage pools of storage devices. The value format is a list.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p971172414020"><a name="en-us_topic_0000001324610777_p971172414020"></a><a name="en-us_topic_0000001324610777_p971172414020"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p19191715195117"><a name="p19191715195117"></a><a name="p19191715195117"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001324610777_p117122413014"><a name="en-us_topic_0000001324610777_p117122413014"></a><a name="en-us_topic_0000001324610777_p117122413014"></a>Enter the storage pool names.</p>
</td>
</tr>
<tr id="row1312711851911"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p20613155814116"><a name="en-us_topic_0000001324610777_p20613155814116"></a><a name="en-us_topic_0000001324610777_p20613155814116"></a>parameters.protocol</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p12810447425"><a name="en-us_topic_0000001324610777_p12810447425"></a><a name="en-us_topic_0000001324610777_p12810447425"></a>Storage protocol. The value is a character string.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1261313581616"><a name="en-us_topic_0000001324610777_p1261313581616"></a><a name="en-us_topic_0000001324610777_p1261313581616"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p109191715115118"><a name="p109191715115118"></a><a name="p109191715115118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><a name="ul1295371272019"></a><a name="ul1295371272019"></a><ul id="ul1295371272019"><li>The value is fixed at <strong id="b13261045132619"><a name="b13261045132619"></a><a name="b13261045132619"></a>fc</strong>.</li></ul>
</td>
</tr>
<tr id="row341561664412"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="p1993622194320"><a name="p1993622194320"></a><a name="p1993622194320"></a>parameters.ALUA</p>
<p id="p1247462414531"><a name="p1247462414531"></a><a name="p1247462414531"></a></p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="p13334182974311"><a name="p13334182974311"></a><a name="p13334182974311"></a>ALUA configuration of the storage backend. If the worker node uses the native multipathing software provided by the OS and ALUA is enabled, you need to configure this parameter.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="p1879919341434"><a name="p1879919341434"></a><a name="p1879919341434"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p1826418436"><a name="p1826418436"></a><a name="p1826418436"></a>-</p>
<p id="p44741924115319"><a name="p44741924115319"></a><a name="p44741924115319"></a></p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="p1496214564317"><a name="p1496214564317"></a><a name="p1496214564317"></a>If ALUA is enabled for the host multipathing software, ensure that the backend ALUA configuration is the same as that of the host ALUA configuration. For details, see <a href="/css-docs/en/docs/common-o-m-operations/configuring-alua">Configuring ALUA</a>.</p>
</td>
</tr>
<tr id="row36316121111"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="p2064181219115"><a name="p2064181219115"></a><a name="p2064181219115"></a>supportedTopologies</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="p18642127115"><a name="p18642127115"></a><a name="p18642127115"></a>Storage topology awareness configuration. The parameter format is JSON of the list type.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="p864111251119"><a name="p864111251119"></a><a name="p864111251119"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p1191961545114"><a name="p1191961545114"></a><a name="p1191961545114"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="p176418120111"><a name="p176418120111"></a><a name="p176418120111"></a>This parameter is mandatory if storage topology awareness is enabled. For details, see <a href="/css-docs/en/docs/common-o-m-operations/configuring-storage-topology-awareness">Configuring Storage Topology Awareness</a>.</p>
</td>
</tr>
<tr id="row11363104441311"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="p0363164461310"><a name="p0363164461310"></a><a name="p0363164461310"></a>maxClientThreads</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="p1236374461311"><a name="p1236374461311"></a><a name="p1236374461311"></a>Maximum number of concurrent connections to a storage backend.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="p43631344161310"><a name="p43631344161310"></a><a name="p43631344161310"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p16919715145113"><a name="p16919715145113"></a><a name="p16919715145113"></a>30</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="p7363204412133"><a name="p7363204412133"></a><a name="p7363204412133"></a>The value ranges from <strong id="b8067623594311"><a name="b8067623594311"></a><a name="b8067623594311"></a>1</strong> to <strong id="b9593441834311"><a name="b9593441834311"></a><a name="b9593441834311"></a>30</strong>. If this parameter is not set or the value is not in the specified range, the default value <strong id="b11853287454311"><a name="b11853287454311"></a><a name="b11853287454311"></a>30</strong> is used.</p>
</td>
</tr>
<tr id="row51574418229"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="p3158541228"><a name="p3158541228"></a><a name="p3158541228"></a>authenticationMode</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="p31581743223"><a name="p31581743223"></a><a name="p31581743223"></a>Authentication mode for logging in to a storage backend.</p>
<p id="p13386105733415"><a name="p13386105733415"></a><a name="p13386105733415"></a>The following modes are supported:</p>
<a name="ul41301430359"></a><a name="ul41301430359"></a><ul id="ul41301430359"><li><strong id="b845135080446"><a name="b845135080446"></a><a name="b845135080446"></a>local</strong>: local authentication</li><li><strong id="b6182382614412"><a name="b6182382614412"></a><a name="b6182382614412"></a>ldap</strong>: LDAP authentication</li></ul>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="p315894172213"><a name="p315894172213"></a><a name="p315894172213"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p121587482213"><a name="p121587482213"></a><a name="p121587482213"></a>local</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="p1035410219267"><a name="p1035410219267"></a><a name="p1035410219267"></a>When Huawei enterprise storage is OceanStor V5, the ID of the LDAP domain authentication server must be 0.</p>
</td>
</tr>
<tr id="row3444146104214"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001276213416_p179320619189"><a name="en-us_topic_0000001276213416_p179320619189"></a><a name="en-us_topic_0000001276213416_p179320619189"></a>metroBackend</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001276213416_p3494125991718"><a name="en-us_topic_0000001276213416_p3494125991718"></a><a name="en-us_topic_0000001276213416_p3494125991718"></a>Backend name of the HyperMetro peer. The value is a character string.</p>
<p id="p19322352557"><a name="p19322352557"></a><a name="p19322352557"></a>This parameter is mandatory when a PV to be created on the storage side needs to support the SAN HyperMetro feature. In this case, you need to enter the name of the other backend to form a HyperMetro pair with the current backend.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="p1653215216187"><a name="p1653215216187"></a><a name="p1653215216187"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p1791951575111"><a name="p1791951575111"></a><a name="p1791951575111"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001276213416_p768261754513"><a name="en-us_topic_0000001276213416_p768261754513"></a><a name="en-us_topic_0000001276213416_p768261754513"></a>The names of the two backends in the pair must be entered. After the two backends form a HyperMetro relationship, they cannot form a HyperMetro relationship with other backends.</p>
</td>
</tr>
<tr id="row644418614218"><td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001276213416_p1619335616176"><a name="en-us_topic_0000001276213416_p1619335616176"></a><a name="en-us_topic_0000001276213416_p1619335616176"></a>hyperMetroDomain</p>
</td>
<td class="cellrowborder" valign="top" width="27.18446601941747%" headers="mcps1.2.6.1.2 "><p id="p03781853135"><a name="p03781853135"></a><a name="p03781853135"></a>HyperMetro domain name.</p>
<p id="en-us_topic_0000001276213416_p17485124117179"><a name="en-us_topic_0000001276213416_p17485124117179"></a><a name="en-us_topic_0000001276213416_p17485124117179"></a>This parameter is mandatory when a PV to be created on the storage side needs to support the SAN HyperMetro feature. In this case, you need to enter the name of the HyperMetro domain to which the PV to be created belongs.</p>
</td>
<td class="cellrowborder" valign="top" width="16.504854368932037%" headers="mcps1.2.6.1.3 "><p id="p1382133417179"><a name="p1382133417179"></a><a name="p1382133417179"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="14.563106796116502%" headers="mcps1.2.6.1.4 "><p id="p391981511519"><a name="p391981511519"></a><a name="p391981511519"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="25.242718446601938%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001276213416_p568210171458"><a name="en-us_topic_0000001276213416_p568210171458"></a><a name="en-us_topic_0000001276213416_p568210171458"></a>You can query the HyperMetro domain name on DeviceManager.</p>
</td>
</tr>
</tbody>
</table>

## Creating a Storage Backend{#section427044474916}

1.  Prepare a backend configuration file, for example,  **backend.yaml**.

    ```yaml
    storage: "oceanstor-san"
    name: "backend-demo"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.157:8088"
    pools:
      - "StoragePool001"
    parameters:
      protocol: "fc"
    maxClientThreads: "30"
    ```

2.  Run the following command to create a storage backend.

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml
    ```

    The following is an example of the command output.

    ```
    NUMBER  CONFIGURED    NAME           STORAGE              URLS                
    1       false         backend-demo   oceanstor-san        https://192.168.129.157:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

3.  Enter the serial number of the backend to be created and enter the account and password.

    ```
    Please enter the backend number to configure (Enter 'exit' to exit):1
    Please enter this backend user name: admin
    Please enter this backend password:
    
    Backend backend-demo is configured
    NUMBER  CONFIGURED    NAME            STORAGE              URLS               
    1       true          backend-demo    oceanstor-san        https://192.168.129.157:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

4.  Check the storage backend creation result.

    ```
    oceanctl get backend
    ```

    The following is an example of the command output. If the backend status is  **Bound**, the creation is successful.

    ```
    NAMESPACE     NAME            PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-demo    fc          oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    ```

## Creating Storage Backends of the HyperMetro Type{#section1540717120711}

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   Before configuring SAN HyperMetro, you need to configure the HyperMetro relationship between two storage devices, including the remote device and HyperMetro domain. For details, see the product documentation of the corresponding storage model.

1.  Prepare a storage backend configuration file, for example,  **backend.yaml**.

    ```
    storage: "oceanstor-san"
    name: "backend-active"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.155:8088"
    pools:
      - "StoragePool001"
    hyperMetroDomain: "BlockHyperMetroDomain"
    metroBackend: "backend-standby"
    parameters:
      protocol: "fc"
    maxClientThreads: "30"
    ---
    storage: "oceanstor-san"
    name: "backend-standby"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.157:8088"
    pools:
      - "StoragePool001"
    hyperMetroDomain: "BlockHyperMetroDomain"
    metroBackend: "backend-active"
    parameters:
      protocol: "fc"
    maxClientThreads: "30"
    ```

2.  Run the following command to create a storage backend.

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml
    ```

    The following is an example of the command output.

    ```
    NUMBER  CONFIGURED    NAME              STORAGE              URLS                
    1       false         backend-active    oceanstor-san        https://192.168.129.155:8088 
    2       false         backend-standby   oceanstor-san        https://192.168.129.157:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

3.  Enter the serial number of the backend to be created and enter the account and password.

    ```
    Please enter the backend number to configure (Enter 'exit' to exit):1
    Please enter this backend user name: user1
    Please enter this backend password:
    
    Backend backend-standby is configured
    NUMBER  CONFIGURED    NAME              STORAGE              URLS               
    1       true          backend-active    oceanstor-san        https://192.168.129.155:8088 
    2       true          backend-standby   oceanstor-san        https://192.168.129.157:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

4.  Check the storage backend creation result.

    ```
    oceanctl get backend
    ```

    The following is an example of the command output. If the backend status is  **Bound**, the creation is successful.

    ```
    NAMESPACE     NAME              PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-active    fc          oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.155:8088   
    huawei-csi    backend-standby   fc          oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088 
    ```

