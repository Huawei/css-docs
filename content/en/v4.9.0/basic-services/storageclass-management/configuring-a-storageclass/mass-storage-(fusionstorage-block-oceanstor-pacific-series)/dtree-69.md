---
title: "Dtree"
linkTitle: "Dtree"
description: 
weight: 2
---

## Creating a StorageClass{#section1448412281571}

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

## Example of StorageClass Configuration Supported by the NFS Protocol{#section1053116812255}

When a container uses the NFS protocol to connect to dtree resources, refer to the following StorageClass configuration example. In this example, NFS version 4.1 is specified for mounting.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dtree-181
  parentname: parent-filesystem-name
  volumeType: dtree
  allocType: thin
  authClient: "*"
mountOptions:
  - nfsvers=4.1 # Specify the version 4.1 for NFS mounting.
```

## Example of StorageClass Configuration Supported by the DPC Protocol{#section36031677149}

When a container uses the DPC protocol to connect to dtree resources, refer to the following StorageClass configuration example. In this example,  **acl**  is used as the authentication parameter for mounting, and  **cnflush**  is used to set the asynchronous disk flushing mode.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dtree-181
  parentname: parent-filesystem-name
  volumeType: dtree
  allocType: thin
  authClient: "*"
mountOptions:
  - acl # Set the authentication parameter.
  - cnflush # Set the asynchronous disk flushing mode.
```

## StorageClass Parameters Supported by Dtrees{#section1758842912252}

**Table  1**  StorageClass configuration parameters

<a name="en-us_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="en-us_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="20.43%" id="mcps1.2.6.1.1"><p id="en-us_topic_0000001162111564_p875071122919"><a name="en-us_topic_0000001162111564_p875071122919"></a><a name="en-us_topic_0000001162111564_p875071122919"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="25.52%" id="mcps1.2.6.1.2"><p id="en-us_topic_0000001162111564_p17750131113295"><a name="en-us_topic_0000001162111564_p17750131113295"></a><a name="en-us_topic_0000001162111564_p17750131113295"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="5.18%" id="mcps1.2.6.1.3"><p id="p10370187155216"><a name="p10370187155216"></a><a name="p10370187155216"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="9.34%" id="mcps1.2.6.1.4"><p id="p1639801013525"><a name="p1639801013525"></a><a name="p1639801013525"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="39.53%" id="mcps1.2.6.1.5"><p id="en-us_topic_0000001162111564_p075011113295"><a name="en-us_topic_0000001162111564_p075011113295"></a><a name="en-us_topic_0000001162111564_p075011113295"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p4750141111292"><a name="en-us_topic_0000001162111564_p4750141111292"></a><a name="en-us_topic_0000001162111564_p4750141111292"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p475091120296"><a name="en-us_topic_0000001162111564_p475091120296"></a><a name="en-us_topic_0000001162111564_p475091120296"></a>User-defined name of a StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p037012725218"><a name="p037012725218"></a><a name="p037012725218"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1539814102527"><a name="p1539814102527"></a><a name="p1539814102527"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001162111564_p861713973915"><a name="en-us_topic_0000001162111564_p861713973915"></a><a name="en-us_topic_0000001162111564_p861713973915"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p8750161119299"><a name="en-us_topic_0000001162111564_p8750161119299"></a><a name="en-us_topic_0000001162111564_p8750161119299"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p15750201119295"><a name="en-us_topic_0000001162111564_p15750201119295"></a><a name="en-us_topic_0000001162111564_p15750201119295"></a>Name of the provisioner.</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p437013755212"><a name="p437013755212"></a><a name="p437013755212"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p2039881018524"><a name="p2039881018524"></a><a name="p2039881018524"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>Set this parameter to the driver name set during Huawei CSI installation.</p>
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>The value is the same as that of <strong id="b1223814278013"><a name="b1223814278013"></a><a name="b1223814278013"></a>driverName</strong> in the <strong id="b1649220321700"><a name="b1649220321700"></a><a name="b1649220321700"></a>values.yaml</strong> file.</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p119108535312"><a name="p119108535312"></a><a name="p119108535312"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p16910135393118"><a name="p16910135393118"></a><a name="p16910135393118"></a>Reclamation policy. The following types are supported:</p>
<a name="ul5209917195517"></a><a name="ul5209917195517"></a><ul id="ul5209917195517"><li><strong id="b39881432511"><a name="b39881432511"></a><a name="b39881432511"></a>Delete</strong>: Resources are automatically reclaimed.</li><li><strong id="b15829858448"><a name="b15829858448"></a><a name="b15829858448"></a>Retain</strong>: Resources are manually reclaimed.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p4370073521"><a name="p4370073521"></a><a name="p4370073521"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p139811010528"><a name="p139811010528"></a><a name="p139811010528"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li><strong id="b48131861150"><a name="b48131861150"></a><a name="b48131861150"></a>Delete</strong>: When a PV/PVC is deleted, resources on the storage device are also deleted.</li><li><strong id="b52391026851"><a name="b52391026851"></a><a name="b52391026851"></a>Retain</strong>: When a PV/PVC is deleted, resources on the storage device are not deleted.</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p192771821155012"><a name="p192771821155012"></a><a name="p192771821155012"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p8277132112501"><a name="p8277132112501"></a><a name="p8277132112501"></a>Whether to allow volume expansion. If this parameter is set to <strong id="b494616718617"><a name="b494616718617"></a><a name="b494616718617"></a>true</strong>, the capacity of the PV that uses the StorageClass can be expanded.</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1637010715210"><a name="p1637010715210"></a><a name="p1637010715210"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p20398110155213"><a name="p20398110155213"></a><a name="p20398110155213"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p13923171118495"><a name="p13923171118495"></a><a name="p13923171118495"></a>This function can only be used to expand PV capacity but cannot be used to reduce PV capacity.</p>
</td>
</tr>
<tr id="row63343268297"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p13432132752911"><a name="p13432132752911"></a><a name="p13432132752911"></a>mountOptions</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p134321427192916"><a name="p134321427192916"></a><a name="p134321427192916"></a>List of mount parameters, which can be used to specify the parameters of the <strong id="b938691915113"><a name="b938691915113"></a><a name="b938691915113"></a>-o</strong> option when the <strong id="b1420143218111"><a name="b1420143218111"></a><a name="b1420143218111"></a>mount</strong> command is executed on a host.</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p2432227172910"><a name="p2432227172910"></a><a name="p2432227172910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p1432112762919"><a name="p1432112762919"></a><a name="p1432112762919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p15432162772912"><a name="p15432162772912"></a><a name="p15432162772912"></a>For details about common parameters in <strong id="b1945445410117"><a name="b1945445410117"></a><a name="b1945445410117"></a>mountOptions</strong>, see <a href="#table65545557506">Table 2</a>.</p>
<p id="p104322027152920"><a name="p104322027152920"></a><a name="p104322027152920"></a>You can also specify other mount parameters.</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>Name of the backend where the resource to be created is located.</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>If this parameter is not set, Huawei CSI will randomly select a backend that meets the capacity requirements to create resources.</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>You are advised to specify a backend to ensure that the created resource is located on the expected backend.</p>
<p id="p1746961523912"><a name="p1746961523912"></a><a name="p1746961523912"></a>This parameter is mandatory if <strong id="b51351758122218"><a name="b51351758122218"></a><a name="b51351758122218"></a>parameters.parentname</strong> is set.</p>
</td>
</tr>
<tr id="row9425191220356"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p122751558184511"><a name="p122751558184511"></a><a name="p122751558184511"></a>parameters.parentname</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p327525817451"><a name="p327525817451"></a><a name="p327525817451"></a>Name of a file system on the current storage device. Dtree is created in the file system.</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p8275125812453"><a name="p8275125812453"></a><a name="p8275125812453"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p327535812450"><a name="p327535812450"></a><a name="p327535812450"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p16731411944"><a name="p16731411944"></a><a name="p16731411944"></a>This parameter is mandatory when <strong id="b11122202217235"><a name="b11122202217235"></a><a name="b11122202217235"></a>parentname</strong> is not set for the backend.</p>
<p id="p122751358134518"><a name="p122751358134518"></a><a name="p122751358134518"></a>If <strong id="b136911940182319"><a name="b136911940182319"></a><a name="b136911940182319"></a>parentname</strong> is configured only in the StorageClass but not configured in the storage backend, set <strong id="b1569111401234"><a name="b1569111401234"></a><a name="b1569111401234"></a>CSIDriverObject.attachRequired</strong> to <strong id="b10691114019236"><a name="b10691114019236"></a><a name="b10691114019236"></a>true</strong> during CSI installation.</p>
</td>
</tr>
<tr id="row12968565337"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p19968166163320"><a name="p19968166163320"></a><a name="p19968166163320"></a>parameters.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p270mcpsimp"><a name="p270mcpsimp"></a><a name="p270mcpsimp"></a>Name of the storage resource created by dynamic volume provisioning.</p>
<p id="p271mcpsimp"><a name="p271mcpsimp"></a><a name="p271mcpsimp"></a>You can configure a placeholder to customize the storage resource name. The following placeholders are supported:</p>
<a name="ul277mcpsimp"></a><a name="ul277mcpsimp"></a><ul id="ul277mcpsimp"><li>PVC namespace: {{ .PVCNamespace }}</li><li>PVC name: {{ .PVCName }}</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p49687693314"><a name="p49687693314"></a><a name="p49687693314"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p096819643312"><a name="p096819643312"></a><a name="p096819643312"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><a name="ul165061538173414"></a><a name="ul165061538173414"></a><ul id="ul165061538173414"><li>The value can contain letters, digits, hyphens (-), underscores (_), and periods (.). It cannot be left empty. The length of the expanded placeholder ranges from 1 to 255 characters.</li><li>Both the PVC namespace and PVC name must be configured.</li><li>To avoid duplicate resource names, the PVC UID is added to the end of the name as a unique identifier by default.</li></ul>
<p id="p3486174714359"><a name="p3486174714359"></a><a name="p3486174714359"></a></p>
<p id="p292mcpsimp"><a name="p292mcpsimp"></a><a name="p292mcpsimp"></a>Configuration example:</p>
<p id="p293mcpsimp"><a name="p293mcpsimp"></a><a name="p293mcpsimp"></a>PVC namespace: <strong id="b17463154211711"><a name="b17463154211711"></a><a name="b17463154211711"></a>namespace</strong>. PVC name: <strong id="b723125051719"><a name="b723125051719"></a><a name="b723125051719"></a>pvc-1</strong>. PVC UID: <strong id="b1858945412171"><a name="b1858945412171"></a><a name="b1858945412171"></a>c2fd3f46-bf17-4a7d-b88e-2e3232bae434</strong>.</p>
<p id="p301mcpsimp"><a name="p301mcpsimp"></a><a name="p301mcpsimp"></a><strong id="b4947105911719"><a name="b4947105911719"></a><a name="b4947105911719"></a>volumeName</strong> is set to <strong id="b87210186180"><a name="b87210186180"></a><a name="b87210186180"></a>prefix-{{ .PVCNamespace }}_{{ .PVCName }}</strong>.</p>
<p id="p302mcpsimp"><a name="p302mcpsimp"></a><a name="p302mcpsimp"></a>The ultimate storage resource name is <strong id="b52901641111819"><a name="b52901641111819"></a><a name="b52901641111819"></a>prefix-namespace_pvc-1-c2fd3f46bf174a7db88e2e3232bae434</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001162111564_p1775061119292"><a name="en-us_topic_0000001162111564_p1775061119292"></a><a name="en-us_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001162111564_p975011122920"><a name="en-us_topic_0000001162111564_p975011122920"></a><a name="en-us_topic_0000001162111564_p975011122920"></a>Type of the volume to be created. The following types are supported:</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li><strong id="b1733717591123"><a name="b1733717591123"></a><a name="b1733717591123"></a>lun</strong>: A LUN is provisioned on the storage side.</li><li><strong id="b10216124101312"><a name="b10216124101312"></a><a name="b10216124101312"></a>fs</strong>: A file system is provisioned on the storage side.</li><li><strong id="b1412435781313"><a name="b1412435781313"></a><a name="b1412435781313"></a>dtree</strong>: A volume of the Dtree type is provisioned on the storage side.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p159151023181412"><a name="p159151023181412"></a><a name="p159151023181412"></a>When dtree is used, the value must be <strong id="b87721949162317"><a name="b87721949162317"></a><a name="b87721949162317"></a>dtree</strong>.</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p499022713590"><a name="p499022713590"></a><a name="p499022713590"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p552215442213"><a name="p552215442213"></a><a name="p552215442213"></a>IP address of the NFS client that can access the volume.</p>
<p id="p914297103211"><a name="p914297103211"></a><a name="p914297103211"></a>You can enter the client host name (a full domain name is recommended), client IP address, or client IP address segment.</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p1637013765210"><a name="p1637013765210"></a><a name="p1637013765210"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p113981010185211"><a name="p113981010185211"></a><a name="p113981010185211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p466615315578"><a name="p466615315578"></a><a name="p466615315578"></a>The asterisk (*) can be used to indicate any client. If you are not sure about the IP address of the access client, you are advised to use the asterisk (*) to prevent the client access from being rejected by the storage system.</p>
<p id="p164521752175617"><a name="p164521752175617"></a><a name="p164521752175617"></a>If the client host name is used, you are advised to use the full domain name.</p>
<p id="p20828214135714"><a name="p20828214135714"></a><a name="p20828214135714"></a>The IP addresses can be IPv4 addresses, IPv6 addresses, or a combination of IPv4 and IPv6 addresses.</p>
<p id="p208641555185710"><a name="p208641555185710"></a><a name="p208641555185710"></a>You can enter multiple host names, IP addresses, or IP address segments and separate them with semicolons (;). Example: <strong id="b1791131414223"><a name="b1791131414223"></a><a name="b1791131414223"></a>192.168.0.10;192.168.0.0/24;myserver1.test</strong></p>
</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p6909540133118"><a name="p6909540133118"></a><a name="p6909540133118"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p5909540143115"><a name="p5909540143115"></a><a name="p5909540143115"></a>Permission on the directory mounted to a container.</p>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p19370877528"><a name="p19370877528"></a><a name="p19370877528"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p173981610175210"><a name="p173981610175210"></a><a name="p173981610175210"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>For details about the configuration format, refer to the Linux permission settings, for example, 777 and 755.</p>
</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p6718844173115"><a name="p6718844173115"></a><a name="p6718844173115"></a>parameters.rootSquash</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p07183448314"><a name="p07183448314"></a><a name="p07183448314"></a>Controls the <strong id="b677565983115"><a name="b677565983115"></a><a name="b677565983115"></a>root</strong> permission of the client.</p>
<p id="p129442384148"><a name="p129442384148"></a><a name="p129442384148"></a>The value can be:</p>
<a name="ul124031949175810"></a><a name="ul124031949175810"></a><ul id="ul124031949175810"><li><strong id="b4742203910327"><a name="b4742203910327"></a><a name="b4742203910327"></a>root_squash</strong>: The client cannot access the storage system as user <strong id="b8742193953219"><a name="b8742193953219"></a><a name="b8742193953219"></a>root</strong>. If a client accesses the storage system as user <strong id="b1774216396326"><a name="b1774216396326"></a><a name="b1774216396326"></a>root</strong>, the client will be mapped as an anonymous user.</li><li><strong id="b1629216953320"><a name="b1629216953320"></a><a name="b1629216953320"></a>no_root_squash</strong>: A client can access the storage system as user <strong id="b1429279123310"><a name="b1429279123310"></a><a name="b1429279123310"></a>root</strong> and has the permission of user <strong id="b929320911332"><a name="b929320911332"></a><a name="b929320911332"></a>root</strong>.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p73701479521"><a name="p73701479521"></a><a name="p73701479521"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p13981710165217"><a name="p13981710165217"></a><a name="p13981710165217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p14519141410508"><a name="p14519141410508"></a><a name="p14519141410508"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p3644133462719"><a name="p3644133462719"></a><a name="p3644133462719"></a>Whether to retain the user ID (UID) and group ID (GID) of a shared directory.</p>
<p id="p19519161416501"><a name="p19519161416501"></a><a name="p19519161416501"></a>The value can be:</p>
<a name="ul14691584594"></a><a name="ul14691584594"></a><ul id="ul14691584594"><li><strong id="b1996694383314"><a name="b1996694383314"></a><a name="b1996694383314"></a>all_squash</strong>: The UID and GID of the shared directory are mapped to anonymous users.</li><li><strong id="b108734512335"><a name="b108734512335"></a><a name="b108734512335"></a>no_all_squash</strong>: The UID and GID of the shared directory are retained.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p163702712526"><a name="p163702712526"></a><a name="p163702712526"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p7398121045211"><a name="p7398121045211"></a><a name="p7398121045211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="20.43%" headers="mcps1.2.6.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a>parameters.disableVerifyCapacity</p>
</td>
<td class="cellrowborder" valign="top" width="25.52%" headers="mcps1.2.6.1.2 "><p id="p1899222312222"><a name="p1899222312222"></a><a name="p1899222312222"></a>Whether to disable volume capacity verification. After this function is disabled, the system will not verify whether the volume capacity is an integer multiple of the sector size.</p>
<p id="p4236912172515"><a name="p4236912172515"></a><a name="p4236912172515"></a>The value can be:</p>
<a name="ul7370193012510"></a><a name="ul7370193012510"></a><ul id="ul7370193012510"><li>"true": disables volume capacity verification.</li><li>"false": enables volume capacity verification.</li></ul>
<div class="notice" id="note163681158114916"><a name="note163681158114916"></a><a name="note163681158114916"></a><span class="noticetitle"> NOTICE: </span><div class="noticebody"><p id="p6368158104913"><a name="p6368158104913"></a><a name="p6368158104913"></a>When Red Hat OpenShift Virtualization is used to connect to CSI, this parameter must be set to <strong id="b127232182416"><a name="b127232182416"></a><a name="b127232182416"></a>true</strong>.</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="5.18%" headers="mcps1.2.6.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="9.34%" headers="mcps1.2.6.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="39.53%" headers="mcps1.2.6.1.5 "><p id="p52910516599"><a name="p52910516599"></a><a name="p52910516599"></a>For OceanStor Pacific dtrees, the sector size is 1 byte.</p>
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
<tbody><tr id="row19991425459"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p79442518513"><a name="p79442518513"></a><a name="p79442518513"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p29482515513"><a name="p29482515513"></a><a name="p29482515513"></a>NFS mount option on the host. The following mount option is supported:</p>
<p id="p494142514512"><a name="p494142514512"></a><a name="p494142514512"></a><strong id="b1829141763615"><a name="b1829141763615"></a><a name="b1829141763615"></a>nfsvers</strong>: protocol version for NFS mounting. The value can be <strong id="b1677134312360"><a name="b1677134312360"></a><a name="b1677134312360"></a>3</strong>, <strong id="b15848443362"><a name="b15848443362"></a><a name="b15848443362"></a>4</strong>, <strong id="b813154612361"><a name="b813154612361"></a><a name="b813154612361"></a>4.0</strong>, <strong id="b979851623714"><a name="b979851623714"></a><a name="b979851623714"></a>4.1</strong>, or <strong id="b10691247183619"><a name="b10691247183619"></a><a name="b10691247183619"></a>4.2</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p0941251358"><a name="p0941251358"></a><a name="p0941251358"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p149413259515"><a name="p149413259515"></a><a name="p149413259515"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p09415251518"><a name="p09415251518"></a><a name="p09415251518"></a>This parameter is optional after the <strong id="b17158349193611"><a name="b17158349193611"></a><a name="b17158349193611"></a>-o</strong> parameter when the <strong id="b19158549153613"><a name="b19158549153613"></a><a name="b19158549153613"></a>mount</strong> command is executed on the host. The value is in list format.</p>
<p id="p1094162515515"><a name="p1094162515515"></a><a name="p1094162515515"></a>If the NFS version is specified for mounting, NFS 3, 4.0, 4.1, and 4.2 protocols are supported (the protocol must be supported and enabled on storage devices). If <strong id="b733146143816"><a name="b733146143816"></a><a name="b733146143816"></a>nfsvers</strong> is set to <strong id="b143311693811"><a name="b143311693811"></a><a name="b143311693811"></a>4</strong>, the latest protocol version NFS 4 may be used for mounting due to different OS configurations, for example, 4.2. If the 4.0 protocol is required, you are advised to set <strong id="b7342612383"><a name="b7342612383"></a><a name="b7342612383"></a>nfsvers</strong> to <strong id="b15357673814"><a name="b15357673814"></a><a name="b15357673814"></a>4.0</strong>.</p>
</td>
</tr>
<tr id="row189910251055"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p139422511517"><a name="p139422511517"></a><a name="p139422511517"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p19417251455"><a name="p19417251455"></a><a name="p19417251455"></a>Transmission protocol used for NFS mounting.</p>
<p id="p8942255515"><a name="p8942255515"></a><a name="p8942255515"></a>The value can be <strong id="b11371339115410"><a name="b11371339115410"></a><a name="b11371339115410"></a>rdma</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p17945251752"><a name="p17945251752"></a><a name="p17945251752"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p994192515510"><a name="p994192515510"></a><a name="p994192515510"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p647716526533"><a name="p647716526533"></a><a name="p647716526533"></a>This parameter is supported by 8.2.0 or later.</p>
</td>
</tr>
<tr id="row16992251759"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p294162514515"><a name="p294162514515"></a><a name="p294162514515"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1194825554"><a name="p1194825554"></a><a name="p1194825554"></a>Protocol port used for NFS mounting.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p29422515511"><a name="p29422515511"></a><a name="p29422515511"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p1943251350"><a name="p1943251350"></a><a name="p1943251350"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p169452512514"><a name="p169452512514"></a><a name="p169452512514"></a>If the transmission protocol is <strong id="b698755172717"><a name="b698755172717"></a><a name="b698755172717"></a>rdma</strong>, set this parameter to <strong id="b1080767142715"><a name="b1080767142715"></a><a name="b1080767142715"></a>20049</strong>.</p>
</td>
</tr>
<tr id="row189915251856"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p128525610511"><a name="p128525610511"></a><a name="p128525610511"></a>mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p112856566510"><a name="p112856566510"></a><a name="p112856566510"></a>The DPC namespace supports the ACL function. The DPC client supports POSIX ACL, NFSv4 ACL, and NT ACL authentication.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p228505620512"><a name="p228505620512"></a><a name="p228505620512"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p132852564514"><a name="p132852564514"></a><a name="p132852564514"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p428595635116"><a name="p428595635116"></a><a name="p428595635116"></a>The descriptions of <strong id="b1566386735377"><a name="b1566386735377"></a><a name="b1566386735377"></a>acl</strong>, <strong id="b12515078875377"><a name="b12515078875377"></a><a name="b12515078875377"></a>aclonlyposix</strong>, <strong id="b17775723375377"><a name="b17775723375377"></a><a name="b17775723375377"></a>cnflush</strong>, and <strong id="b18043076685377"><a name="b18043076685377"></a><a name="b18043076685377"></a>cflush</strong> are for reference only. For details about the parameters, see <a href="https://support.huawei.com/enterprise/en/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">OceanStor Pacific Series Product Documentation</a> and choose <strong id="b15339881055377"><a name="b15339881055377"></a><a name="b15339881055377"></a>Configuration</strong> &gt; <strong id="b7743722285377"><a name="b7743722285377"></a><a name="b7743722285377"></a>Basic Service Configuration Guide for File</strong> &gt; <strong id="b4276346165377"><a name="b4276346165377"></a><a name="b4276346165377"></a>Configuring Basic Services (DPC Scenario)</strong> &gt; <strong id="b5048539545377"><a name="b5048539545377"></a><a name="b5048539545377"></a>Accessing a DPC Share on a Client</strong> &gt; <strong id="b8680175485377"><a name="b8680175485377"></a><a name="b8680175485377"></a>Step 2</strong>.</p>
</td>
</tr>
<tr id="row3999259515"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p528513563511"><a name="p528513563511"></a><a name="p528513563511"></a>mountOptions.aclonlyposix</p>
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
<tr id="row1699525654"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p1228513566515"><a name="p1228513566515"></a><a name="p1228513566515"></a>mountOptions.cnflush</p>
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
<tr id="row139942518518"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p22851456185117"><a name="p22851456185117"></a><a name="p22851456185117"></a>mountOptions.cflush</p>
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

