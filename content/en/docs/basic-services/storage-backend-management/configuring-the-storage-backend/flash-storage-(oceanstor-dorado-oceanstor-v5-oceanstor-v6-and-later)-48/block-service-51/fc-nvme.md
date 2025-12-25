---
title: "FC-NVMe"
linkTitle: "FC-NVMe"
description: 
weight: 4
---

This section describes how to create a storage backend of the FC-NVMe protocol type.

## Configuration Item Description{#section2854172414476}

**Table  1**  backend parameters

<a name="table9126101819192"></a>
<table><thead align="left"><tr id="row10127131813194"><th class="cellrowborder" valign="top" width="13.266105345604077%" id="mcps1.2.6.1.1"><p id="p5631154913199"><a name="p5631154913199"></a><a name="p5631154913199"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="37.771685921284515%" id="mcps1.2.6.1.2"><p id="p463104991916"><a name="p463104991916"></a><a name="p463104991916"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="7.1176816134717065%" id="mcps1.2.6.1.3"><p id="p1463134917198"><a name="p1463134917198"></a><a name="p1463134917198"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="6.8533385549246155%" id="mcps1.2.6.1.4"><p id="p6919415195119"><a name="p6919415195119"></a><a name="p6919415195119"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="34.9911885647151%" id="mcps1.2.6.1.5"><p id="p10631049171910"><a name="p10631049171910"></a><a name="p10631049171910"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row111271188193"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p1233915445454"><a name="en-us_topic_0000001324610777_p1233915445454"></a><a name="en-us_topic_0000001324610777_p1233915445454"></a>storage</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p3339204417453"><a name="en-us_topic_0000001324610777_p3339204417453"></a><a name="en-us_topic_0000001324610777_p3339204417453"></a>Storage service type.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p533910449459"><a name="en-us_topic_0000001324610777_p533910449459"></a><a name="en-us_topic_0000001324610777_p533910449459"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p15919151545111"><a name="p15919151545111"></a><a name="p15919151545111"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001324610777_p17339174424512"><a name="en-us_topic_0000001324610777_p17339174424512"></a><a name="en-us_topic_0000001324610777_p17339174424512"></a>The value is fixed to <strong id="b84586301251912"><a name="b84586301251912"></a><a name="b84586301251912"></a>oceanstor-san</strong>.</p>
</td>
</tr>
<tr id="row15127618111910"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p733904424519"><a name="en-us_topic_0000001324610777_p733904424519"></a><a name="en-us_topic_0000001324610777_p733904424519"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p23903331109"><a name="en-us_topic_0000001324610777_p23903331109"></a><a name="en-us_topic_0000001324610777_p23903331109"></a>Storage backend name. The value can contain a maximum of 63 characters, including lowercase letters, digits, and hyphens (-). It must start with a letter or digit.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p18339944154510"><a name="en-us_topic_0000001324610777_p18339944154510"></a><a name="en-us_topic_0000001324610777_p18339944154510"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p18919015125112"><a name="p18919015125112"></a><a name="p18919015125112"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p1874481011019"><a name="p1874481011019"></a><a name="p1874481011019"></a>Ensure that the storage backend name is unique.</p>
</td>
</tr>
<tr id="row765135132312"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p1650357236"><a name="p1650357236"></a><a name="p1650357236"></a>namespace</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p1466335142311"><a name="p1466335142311"></a><a name="p1466335142311"></a>Namespace.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p176653592311"><a name="p176653592311"></a><a name="p176653592311"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p391981510517"><a name="p391981510517"></a><a name="p391981510517"></a>huawei-csi</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p866103515237"><a name="p866103515237"></a><a name="p866103515237"></a>The storage backend must be in the same namespace as Huawei CSI.</p>
</td>
</tr>
<tr id="row1212714182196"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p153399449451"><a name="en-us_topic_0000001324610777_p153399449451"></a><a name="en-us_topic_0000001324610777_p153399449451"></a>urls</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p430691742216"><a name="en-us_topic_0000001324610777_p430691742216"></a><a name="en-us_topic_0000001324610777_p430691742216"></a>Management URLs of the storage device. The value format is a list. The value can be a domain name or an IP address + port number.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1233934484518"><a name="en-us_topic_0000001324610777_p1233934484518"></a><a name="en-us_topic_0000001324610777_p1233934484518"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p691916153512"><a name="p691916153512"></a><a name="p691916153512"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><a name="ul96961628201612"></a><a name="ul96961628201612"></a><ul id="ul96961628201612"><li>If the management URL is of the IPv6 type, the URL format is <strong id="b12250664403570"><a name="b12250664403570"></a><a name="b12250664403570"></a>https://[</strong><em id="i14230450443570"><a name="i14230450443570"></a><a name="i14230450443570"></a>IPv6 address</em><strong id="b7087761393570"><a name="b7087761393570"></a><a name="b7087761393570"></a>]:</strong><em id="i9073075103570"><a name="i9073075103570"></a><a name="i9073075103570"></a>Port number</em>.</li></ul>
</td>
</tr>
<tr id="row7127101841917"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p17111241100"><a name="en-us_topic_0000001324610777_p17111241100"></a><a name="en-us_topic_0000001324610777_p17111241100"></a>pools</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p1671172411012"><a name="en-us_topic_0000001324610777_p1671172411012"></a><a name="en-us_topic_0000001324610777_p1671172411012"></a>Storage pools of storage devices. The value format is a list.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p971172414020"><a name="en-us_topic_0000001324610777_p971172414020"></a><a name="en-us_topic_0000001324610777_p971172414020"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p19191715195117"><a name="p19191715195117"></a><a name="p19191715195117"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001324610777_p117122413014"><a name="en-us_topic_0000001324610777_p117122413014"></a><a name="en-us_topic_0000001324610777_p117122413014"></a>Enter the storage pool names.</p>
</td>
</tr>
<tr id="row1312711851911"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p20613155814116"><a name="en-us_topic_0000001324610777_p20613155814116"></a><a name="en-us_topic_0000001324610777_p20613155814116"></a>parameters.protocol</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p12810447425"><a name="en-us_topic_0000001324610777_p12810447425"></a><a name="en-us_topic_0000001324610777_p12810447425"></a>Storage protocol. The value is a character string.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1261313581616"><a name="en-us_topic_0000001324610777_p1261313581616"></a><a name="en-us_topic_0000001324610777_p1261313581616"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p109191715115118"><a name="p109191715115118"></a><a name="p109191715115118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><a name="ul555819319152"></a><a name="ul555819319152"></a><ul id="ul555819319152"><li>The value is fixed to <strong id="b178941010123716"><a name="b178941010123716"></a><a name="b178941010123716"></a>fc-nvme</strong>.</li><li>Ensure that the nvme-cli tool has been installed on the compute node to be connected. The supported nvme-cli tool version is 1.9 and later.</li></ul>
</td>
</tr>
<tr id="row36316121111"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p2064181219115"><a name="p2064181219115"></a><a name="p2064181219115"></a>supportedTopologies</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p18642127115"><a name="p18642127115"></a><a name="p18642127115"></a>Storage topology awareness configuration. The parameter format is JSON of the list type.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p864111251119"><a name="p864111251119"></a><a name="p864111251119"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p1191961545114"><a name="p1191961545114"></a><a name="p1191961545114"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p176418120111"><a name="p176418120111"></a><a name="p176418120111"></a>This parameter is mandatory if storage topology awareness is enabled. For details, see <a href="/css-docs/en/docs/common-o-m-operations/configuring-storage-topology-awareness">Configuring Storage Topology Awareness</a>.</p>
</td>
</tr>
<tr id="row11363104441311"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p0363164461310"><a name="p0363164461310"></a><a name="p0363164461310"></a>maxClientThreads</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p1236374461311"><a name="p1236374461311"></a><a name="p1236374461311"></a>Maximum number of concurrent connections to a storage backend.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p43631344161310"><a name="p43631344161310"></a><a name="p43631344161310"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p16919715145113"><a name="p16919715145113"></a><a name="p16919715145113"></a>30</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p7363204412133"><a name="p7363204412133"></a><a name="p7363204412133"></a>The value ranges from <strong id="b18196838304313"><a name="b18196838304313"></a><a name="b18196838304313"></a>1</strong> to <strong id="b10489190704313"><a name="b10489190704313"></a><a name="b10489190704313"></a>30</strong>. If this parameter is not set or the value is not in the specified range, the default value <strong id="b13276111504313"><a name="b13276111504313"></a><a name="b13276111504313"></a>30</strong> is used.</p>
</td>
</tr>
<tr id="row51574418229"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p3158541228"><a name="p3158541228"></a><a name="p3158541228"></a>authenticationMode</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p31581743223"><a name="p31581743223"></a><a name="p31581743223"></a>Authentication mode for logging in to a storage backend.</p>
<p id="p13386105733415"><a name="p13386105733415"></a><a name="p13386105733415"></a>The following modes are supported:</p>
<a name="ul41301430359"></a><a name="ul41301430359"></a><ul id="ul41301430359"><li><strong id="b1406895323448"><a name="b1406895323448"></a><a name="b1406895323448"></a>local</strong>: local authentication</li><li><strong id="b2888137064414"><a name="b2888137064414"></a><a name="b2888137064414"></a>ldap</strong>: LDAP authentication</li></ul>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p315894172213"><a name="p315894172213"></a><a name="p315894172213"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p121587482213"><a name="p121587482213"></a><a name="p121587482213"></a>local</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p1481202562916"><a name="p1481202562916"></a><a name="p1481202562916"></a>When Huawei enterprise storage is OceanStor V5, the ID of the LDAP domain authentication server must be 0.</p>
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
      protocol: "fc-nvme"
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
    huawei-csi    backend-demo    fc-nvme     oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    ```

