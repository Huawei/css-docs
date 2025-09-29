---
title: "File System"
linkTitle: "File System"
description: 
weight: 1
---

## Creating a StorageClass{#section1071213595715}

1.  Prepare a StorageClass configuration file, for example,  **msc .yaml**. For details about the StorageClass configuration, see the following example.
2.  Run the following command to create a StorageClass using the configuration file.

    ```
    kubectl apply -f mysc.yaml
    ```

3.  Run the following command to view the information about the created StorageClass.

    ```
    kubectl get sc mysc
    ```

    The following is an example of the command output.

    ```
    NAME   PROVISIONER      RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
    mysc   csi.huawei.com   Delete          Immediate           true                   8s
    ```

## NFS Protocol Configuration Example{#section1053116812255}

When a container uses the NFS protocol to connect to file system resources, refer to the following StorageClass configuration example. In this example, NFS version 4.1 is specified for mounting.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-nas-181
  pool: pool001
  volumeType: fs
  allocType: thin
  authClient: "*"
mountOptions:
  - nfsvers=4.1 # Specify the version 4.1 for NFS mounting.
```

## DPC Protocol Configuration Example{#section420824715129}

When the storage supports access using the DPC protocol, you can configure the mount parameters for DPC access in the StorageClass. In this example,  **acl**  is used as the authentication parameter for mounting, and  **cnflush**  is used to set the asynchronous disk flushing mode.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dpc-101
  pool: pool001
  volumeType: fs
  allocType: thin
mountOptions:
  - acl # Set the authentication parameter.
  - cnflush # Set the asynchronous disk flushing mode.
```

## StorageClass Parameters Supported by File Systems{#section1758842912252}

**Table  1**  StorageClass configuration parameters

<a name="en-us_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="en-us_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="18.481557577536446%" id="mcps1.2.7.1.1"><p id="en-us_topic_0000001162111564_p875071122919"><a name="en-us_topic_0000001162111564_p875071122919"></a><a name="en-us_topic_0000001162111564_p875071122919"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="23.089717248801485%" id="mcps1.2.7.1.2"><p id="en-us_topic_0000001162111564_p17750131113295"><a name="en-us_topic_0000001162111564_p17750131113295"></a><a name="en-us_topic_0000001162111564_p17750131113295"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="6.848644946678408%" id="mcps1.2.7.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="8.453184619900206%" id="mcps1.2.7.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="7.35740142843166%" id="mcps1.2.7.1.5"><p id="p1113325565918"><a name="p1113325565918"></a><a name="p1113325565918"></a>Whether the Volume Management Takes Effect</p>
</th>
<th class="cellrowborder" valign="top" width="35.7694941786518%" id="mcps1.2.7.1.6"><p id="en-us_topic_0000001162111564_p075011113295"><a name="en-us_topic_0000001162111564_p075011113295"></a><a name="en-us_topic_0000001162111564_p075011113295"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p4750141111292"><a name="en-us_topic_0000001162111564_p4750141111292"></a><a name="en-us_topic_0000001162111564_p4750141111292"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p475091120296"><a name="en-us_topic_0000001162111564_p475091120296"></a><a name="en-us_topic_0000001162111564_p475091120296"></a>User-defined name of a StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p16133655135913"><a name="p16133655135913"></a><a name="p16133655135913"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p861713973915"><a name="en-us_topic_0000001162111564_p861713973915"></a><a name="en-us_topic_0000001162111564_p861713973915"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p8750161119299"><a name="en-us_topic_0000001162111564_p8750161119299"></a><a name="en-us_topic_0000001162111564_p8750161119299"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p15750201119295"><a name="en-us_topic_0000001162111564_p15750201119295"></a><a name="en-us_topic_0000001162111564_p15750201119295"></a>Name of the provisioner.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p0133955185920"><a name="p0133955185920"></a><a name="p0133955185920"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>Set this parameter to the driver name set during Huawei CSI installation.</p>
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>The value is the same as that of <strong id="b1223814278013"><a name="b1223814278013"></a><a name="b1223814278013"></a>driverName</strong> in the <strong id="b1649220321700"><a name="b1649220321700"></a><a name="b1649220321700"></a>values.yaml</strong> file.</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p119108535312"><a name="p119108535312"></a><a name="p119108535312"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p16910135393118"><a name="p16910135393118"></a><a name="p16910135393118"></a>Reclamation policy. The following types are supported:</p>
<a name="ul5209917195517"></a><a name="ul5209917195517"></a><ul id="ul5209917195517"><li><strong id="b39881432511"><a name="b39881432511"></a><a name="b39881432511"></a>Delete</strong>: Resources are automatically reclaimed.</li><li><strong id="b15829858448"><a name="b15829858448"></a><a name="b15829858448"></a>Retain</strong>: Resources are manually reclaimed.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p11332055125915"><a name="p11332055125915"></a><a name="p11332055125915"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li><strong id="b48131861150"><a name="b48131861150"></a><a name="b48131861150"></a>Delete</strong>: When a PV/PVC is deleted, resources on the storage device are also deleted.</li><li><strong id="b52391026851"><a name="b52391026851"></a><a name="b52391026851"></a>Retain</strong>: When a PV/PVC is deleted, resources on the storage device are not deleted.</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p192771821155012"><a name="p192771821155012"></a><a name="p192771821155012"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p8277132112501"><a name="p8277132112501"></a><a name="p8277132112501"></a>Whether to allow volume expansion. If this parameter is set to <strong id="b494616718617"><a name="b494616718617"></a><a name="b494616718617"></a>true</strong>, the capacity of the PV that uses the StorageClass can be expanded.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1613325519595"><a name="p1613325519595"></a><a name="p1613325519595"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p13923171118495"><a name="p13923171118495"></a><a name="p13923171118495"></a>This function can only be used to expand PV capacity but cannot be used to reduce PV capacity.</p>
</td>
</tr>
<tr id="row63343268297"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p13432132752911"><a name="p13432132752911"></a><a name="p13432132752911"></a>mountOptions</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p134321427192916"><a name="p134321427192916"></a><a name="p134321427192916"></a>List of mount parameters, which can be used to specify the parameters of the <strong id="b938691915113"><a name="b938691915113"></a><a name="b938691915113"></a>-o</strong> option when the <strong id="b1420143218111"><a name="b1420143218111"></a><a name="b1420143218111"></a>mount</strong> command is executed on a host.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p2432227172910"><a name="p2432227172910"></a><a name="p2432227172910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1432112762919"><a name="p1432112762919"></a><a name="p1432112762919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1613355555915"><a name="p1613355555915"></a><a name="p1613355555915"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p15432162772912"><a name="p15432162772912"></a><a name="p15432162772912"></a>For details about common parameters in <strong id="b1945445410117"><a name="b1945445410117"></a><a name="b1945445410117"></a>mountOptions</strong>, see <a href="#table65545557506">Table 2</a>.</p>
<p id="p104322027152920"><a name="p104322027152920"></a><a name="p104322027152920"></a>You can also specify other mount parameters.</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>Name of the backend where the resource to be created is located. This field must be set if <strong id="b1904344191919"><a name="b1904344191919"></a><a name="b1904344191919"></a>parameters.pool</strong> is set.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p184571869188"><a name="p184571869188"></a><a name="p184571869188"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>If this parameter is not set, Huawei CSI will randomly select a backend that meets the capacity requirements to create resources.</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>You are advised to specify a backend to ensure that the created resource is located on the expected backend.</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p395711171674"><a name="p395711171674"></a><a name="p395711171674"></a>parameters.pool</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p119571517771"><a name="p119571517771"></a><a name="p119571517771"></a>Name of the storage resource pool where the resource to be created is located.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p43701077524"><a name="p43701077524"></a><a name="p43701077524"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p12398310135213"><a name="p12398310135213"></a><a name="p12398310135213"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p445711620185"><a name="p445711620185"></a><a name="p445711620185"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p99571317978"><a name="p99571317978"></a><a name="p99571317978"></a>If this parameter is not set, Huawei CSI will randomly select a storage pool that meets the capacity requirements from the selected backend to create resources. You are advised to specify a storage pool to ensure that the created resource is located in the expected storage pool.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p1775061119292"><a name="en-us_topic_0000001162111564_p1775061119292"></a><a name="en-us_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p975011122920"><a name="en-us_topic_0000001162111564_p975011122920"></a><a name="en-us_topic_0000001162111564_p975011122920"></a>Type of the volume to be created. The following types are supported:</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li><strong id="b1733717591123"><a name="b1733717591123"></a><a name="b1733717591123"></a>lun</strong>: A LUN is provisioned on the storage side.</li><li><strong id="b10216124101312"><a name="b10216124101312"></a><a name="b10216124101312"></a>fs</strong>: A file system is provisioned on the storage side.</li><li><strong id="b1412435781313"><a name="b1412435781313"></a><a name="b1412435781313"></a>dtree</strong>: A volume of the Dtree type is provisioned on the storage side.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p845812615184"><a name="p845812615184"></a><a name="p845812615184"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p159151023181412"><a name="p159151023181412"></a><a name="p159151023181412"></a>The value is fixed to <strong id="b980715176283"><a name="b980715176283"></a><a name="b980715176283"></a>fs</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p13750171110290"><a name="en-us_topic_0000001162111564_p13750171110290"></a><a name="en-us_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p67501211102911"><a name="en-us_topic_0000001162111564_p67501211102911"></a><a name="en-us_topic_0000001162111564_p67501211102911"></a>Allocation type of the volume to be created. The following types are supported:</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li><strong id="b0621115111132"><a name="b0621115111132"></a><a name="b0621115111132"></a>thin</strong>: Not all required space is allocated during creation. Instead, the space is dynamically allocated based on the usage.</li><li><strong id="b1051217771412"><a name="b1051217771412"></a><a name="b1051217771412"></a>thick</strong>: All required space is allocated during creation.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>thin</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p14582641817"><a name="p14582641817"></a><a name="p14582641817"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p57502011142910"><a name="en-us_topic_0000001162111564_p57502011142910"></a><a name="en-us_topic_0000001162111564_p57502011142910"></a>If this parameter is set to <strong id="b18263191015196"><a name="b18263191015196"></a><a name="b18263191015196"></a>thin</strong>, the required space is not allocated immediately when a volume is created. Instead, the space is dynamically allocated based on the usage.</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p499022713590"><a name="p499022713590"></a><a name="p499022713590"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p552215442213"><a name="p552215442213"></a><a name="p552215442213"></a>IP address of the NFS client that can access the volume. This parameter is mandatory when the NFS protocol is used.</p>
<p id="p914297103211"><a name="p914297103211"></a><a name="p914297103211"></a>You can enter the client host name (a full domain name is recommended), client IP address, or client IP address segment.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637013765210"><a name="p1637013765210"></a><a name="p1637013765210"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p113981010185211"><a name="p113981010185211"></a><a name="p113981010185211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1145820621813"><a name="p1145820621813"></a><a name="p1145820621813"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p466615315578"><a name="p466615315578"></a><a name="p466615315578"></a>The asterisk (*) can be used to indicate any client. If you are not sure about the IP address of the access client, you are advised to use the asterisk (*) to prevent the client access from being rejected by the storage system.</p>
<p id="p164521752175617"><a name="p164521752175617"></a><a name="p164521752175617"></a>If the client host name is used, you are advised to use the full domain name.</p>
<p id="p20828214135714"><a name="p20828214135714"></a><a name="p20828214135714"></a>The IP addresses can be IPv4 addresses, IPv6 addresses, or a combination of IPv4 and IPv6 addresses.</p>
<p id="p208641555185710"><a name="p208641555185710"></a><a name="p208641555185710"></a>You can enter multiple host names, IP addresses, or IP address segments and separate them with semicolons (;). Example: <strong id="b1791131414223"><a name="b1791131414223"></a><a name="b1791131414223"></a>192.168.0.10;192.168.0.0/24;myserver1.test</strong></p>
</td>
</tr>
<tr id="row17122191413012"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p513251416380"><a name="p513251416380"></a><a name="p513251416380"></a>parameters.storageQuota</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p613221412389"><a name="p613221412389"></a><a name="p613221412389"></a>File system quota settings.</p>
<p id="p7371208112220"><a name="p7371208112220"></a><a name="p7371208112220"></a>The value of the parameter is JSON character strings in dictionary format. A character string is enclosed by single quotation marks and the dictionary key by double quotation marks. Example: <strong id="b12299131202918"><a name="b12299131202918"></a><a name="b12299131202918"></a>'{"spaceQuota": "softQuota", "gracePeriod": 100}'</strong></p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p73707715210"><a name="p73707715210"></a><a name="p73707715210"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p639812105526"><a name="p639812105526"></a><a name="p639812105526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1545816617183"><a name="p1545816617183"></a><a name="p1545816617183"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p21321014103814"><a name="p21321014103814"></a><a name="p21321014103814"></a>For details about the supported quota configurations, see <a href="#table2083974632312">Table 4</a>.</p>
</td>
</tr>
<tr id="row15478113119190"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p18478163131914"><a name="p18478163131914"></a><a name="p18478163131914"></a>parameters.qos</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15525175120211"><a name="p15525175120211"></a><a name="p15525175120211"></a>QoS settings of the file system on the storage side of the PV.</p>
<p id="p12218174732111"><a name="p12218174732111"></a><a name="p12218174732111"></a>The value of the parameter is JSON character strings in dictionary format. A character string is enclosed by single quotation marks and the dictionary key by double quotation marks. Example: <strong id="b1246522122814"><a name="b1246522122814"></a><a name="b1246522122814"></a>'{"maxMBPS": 999, "maxIOPS": 999}'</strong></p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p03704715211"><a name="p03704715211"></a><a name="p03704715211"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1439818100526"><a name="p1439818100526"></a><a name="p1439818100526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1245817618182"><a name="p1245817618182"></a><a name="p1245817618182"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p24789316192"><a name="p24789316192"></a><a name="p24789316192"></a>For details about the supported QoS configurations, see <a href="#table74841513116">Table 3</a>.</p>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>Permission on the directory mounted to a container.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p6458267189"><a name="p6458267189"></a><a name="p6458267189"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>For details about the configuration format, refer to the Linux permission settings, for example, 777 and 755.</p>
</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6718844173115"><a name="p6718844173115"></a><a name="p6718844173115"></a>parameters.rootSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p07183448314"><a name="p07183448314"></a><a name="p07183448314"></a>Controls the <strong id="b677565983115"><a name="b677565983115"></a><a name="b677565983115"></a>root</strong> permission of the client.</p>
<p id="p129442384148"><a name="p129442384148"></a><a name="p129442384148"></a>The value can be:</p>
<a name="ul124031949175810"></a><a name="ul124031949175810"></a><ul id="ul124031949175810"><li><strong id="b4742203910327"><a name="b4742203910327"></a><a name="b4742203910327"></a>root_squash</strong>: The client cannot access the storage system as user <strong id="b8742193953219"><a name="b8742193953219"></a><a name="b8742193953219"></a>root</strong>. If a client accesses the storage system as user <strong id="b1774216396326"><a name="b1774216396326"></a><a name="b1774216396326"></a>root</strong>, the client will be mapped as an anonymous user.</li><li><strong id="b1629216953320"><a name="b1629216953320"></a><a name="b1629216953320"></a>no_root_squash</strong>: A client can access the storage system as user <strong id="b1429279123310"><a name="b1429279123310"></a><a name="b1429279123310"></a>root</strong> and has the permission of user <strong id="b929320911332"><a name="b929320911332"></a><a name="b929320911332"></a>root</strong>.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p73701479521"><a name="p73701479521"></a><a name="p73701479521"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p13981710165217"><a name="p13981710165217"></a><a name="p13981710165217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p145819610185"><a name="p145819610185"></a><a name="p145819610185"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14519141410508"><a name="p14519141410508"></a><a name="p14519141410508"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p3644133462719"><a name="p3644133462719"></a><a name="p3644133462719"></a>Whether to retain the user ID (UID) and group ID (GID) of a shared directory.</p>
<p id="p19519161416501"><a name="p19519161416501"></a><a name="p19519161416501"></a>The value can be:</p>
<a name="ul14691584594"></a><a name="ul14691584594"></a><ul id="ul14691584594"><li><strong id="b1996694383314"><a name="b1996694383314"></a><a name="b1996694383314"></a>all_squash</strong>: The UID and GID of the shared directory are mapped to anonymous users.</li><li><strong id="b108734512335"><a name="b108734512335"></a><a name="b108734512335"></a>no_all_squash</strong>: The UID and GID of the shared directory are retained.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p163702712526"><a name="p163702712526"></a><a name="p163702712526"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p7398121045211"><a name="p7398121045211"></a><a name="p7398121045211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1345810617186"><a name="p1345810617186"></a><a name="p1345810617186"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row446717321624"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p204682321028"><a name="p204682321028"></a><a name="p204682321028"></a>parameters.snapshotDirectoryVisibility</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p124681932122"><a name="p124681932122"></a><a name="p124681932122"></a>Whether the snapshot directory is visible.</p>
<p id="p445010115419"><a name="p445010115419"></a><a name="p445010115419"></a>The value can be:</p>
<a name="ul129350148597"></a><a name="ul129350148597"></a><ul id="ul129350148597"><li><strong id="b2154143563513"><a name="b2154143563513"></a><a name="b2154143563513"></a>visible</strong>: The snapshot directory is visible.</li><li><strong id="b184508441358"><a name="b184508441358"></a><a name="b184508441358"></a>invisible</strong>: The snapshot directory is invisible.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p23707785219"><a name="p23707785219"></a><a name="p23707785219"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p14398210185219"><a name="p14398210185219"></a><a name="p14398210185219"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1045846111813"><a name="p1045846111813"></a><a name="p1045846111813"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a>parameters.disableVerifyCapacity</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1899222312222"><a name="p1899222312222"></a><a name="p1899222312222"></a>Whether to disable volume capacity verification. After this function is disabled, the system will not verify whether the volume capacity is an integer multiple of the sector size.</p>
<p id="p4236912172515"><a name="p4236912172515"></a><a name="p4236912172515"></a>The value can be:</p>
<a name="ul7370193012510"></a><a name="ul7370193012510"></a><ul id="ul7370193012510"><li>"true": disables volume capacity verification.</li><li>"false": enables volume capacity verification.</li></ul>
<div class="notice" id="note163681158114916"><a name="note163681158114916"></a><a name="note163681158114916"></a><span class="noticetitle"> NOTICE: </span><div class="noticebody"><p id="p6368158104913"><a name="p6368158104913"></a><a name="p6368158104913"></a>When Red Hat OpenShift Virtualization is used to connect to CSI, this parameter must be set to <strong id="b16328822111417"><a name="b16328822111417"></a><a name="b16328822111417"></a>true</strong>.</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p164589651813"><a name="p164589651813"></a><a name="p164589651813"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p332084914582"><a name="p332084914582"></a><a name="p332084914582"></a>For OceanStor Pacific NAS, the sector size is 1 KB.</p>
</td>
</tr>
</tbody>
</table>

**Table  2**  Common parameters in mountOptions

<a name="table65545557506"></a>
<table><thead align="left"><tr id="row1555414559506"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.1"><p id="p5274819155114"><a name="p5274819155114"></a><a name="p5274819155114"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.2"><p id="p19274619145114"><a name="p19274619145114"></a><a name="p19274619145114"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.3"><p id="p6274171905110"><a name="p6274171905110"></a><a name="p6274171905110"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.4"><p id="p13274419205110"><a name="p13274419205110"></a><a name="p13274419205110"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.5"><p id="p19274171912519"><a name="p19274171912519"></a><a name="p19274171912519"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row8555755185012"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p162853569513"><a name="p162853569513"></a><a name="p162853569513"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1928585612516"><a name="p1928585612516"></a><a name="p1928585612516"></a>NFS mount option on the host. The following mount option is supported:</p>
<p id="p328516567514"><a name="p328516567514"></a><a name="p328516567514"></a><strong id="b1829141763615"><a name="b1829141763615"></a><a name="b1829141763615"></a>nfsvers</strong>: protocol version for NFS mounting. The value can be <strong id="b1677134312360"><a name="b1677134312360"></a><a name="b1677134312360"></a>3</strong>, <strong id="b15848443362"><a name="b15848443362"></a><a name="b15848443362"></a>4</strong>, <strong id="b813154612361"><a name="b813154612361"></a><a name="b813154612361"></a>4.0</strong>, <strong id="b979851623714"><a name="b979851623714"></a><a name="b979851623714"></a>4.1</strong>, or <strong id="b10691247183619"><a name="b10691247183619"></a><a name="b10691247183619"></a>4.2</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p15285356185114"><a name="p15285356185114"></a><a name="p15285356185114"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p182851756145119"><a name="p182851756145119"></a><a name="p182851756145119"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p228545619510"><a name="p228545619510"></a><a name="p228545619510"></a>This parameter is optional after the <strong id="b17158349193611"><a name="b17158349193611"></a><a name="b17158349193611"></a>-o</strong> parameter when the <strong id="b19158549153613"><a name="b19158549153613"></a><a name="b19158549153613"></a>mount</strong> command is executed on the host. The value is in list format.</p>
<p id="p13285856115110"><a name="p13285856115110"></a><a name="p13285856115110"></a>If the NFS version is specified for mounting, NFS 3, 4.0, 4.1, and 4.2 protocols are supported (the protocol must be supported and enabled on storage devices). If <strong id="b733146143816"><a name="b733146143816"></a><a name="b733146143816"></a>nfsvers</strong> is set to <strong id="b143311693811"><a name="b143311693811"></a><a name="b143311693811"></a>4</strong>, the latest protocol version NFS 4 may be used for mounting due to different OS configurations, for example, 4.2. If the 4.0 protocol is required, you are advised to set <strong id="b7342612383"><a name="b7342612383"></a><a name="b7342612383"></a>nfsvers</strong> to <strong id="b15357673814"><a name="b15357673814"></a><a name="b15357673814"></a>4.0</strong>.</p>
</td>
</tr>
<tr id="row1142654125113"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p028615569516"><a name="p028615569516"></a><a name="p028615569516"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p328617569519"><a name="p328617569519"></a><a name="p328617569519"></a>Transmission protocol used for NFS mounting.</p>
<p id="p18286185612518"><a name="p18286185612518"></a><a name="p18286185612518"></a>The value can be <strong id="b11371339115410"><a name="b11371339115410"></a><a name="b11371339115410"></a>rdma</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p172868562511"><a name="p172868562511"></a><a name="p172868562511"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p1286155614517"><a name="p1286155614517"></a><a name="p1286155614517"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p647716526533"><a name="p647716526533"></a><a name="p647716526533"></a>This example applies to 8.2.0 or later.</p>
</td>
</tr>
<tr id="row16338113817517"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p6286105617518"><a name="p6286105617518"></a><a name="p6286105617518"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p628665645117"><a name="p628665645117"></a><a name="p628665645117"></a>Protocol port used for NFS mounting.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p192861056115114"><a name="p192861056115114"></a><a name="p192861056115114"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p628655665114"><a name="p628655665114"></a><a name="p628655665114"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p6286145618514"><a name="p6286145618514"></a><a name="p6286145618514"></a>If the transmission protocol is <strong id="b698755172717"><a name="b698755172717"></a><a name="b698755172717"></a>rdma</strong>, set this parameter to <strong id="b1080767142715"><a name="b1080767142715"></a><a name="b1080767142715"></a>20049</strong>.</p>
</td>
</tr>
<tr id="row697305614016"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p128525610511"><a name="p128525610511"></a><a name="p128525610511"></a>mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p112856566510"><a name="p112856566510"></a><a name="p112856566510"></a>The DPC namespace supports the ACL function. The DPC client supports POSIX ACL, NFSv4 ACL, and NT ACL authentication.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p228505620512"><a name="p228505620512"></a><a name="p228505620512"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p132852564514"><a name="p132852564514"></a><a name="p132852564514"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p428595635116"><a name="p428595635116"></a><a name="p428595635116"></a>The descriptions of <strong id="b6489173317352"><a name="b6489173317352"></a><a name="b6489173317352"></a>acl</strong>, <strong id="b148993333520"><a name="b148993333520"></a><a name="b148993333520"></a>aclonlyposix</strong>, <strong id="b16489173318359"><a name="b16489173318359"></a><a name="b16489173318359"></a>cnflush</strong>, and <strong id="b1048983333518"><a name="b1048983333518"></a><a name="b1048983333518"></a>cflush</strong> are for reference only. For details about the parameters, see <a href="https://support.huawei.com/enterprise/en/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">OceanStor Pacific Series Product Documentation</a> and choose <strong id="b19490183383510"><a name="b19490183383510"></a><a name="b19490183383510"></a>Configuration</strong> &gt; <strong id="b154901133133510"><a name="b154901133133510"></a><a name="b154901133133510"></a>Basic Service Configuration Guide for File</strong> &gt; <strong id="b16490123316354"><a name="b16490123316354"></a><a name="b16490123316354"></a>Configuring Basic Services (DPC Scenario)</strong> &gt; <strong id="b349011336355"><a name="b349011336355"></a><a name="b349011336355"></a>Accessing a DPC Share on a Client</strong> &gt; <strong id="b13490193320356"><a name="b13490193320356"></a><a name="b13490193320356"></a>Step 2</strong>.</p>
</td>
</tr>
<tr id="row1153312541506"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p528513563511"><a name="p528513563511"></a><a name="p528513563511"></a>mountOptions.aclonlyposix</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p328545655110"><a name="p328545655110"></a><a name="p328545655110"></a>The DPC namespace supports POSIX ACL, and the DPC client supports POSIX ACL authentication.</p>
<p id="p02851756105111"><a name="p02851756105111"></a><a name="p02851756105111"></a>The following protocols support POSIX ACL: DPC, NFSv3, and HDFS. If NFSv4 ACL or NT ACL is used, the DPC client cannot identify the ACL of this type. As a result, the ACL of this type does not take effect.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p1428575617514"><a name="p1428575617514"></a><a name="p1428575617514"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p3285056145120"><a name="p3285056145120"></a><a name="p3285056145120"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p192851156145118"><a name="p192851156145118"></a><a name="p192851156145118"></a>If <strong id="b4962121204015"><a name="b4962121204015"></a><a name="b4962121204015"></a>aclonlyposix</strong> and <strong id="b9962721104015"><a name="b9962721104015"></a><a name="b9962721104015"></a>acl</strong> are used together, only <strong id="b6963172144010"><a name="b6963172144010"></a><a name="b6963172144010"></a>acl</strong> takes effect. That is, the namespace supports the ACL function.</p>
</td>
</tr>
<tr id="row281161110"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1228513566515"><a name="p1228513566515"></a><a name="p1228513566515"></a>mountOptions.cnflush</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p52851756125115"><a name="p52851756125115"></a><a name="p52851756125115"></a>Asynchronous disk flushing mode. That is, data is not flushed to disks immediately when files in the namespace are closed.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p12854568514"><a name="p12854568514"></a><a name="p12854568514"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p9285956175117"><a name="p9285956175117"></a><a name="p9285956175117"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p228575614518"><a name="p228575614518"></a><a name="p228575614518"></a>Asynchronous flushing mode: When a file is closed, data in the cache is not flushed to storage media in synchronous mode. Instead, data is written from the cache to the storage media in asynchronous flushing mode. After the write service is complete, data is flushed from the cache to disks periodically based on the flushing period. In a multi-client scenario, if concurrent operations are performed on the same file, the file size update is affected by the disk flushing period. That is, the file size is updated only after the disk flushing is complete. Generally, the update is completed within several seconds. Synchronous I/Os are not affected by the disk flushing period.</p>
</td>
</tr>
<tr id="row177671317113"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p22851456185117"><a name="p22851456185117"></a><a name="p22851456185117"></a>mountOptions.cflush</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p18285656115120"><a name="p18285656115120"></a><a name="p18285656115120"></a>Synchronous disk flushing mode. That is, data is flushed to disks immediately when files in the namespace are closed.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p528515645111"><a name="p528515645111"></a><a name="p528515645111"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p528545655118"><a name="p528545655118"></a><a name="p528545655118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p8285185695115"><a name="p8285185695115"></a><a name="p8285185695115"></a>By default, the synchronous disk flushing mode is used.</p>
</td>
</tr>
</tbody>
</table>

**Table  3**  Supported QoS configurations

<a name="table74841513116"></a>
<table><thead align="left"><tr id="row74844518118"><th class="cellrowborder" valign="top" width="17.7%" id="mcps1.2.4.1.1"><p id="p1643904313015"><a name="p1643904313015"></a><a name="p1643904313015"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="30.17%" id="mcps1.2.4.1.2"><p id="p164391543143020"><a name="p164391543143020"></a><a name="p164391543143020"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="52.129999999999995%" id="mcps1.2.4.1.3"><p id="p34393439301"><a name="p34393439301"></a><a name="p34393439301"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row3455115971517"><td class="cellrowborder" valign="top" width="17.7%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0273440106_p743994313307"><a name="en-us_topic_0273440106_p743994313307"></a><a name="en-us_topic_0273440106_p743994313307"></a>maxMBPS</p>
</td>
<td class="cellrowborder" valign="top" width="30.17%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0273440106_p7439243173012"><a name="en-us_topic_0273440106_p7439243173012"></a><a name="en-us_topic_0273440106_p7439243173012"></a>Maximum bandwidth. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" width="52.129999999999995%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0273440106_p184391143133017"><a name="en-us_topic_0273440106_p184391143133017"></a><a name="en-us_topic_0273440106_p184391143133017"></a>This parameter is mandatory. The value is an integer greater than 0, expressed in MB/s. For details about the maximum value, see the actual limit of the storage device. For example, the maximum value of OceanStor Pacific NAS is 1073741824.</p>
</td>
</tr>
<tr id="row545565991517"><td class="cellrowborder" valign="top" width="17.7%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0273440106_p184399439309"><a name="en-us_topic_0273440106_p184399439309"></a><a name="en-us_topic_0273440106_p184399439309"></a>maxIOPS</p>
</td>
<td class="cellrowborder" valign="top" width="30.17%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0273440106_p1943913439308"><a name="en-us_topic_0273440106_p1943913439308"></a><a name="en-us_topic_0273440106_p1943913439308"></a>Maximum IOPS. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" width="52.129999999999995%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0273440106_p14439114315304"><a name="en-us_topic_0273440106_p14439114315304"></a><a name="en-us_topic_0273440106_p14439114315304"></a>This parameter is mandatory. The value is an integer greater than 0. For details about the maximum value, see the actual limit of the storage device. For example, the maximum value of OceanStor Pacific NAS is 1073741824000.</p>
</td>
</tr>
</tbody>
</table>

**Table  4**  Supported quota configurations

<a name="table2083974632312"></a>
<table><thead align="left"><tr id="row68394463230"><th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.1"><p id="en-us_topic_0000001218368853_p1643904313015"><a name="en-us_topic_0000001218368853_p1643904313015"></a><a name="en-us_topic_0000001218368853_p1643904313015"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.2"><p id="en-us_topic_0000001218368853_p164391543143020"><a name="en-us_topic_0000001218368853_p164391543143020"></a><a name="en-us_topic_0000001218368853_p164391543143020"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.2.4.1.3"><p id="en-us_topic_0000001218368853_p34393439301"><a name="en-us_topic_0000001218368853_p34393439301"></a><a name="en-us_topic_0000001218368853_p34393439301"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row58391646142313"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001218368853_p10540642195814"><a name="en-us_topic_0000001218368853_p10540642195814"></a><a name="en-us_topic_0000001218368853_p10540642195814"></a>spaceQuota</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001218368853_p7439243173012"><a name="en-us_topic_0000001218368853_p7439243173012"></a><a name="en-us_topic_0000001218368853_p7439243173012"></a>File quota type.</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001218368853_p184391143133017"><a name="en-us_topic_0000001218368853_p184391143133017"></a><a name="en-us_topic_0000001218368853_p184391143133017"></a>This parameter is mandatory. Only <span class="parmvalue" id="parmvalue1275164274510"><a name="parmvalue1275164274510"></a><a name="parmvalue1275164274510"></a><b>softQuota</b></span> or <span class="parmvalue" id="parmvalue19751142154517"><a name="parmvalue19751142154517"></a><a name="parmvalue19751142154517"></a><b>hardQuota</b></span> can be configured.</p>
</td>
</tr>
<tr id="row13839124642310"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001218368853_p184399439309"><a name="en-us_topic_0000001218368853_p184399439309"></a><a name="en-us_topic_0000001218368853_p184399439309"></a>gracePeriod</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001218368853_p1943913439308"><a name="en-us_topic_0000001218368853_p1943913439308"></a><a name="en-us_topic_0000001218368853_p1943913439308"></a>Grace period allowed when the soft quota is configured.</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001218368853_p1540512282024"><a name="en-us_topic_0000001218368853_p1540512282024"></a><a name="en-us_topic_0000001218368853_p1540512282024"></a>This parameter is conditionally optional only when <span class="parmname" id="parmname682317528456"><a name="parmname682317528456"></a><a name="parmname682317528456"></a><b>spaceQuota</b></span> is set to <span class="parmvalue" id="parmvalue68238521459"><a name="parmvalue68238521459"></a><a name="parmvalue68238521459"></a><b>softQuota</b></span>.</p>
<p id="en-us_topic_0000001218368853_p14439114315304"><a name="en-us_topic_0000001218368853_p14439114315304"></a><a name="en-us_topic_0000001218368853_p14439114315304"></a>The value is an integer ranging from 0 to 4294967294.</p>
</td>
</tr>
</tbody>
</table>

