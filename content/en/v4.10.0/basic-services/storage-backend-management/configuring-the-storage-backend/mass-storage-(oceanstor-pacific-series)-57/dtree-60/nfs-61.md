---
title: "NFS"
linkTitle: "NFS"
description: 
weight: 1
---

This section describes how to create a storage backend of the NFS protocol type.

## Configuration Item Description{#section664923118183}

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
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001324610777_p17339174424512"><a name="en-us_topic_0000001324610777_p17339174424512"></a><a name="en-us_topic_0000001324610777_p17339174424512"></a>The value is fixed to <strong id="b42327914448"><a name="b42327914448"></a><a name="b42327914448"></a>fusionstorage-dtree</strong>.</p>
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
<tr id="row1218054742718"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p14180194702714"><a name="p14180194702714"></a><a name="p14180194702714"></a>accountName</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p1518094762719"><a name="p1518094762719"></a><a name="p1518094762719"></a>Account name on the storage side.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p1237175019184"><a name="p1237175019184"></a><a name="p1237175019184"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p20919715115120"><a name="p20919715115120"></a><a name="p20919715115120"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p195481349369"><a name="p195481349369"></a><a name="p195481349369"></a>This parameter is mandatory when NAS resources need to be provisioned under a specified account.</p>
</td>
</tr>
<tr id="row1212714182196"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p153399449451"><a name="en-us_topic_0000001324610777_p153399449451"></a><a name="en-us_topic_0000001324610777_p153399449451"></a>urls</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p430691742216"><a name="en-us_topic_0000001324610777_p430691742216"></a><a name="en-us_topic_0000001324610777_p430691742216"></a>Management URLs of the storage device. The value format is a list.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p1233934484518"><a name="en-us_topic_0000001324610777_p1233934484518"></a><a name="en-us_topic_0000001324610777_p1233934484518"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p691916153512"><a name="p691916153512"></a><a name="p691916153512"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p9969155711201"><a name="p9969155711201"></a><a name="p9969155711201"></a>The value can be a domain name or an IP address + port number.</p>
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
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><a name="ul555819319152"></a><a name="ul555819319152"></a><ul id="ul555819319152"><li>The value is fixed to <strong id="b14861191914736"><a name="b14861191914736"></a><a name="b14861191914736"></a>nfs</strong>.</li><li>Ensure that an NFS client tool has been installed on the connected compute node.</li></ul>
</td>
</tr>
<tr id="row61271618121913"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001324610777_p12730821724"><a name="en-us_topic_0000001324610777_p12730821724"></a><a name="en-us_topic_0000001324610777_p12730821724"></a>parameters.portals</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001324610777_p127300212214"><a name="en-us_topic_0000001324610777_p127300212214"></a><a name="en-us_topic_0000001324610777_p127300212214"></a>Service access port. Nodes will use this port to read and write storage resources. The value format is a list.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0000001324610777_p8730621026"><a name="en-us_topic_0000001324610777_p8730621026"></a><a name="en-us_topic_0000001324610777_p8730621026"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p15919101510519"><a name="p15919101510519"></a><a name="p15919101510519"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><a name="ul73520114122"></a><a name="ul73520114122"></a><ul id="ul73520114122"><li>If an account is used to connect to a backend, <strong id="b2436008659335"><a name="b2436008659335"></a><a name="b2436008659335"></a>portals</strong> must be set to the logical port information of the account.</li><li>You can enter a domain name address.</li></ul>
</td>
</tr>
<tr id="row69321538172918"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p2932193817290"><a name="p2932193817290"></a><a name="p2932193817290"></a>parameters.parentname</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p19753720163619"><a name="p19753720163619"></a><a name="p19753720163619"></a>Name of a file system on the current storage device. A dtree is created in the file system.</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p7932338112916"><a name="p7932338112916"></a><a name="p7932338112916"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p593283812910"><a name="p593283812910"></a><a name="p593283812910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><a name="ul79421446192713"></a><a name="ul79421446192713"></a><ul id="ul79421446192713"><li>Query the name on the <strong id="b1397716991595"><a name="b1397716991595"></a><a name="b1397716991595"></a>File Systems</strong> page of DeviceManager.</li><li>You can configure the parameter in StorageClass.</li></ul>
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
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p7363204412133"><a name="p7363204412133"></a><a name="p7363204412133"></a>The value ranges from <strong id="b18505119254318"><a name="b18505119254318"></a><a name="b18505119254318"></a>1</strong> to <strong id="b5325049434318"><a name="b5325049434318"></a><a name="b5325049434318"></a>30</strong>. If this parameter is not set or the value is not in the specified range, the default value <strong id="b19927642004318"><a name="b19927642004318"></a><a name="b19927642004318"></a>30</strong> is used.</p>
</td>
</tr>
</tbody>
</table>

## Creating a Storage Backend{#section813617238389}

1.  Prepare a backend configuration file, for example,  **backend.yaml**.

    ```yaml
    storage: "fusionstorage-dtree"
    name: "backend-demo"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.157:8088"
    parameters:
      protocol: "nfs"
      parentname: "parent-filesystem"
      portals:
        - "10.10.30.20"
    maxClientThreads: "30"
    ```

2.  Run the following command to create a storage backend.

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml
    ```

    The following is an example of the command output.

    ```
    NUMBER  CONFIGURED    NAME           STORAGE              URLS                
    1       false         backend-demo   fusionstorage-dtree  https://192.168.129.157:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

3.  Enter the serial number of the backend to be created and enter the account and password.

    ```
    Please enter the backend number to configure (Enter 'exit' to exit):1
    Please enter this backend user name: admin
    Please enter this backend password:
    
    Backend backend-demo is configured
    NUMBER  CONFIGURED    NAME            STORAGE              URLS               
    1       true          backend-demo    fusionstorage-dtree  https://192.168.129.157:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

4.  Check the storage backend creation result.

    ```
    oceanctl get backend
    ```

    The following is an example of the command output. If the backend status is  **Bound**, the creation is successful.

    ```
    NAMESPACE     NAME            PROTOCOL    STORAGETYPE           SN            STATUS  ONLINE  URL                 
    huawei-csi    backend-demo    nfs         fusionstorage-dtree                 Bound   true    https://192.168.129.157:8088   
    ```

