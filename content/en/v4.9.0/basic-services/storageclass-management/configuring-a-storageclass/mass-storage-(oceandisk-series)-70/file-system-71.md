---
title: "File System"
linkTitle: "File System"
description: 
weight: 1
---

## Creating a StorageClass{#section15343162123719}

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

When a container uses the NFS protocol to connect to file system resources, refer to the following StorageClass configuration example. In this example, NFS version 4.0 is specified for mounting.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-nas-181
  pool: StoragePool001
  volumeType: fs
  allocType: thin
  authClient: "*"
mountOptions:
  - nfsvers=4.0 # Specify the version 4.0 for NFS mounting.
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
<th class="cellrowborder" valign="top" width="7.191077194012327%" id="mcps1.2.7.1.5"><p id="p1113325565918"><a name="p1113325565918"></a><a name="p1113325565918"></a>Whether the Volume Management Takes Effect</p>
</th>
<th class="cellrowborder" valign="top" width="35.93581841307113%" id="mcps1.2.7.1.6"><p id="en-us_topic_0000001162111564_p075011113295"><a name="en-us_topic_0000001162111564_p075011113295"></a><a name="en-us_topic_0000001162111564_p075011113295"></a>Remarks</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p16133655135913"><a name="p16133655135913"></a><a name="p16133655135913"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p861713973915"><a name="en-us_topic_0000001162111564_p861713973915"></a><a name="en-us_topic_0000001162111564_p861713973915"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p0133955185920"><a name="p0133955185920"></a><a name="p0133955185920"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p848811314350"><a name="p848811314350"></a><a name="p848811314350"></a>Set this parameter to the driver name set during Huawei CSI installation.</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p11332055125915"><a name="p11332055125915"></a><a name="p11332055125915"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><a name="ul94333519558"></a><a name="ul94333519558"></a><ul id="ul94333519558"><li><strong id="b48131861150"><a name="b48131861150"></a><a name="b48131861150"></a>Delete</strong>: When a PV/PVC is deleted, resources on the storage device are also deleted.</li><li><strong id="b52391026851"><a name="b52391026851"></a><a name="b52391026851"></a>Retain</strong>: When a PV/PVC is deleted, resources on the storage device are not deleted.</li></ul>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p1613325519595"><a name="p1613325519595"></a><a name="p1613325519595"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p13923171118495"><a name="p13923171118495"></a><a name="p13923171118495"></a>This function can only be used to expand PV capacity but cannot be used to reduce PV capacity.</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p1613355555915"><a name="p1613355555915"></a><a name="p1613355555915"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p15432162772912"><a name="p15432162772912"></a><a name="p15432162772912"></a>For details about common parameters in <strong id="b1945445410117"><a name="b1945445410117"></a><a name="b1945445410117"></a>mountOptions</strong>, see <a href="#table65545557506">Table 2</a>.</p>
<p id="p104322027152920"><a name="p104322027152920"></a><a name="p104322027152920"></a>You can also specify other mount parameters.</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>Name of the backend where the resource to be created is located. This field must be set if <strong id="b7586115993016"><a name="b7586115993016"></a><a name="b7586115993016"></a>parameters.pool</strong> is set.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p413315519590"><a name="p413315519590"></a><a name="p413315519590"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>If this parameter is not set, Huawei CSI will randomly select a backend that meets the capacity requirements to create resources.</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p91331855155916"><a name="p91331855155916"></a><a name="p91331855155916"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p99571317978"><a name="p99571317978"></a><a name="p99571317978"></a>If this parameter is not set, Huawei CSI will randomly select a storage pool that meets the capacity requirements from the selected backend to create resources. You are advised to specify a storage pool to ensure that the created resource is located in the expected storage pool.</p>
</td>
</tr>
<tr id="row12968565337"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p19968166163320"><a name="p19968166163320"></a><a name="p19968166163320"></a>parameters.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p270mcpsimp"><a name="p270mcpsimp"></a><a name="p270mcpsimp"></a>Name of the storage resource created by dynamic volume provisioning.</p>
<p id="p271mcpsimp"><a name="p271mcpsimp"></a><a name="p271mcpsimp"></a>You can configure a placeholder to customize the storage resource name. The following placeholders are supported:</p>
<a name="ul277mcpsimp"></a><a name="ul277mcpsimp"></a><ul id="ul277mcpsimp"><li>PVC namespace: {{ .PVCNamespace }}</li><li>PVC name: {{ .PVCName }}</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p49687693314"><a name="p49687693314"></a><a name="p49687693314"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p096819643312"><a name="p096819643312"></a><a name="p096819643312"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p0133205515597"><a name="p0133205515597"></a><a name="p0133205515597"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><a name="ul165061538173414"></a><a name="ul165061538173414"></a><ul id="ul165061538173414"><li>The value can contain letters, digits, hyphens (-), underscores (_), and periods (.). It cannot be left empty. The length of the expanded placeholder ranges from 1 to 255 characters.</li><li>Both the PVC namespace and PVC name must be configured.</li><li>To avoid duplicate resource names, the PVC UID is added to the end of the name as a unique identifier by default.</li></ul>
<p id="p3486174714359"><a name="p3486174714359"></a><a name="p3486174714359"></a></p>
<p id="p292mcpsimp"><a name="p292mcpsimp"></a><a name="p292mcpsimp"></a>Configuration example:</p>
<p id="p293mcpsimp"><a name="p293mcpsimp"></a><a name="p293mcpsimp"></a>PVC namespace: <strong id="b17463154211711"><a name="b17463154211711"></a><a name="b17463154211711"></a>namespace</strong>. PVC name: <strong id="b723125051719"><a name="b723125051719"></a><a name="b723125051719"></a>pvc-1</strong>. PVC UID: <strong id="b1858945412171"><a name="b1858945412171"></a><a name="b1858945412171"></a>c2fd3f46-bf17-4a7d-b88e-2e3232bae434</strong>.</p>
<p id="p301mcpsimp"><a name="p301mcpsimp"></a><a name="p301mcpsimp"></a><strong id="b4947105911719"><a name="b4947105911719"></a><a name="b4947105911719"></a>volumeName</strong> is set to <strong id="b87210186180"><a name="b87210186180"></a><a name="b87210186180"></a>prefix-{{ .PVCNamespace }}_{{ .PVCName }}</strong>.</p>
<p id="p302mcpsimp"><a name="p302mcpsimp"></a><a name="p302mcpsimp"></a>The ultimate storage resource name is <strong id="b52901641111819"><a name="b52901641111819"></a><a name="b52901641111819"></a>prefix-namespace_pvc-1-c2fd3f46bf174a7db88e2e3232bae434</strong>.</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p1913415525920"><a name="p1913415525920"></a><a name="p1913415525920"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p159151023181412"><a name="p159151023181412"></a><a name="p159151023181412"></a>The value is fixed to <strong id="b465356297"><a name="b465356297"></a><a name="b465356297"></a>fs</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p13750171110290"><a name="en-us_topic_0000001162111564_p13750171110290"></a><a name="en-us_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p67501211102911"><a name="en-us_topic_0000001162111564_p67501211102911"></a><a name="en-us_topic_0000001162111564_p67501211102911"></a>Allocation type of the volume to be created. The following types are supported:</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li><strong id="b0621115111132"><a name="b0621115111132"></a><a name="b0621115111132"></a>thin</strong>: Not all required space is allocated during creation. Instead, the space is dynamically allocated based on the usage.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>thin</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p1134955145917"><a name="p1134955145917"></a><a name="p1134955145917"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p57502011142910"><a name="en-us_topic_0000001162111564_p57502011142910"></a><a name="en-us_topic_0000001162111564_p57502011142910"></a>If this parameter is set to <strong id="b1230990120304"><a name="b1230990120304"></a><a name="b1230990120304"></a>thin</strong>, the required space is not allocated immediately when a volume is created. Instead, the space is dynamically allocated based on the usage.</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p499022713590"><a name="p499022713590"></a><a name="p499022713590"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p552215442213"><a name="p552215442213"></a><a name="p552215442213"></a>IP address of the NFS client that can access the volume.</p>
<p id="p914297103211"><a name="p914297103211"></a><a name="p914297103211"></a>You can enter the client host name (a full domain name is recommended), client IP address, or client IP address segment.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637013765210"><a name="p1637013765210"></a><a name="p1637013765210"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p113981010185211"><a name="p113981010185211"></a><a name="p113981010185211"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p16134125519590"><a name="p16134125519590"></a><a name="p16134125519590"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p466615315578"><a name="p466615315578"></a><a name="p466615315578"></a>The asterisk (*) can be used to indicate any client. If you are not sure about the IP address of the access client, you are advised to use the asterisk (*) to prevent the client access from being rejected by the storage system.</p>
<p id="p164521752175617"><a name="p164521752175617"></a><a name="p164521752175617"></a>If the client host name is used, you are advised to use the full domain name.</p>
<p id="p20828214135714"><a name="p20828214135714"></a><a name="p20828214135714"></a>The IP addresses can be IPv4 addresses, IPv6 addresses, or a combination of IPv4 and IPv6 addresses.</p>
<p id="p208641555185710"><a name="p208641555185710"></a><a name="p208641555185710"></a>You can enter multiple host names, IP addresses, or IP address segments and separate them with semicolons (;). Example: <strong id="b1791131414223"><a name="b1791131414223"></a><a name="b1791131414223"></a>192.168.0.10;192.168.0.0/24;myserver1.test</strong></p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row475081162913"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p187501311122918"><a name="en-us_topic_0000001162111564_p187501311122918"></a><a name="en-us_topic_0000001162111564_p187501311122918"></a>parameters.cloneSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p77501911192918"><a name="en-us_topic_0000001162111564_p77501911192918"></a><a name="en-us_topic_0000001162111564_p77501911192918"></a>Cloning speed. The value ranges from 1 to 4.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p20370157155213"><a name="p20370157155213"></a><a name="p20370157155213"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p2398810105211"><a name="p2398810105211"></a><a name="p2398810105211"></a>3</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p213412554593"><a name="p213412554593"></a><a name="p213412554593"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p1775091110298"><a name="en-us_topic_0000001162111564_p1775091110298"></a><a name="en-us_topic_0000001162111564_p1775091110298"></a><strong id="b176541499232"><a name="b176541499232"></a><a name="b176541499232"></a>4</strong> indicates the highest speed. This parameter takes effect when a PV is cloned or a PV is created using a snapshot.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750161119295"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p133711471387"><a name="p133711471387"></a><a name="p133711471387"></a>parameters.applicationType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p153378472388"><a name="p153378472388"></a><a name="p153378472388"></a>Application type name when a file system is created.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p193700711523"><a name="p193700711523"></a><a name="p193700711523"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p8398201010524"><a name="p8398201010524"></a><a name="p8398201010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p113415510596"><a name="p113415510596"></a><a name="p113415510596"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p1795516502165"><a name="p1795516502165"></a><a name="p1795516502165"></a>Log in to DeviceManager and choose <strong id="b17381251194810"><a name="b17381251194810"></a><a name="b17381251194810"></a>Services</strong> &gt; <strong id="b1973819511485"><a name="b1973819511485"></a><a name="b1973819511485"></a>File Service</strong> &gt; <strong id="b1738451124818"><a name="b1738451124818"></a><a name="b1738451124818"></a>File Systems</strong> &gt; <strong id="b107381251194816"><a name="b107381251194816"></a><a name="b107381251194816"></a>Create</strong> to obtain the application type name.</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p813405513593"><a name="p813405513593"></a><a name="p813405513593"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p24789316192"><a name="p24789316192"></a><a name="p24789316192"></a>For details about the supported QoS configurations, see <a href="#table1315616262719">Table 3</a>.</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p101341755105914"><a name="p101341755105914"></a><a name="p101341755105914"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>For details about the configuration format, refer to the Linux permission settings, for example, 777 and 755.</p>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p1413416553593"><a name="p1413416553593"></a><a name="p1413416553593"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p11134115595916"><a name="p11134115595916"></a><a name="p11134115595916"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row4779143834112"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6779173815418"><a name="p6779173815418"></a><a name="p6779173815418"></a>parameters.accesskrb5</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p159171449164417"><a name="p159171449164417"></a><a name="p159171449164417"></a>Configures the krb5 security protocol.</p>
<a name="ul957213141953"></a><a name="ul957213141953"></a><ul id="ul957213141953"><li><strong id="b18789162612508"><a name="b18789162612508"></a><a name="b18789162612508"></a>read_only</strong>: read-only</li><li><strong id="b090243019503"><a name="b090243019503"></a><a name="b090243019503"></a>read_write</strong>: read and write</li><li><strong id="b1731815356507"><a name="b1731815356507"></a><a name="b1731815356507"></a>none</strong>: no permission</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p577912382417"><a name="p577912382417"></a><a name="p577912382417"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p9779193814412"><a name="p9779193814412"></a><a name="p9779193814412"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p111342055115917"><a name="p111342055115917"></a><a name="p111342055115917"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p15292191316454"><a name="p15292191316454"></a><a name="p15292191316454"></a>During mounting, you can specify the <strong id="b655174415014"><a name="b655174415014"></a><a name="b655174415014"></a>sec</strong> parameter in <strong id="b12405104713508"><a name="b12405104713508"></a><a name="b12405104713508"></a>mountOptions</strong>.</p>
</td>
</tr>
<tr id="row99331045154111"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p933031214424"><a name="p933031214424"></a><a name="p933031214424"></a>parameters.accesskrb5i</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p7359241154"><a name="p7359241154"></a><a name="p7359241154"></a>Configures the krb5i security protocol.</p>
<a name="ul149421336953"></a><a name="ul149421336953"></a><ul id="ul149421336953"><li><strong id="b43471279502"><a name="b43471279502"></a><a name="b43471279502"></a>read_only</strong>: read-only</li><li><strong id="b666770165"><a name="b666770165"></a><a name="b666770165"></a>read_write</strong>: read and write</li><li><strong id="b379459953"><a name="b379459953"></a><a name="b379459953"></a>none</strong>: no permission</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p129331245154111"><a name="p129331245154111"></a><a name="p129331245154111"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p96976291391"><a name="p96976291391"></a><a name="p96976291391"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p1713445513599"><a name="p1713445513599"></a><a name="p1713445513599"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p787455154620"><a name="p787455154620"></a><a name="p787455154620"></a>During mounting, you can specify the <strong id="b1072939106"><a name="b1072939106"></a><a name="b1072939106"></a>sec</strong> parameter in <strong id="b266606367"><a name="b266606367"></a><a name="b266606367"></a>mountOptions</strong>.</p>
</td>
</tr>
<tr id="row47801443164117"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p11892181264220"><a name="p11892181264220"></a><a name="p11892181264220"></a>parameters.accesskrb5p</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p19699145314447"><a name="p19699145314447"></a><a name="p19699145314447"></a>Configures the krb5p security protocol.</p>
<a name="ul1713519393512"></a><a name="ul1713519393512"></a><ul id="ul1713519393512"><li><strong id="b1335072755019"><a name="b1335072755019"></a><a name="b1335072755019"></a>read_only</strong>: read-only</li><li><strong id="b230248439"><a name="b230248439"></a><a name="b230248439"></a>read_write</strong>: read and write</li><li><strong id="b923881184"><a name="b923881184"></a><a name="b923881184"></a>none</strong>: no permission</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1780134314118"><a name="p1780134314118"></a><a name="p1780134314118"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p14114173118919"><a name="p14114173118919"></a><a name="p14114173118919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p131341955105920"><a name="p131341955105920"></a><a name="p131341955105920"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p1132519619463"><a name="p1132519619463"></a><a name="p1132519619463"></a>During mounting, you can specify the <strong id="b1424133796"><a name="b1424133796"></a><a name="b1424133796"></a>sec</strong> parameter in <strong id="b706769923"><a name="b706769923"></a><a name="b706769923"></a>mountOptions</strong>.</p>
</td>
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
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p101347555596"><a name="p101347555596"></a><a name="p101347555596"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p1346853212219"><a name="p1346853212219"></a><a name="p1346853212219"></a>Only NAS storage is supported.</p>
</td>
</tr>
<tr id="row102662571219"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p526715711214"><a name="p526715711214"></a><a name="p526715711214"></a>parameters.reservedSnapshotSpaceRatio</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p18267205722111"><a name="p18267205722111"></a><a name="p18267205722111"></a>Configures reserved snapshot space.</p>
<p id="p31927526212"><a name="p31927526212"></a><a name="p31927526212"></a>Value type: character string</p>
<p id="p1010918514227"><a name="p1010918514227"></a><a name="p1010918514227"></a>Value range: 0 to 50</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p3370167175211"><a name="p3370167175211"></a><a name="p3370167175211"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p5398131019522"><a name="p5398131019522"></a><a name="p5398131019522"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p16134155555910"><a name="p16134155555910"></a><a name="p16134155555910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p826718573213"><a name="p826718573213"></a><a name="p826718573213"></a>-</p>
</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a>parameters.disableVerifyCapacity</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1899222312222"><a name="p1899222312222"></a><a name="p1899222312222"></a>Whether to disable volume capacity verification. After this function is disabled, the system will not verify whether the volume capacity is an integer multiple of the sector size.</p>
<p id="p4236912172515"><a name="p4236912172515"></a><a name="p4236912172515"></a>The value can be:</p>
<a name="ul7370193012510"></a><a name="ul7370193012510"></a><ul id="ul7370193012510"><li>"true": disables volume capacity verification.</li><li>"false": enables volume capacity verification.</li></ul>
<div class="notice" id="note163681158114916"><a name="note163681158114916"></a><a name="note163681158114916"></a><span class="noticetitle"> NOTICE: </span><div class="noticebody"><p id="p6368158104913"><a name="p6368158104913"></a><a name="p6368158104913"></a>When Red Hat OpenShift Virtualization is used to connect to CSI, this parameter must be set to <strong id="b214739301311256"><a name="b214739301311256"></a><a name="b214739301311256"></a>true</strong>.</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p3134555195918"><a name="p3134555195918"></a><a name="p3134555195918"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p0723450135618"><a name="p0723450135618"></a><a name="p0723450135618"></a>For OceanDisk, the sector size is 512 bytes.</p>
</td>
</tr>
<tr id="row4937192492016"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1893710249209"><a name="p1893710249209"></a><a name="p1893710249209"></a>parameters.description</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p20937182432010"><a name="p20937182432010"></a><a name="p20937182432010"></a>Description of the file system to be created.</p>
<p id="p259255182110"><a name="p259255182110"></a><a name="p259255182110"></a>Value type: character string</p>
<p id="p8541312112118"><a name="p8541312112118"></a><a name="p8541312112118"></a>The value contains 0 to 255 characters.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p15370175529"><a name="p15370175529"></a><a name="p15370175529"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p17398151010524"><a name="p17398151010524"></a><a name="p17398151010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p14134105525910"><a name="p14134105525910"></a><a name="p14134105525910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row1795755912408"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1036995916474"><a name="p1036995916474"></a><a name="p1036995916474"></a>parameters.advancedOptions</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p737mcpsimp"><a name="p737mcpsimp"></a><a name="p737mcpsimp"></a>Advanced <span id="text221712597301"><a name="text221712597301"></a><a name="text221712597301"></a>volume creation</span> parameters.</p>
<p id="p738mcpsimp"><a name="p738mcpsimp"></a><a name="p738mcpsimp"></a>The value of the parameter is JSON character strings in dictionary format. A character string is enclosed by single quotation marks and the dictionary key by double quotation marks. Example: <strong id="b5194134115274"><a name="b5194134115274"></a><a name="b5194134115274"></a>'{"CAPACITYTHRESHOLD": 90}'</strong></p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p53719725212"><a name="p53719725212"></a><a name="p53719725212"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p13398141016526"><a name="p13398141016526"></a><a name="p13398141016526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.191077194012327%" headers="mcps1.2.7.1.5 "><p id="p17135555145910"><a name="p17135555145910"></a><a name="p17135555145910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.93581841307113%" headers="mcps1.2.7.1.6 "><p id="p208761647111216"><a name="p208761647111216"></a><a name="p208761647111216"></a>For details about the supported advanced parameters, see <a href="#_table034918373916">Table 4</a>.</p>
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
<p id="p328516567514"><a name="p328516567514"></a><a name="p328516567514"></a><strong id="b1829141763615"><a name="b1829141763615"></a><a name="b1829141763615"></a>nfsvers</strong>: protocol version for NFS mounting. The value can be <strong id="b62331610115010"><a name="b62331610115010"></a><a name="b62331610115010"></a>3</strong> or <strong id="b1734711365011"><a name="b1734711365011"></a><a name="b1734711365011"></a>4.0</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p15285356185114"><a name="p15285356185114"></a><a name="p15285356185114"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p182851756145119"><a name="p182851756145119"></a><a name="p182851756145119"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p228545619510"><a name="p228545619510"></a><a name="p228545619510"></a>This parameter is optional after the <strong id="b17158349193611"><a name="b17158349193611"></a><a name="b17158349193611"></a>-o</strong> parameter when the <strong id="b19158549153613"><a name="b19158549153613"></a><a name="b19158549153613"></a>mount</strong> command is executed on the host. The value is in list format.</p>
<p id="p13285856115110"><a name="p13285856115110"></a><a name="p13285856115110"></a>If the NFS version is specified for mounting, NFS 3 and 4.0 protocols are supported (the protocol must be supported and enabled on storage devices).</p>
</td>
</tr>
<tr id="row6770194365110"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p92851256105112"><a name="p92851256105112"></a><a name="p92851256105112"></a>mountOptions.sec</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p172852567515"><a name="p172852567515"></a><a name="p172852567515"></a>Kerberos 5 protocol for mounting NFS file systems.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p128511565512"><a name="p128511565512"></a><a name="p128511565512"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p152851756145118"><a name="p152851756145118"></a><a name="p152851756145118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><a name="ul1028516561513"></a><a name="ul1028516561513"></a><ul id="ul1028516561513"><li>If Kerberos 5 is used, set this parameter to <strong id="b1435135952518"><a name="b1435135952518"></a><a name="b1435135952518"></a>krb5</strong>.</li><li>If Kerberos 5i is used, set this parameter to <strong id="b79148018262"><a name="b79148018262"></a><a name="b79148018262"></a>krb5i</strong>.</li><li>If Kerberos 5p is used, set this parameter to <strong id="b1916811982618"><a name="b1916811982618"></a><a name="b1916811982618"></a>krb5p</strong>.</li><li>Only NFS 4.0 supports Kerberos.</li></ul>
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
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p771014195198"><a name="p771014195198"></a><a name="p771014195198"></a>-</p>
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
</tbody>
</table>

**Table  3**  Supported QoS configurations

<a name="table1315616262719"></a>
<table><thead align="left"><tr id="row111561026772"><th class="cellrowborder" valign="top" width="13.278672132786722%" id="mcps1.2.5.1.1"><p id="p2579113031316"><a name="p2579113031316"></a><a name="p2579113031316"></a>Storage Type</p>
</th>
<th class="cellrowborder" valign="top" width="15.348465153484653%" id="mcps1.2.5.1.2"><p id="p1915611264713"><a name="p1915611264713"></a><a name="p1915611264713"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.167383261673834%" id="mcps1.2.5.1.3"><p id="p915615267717"><a name="p915615267717"></a><a name="p915615267717"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="45.205479452054796%" id="mcps1.2.5.1.4"><p id="p111561926172"><a name="p111561926172"></a><a name="p111561926172"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row18484951131113"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="p35795302132"><a name="p35795302132"></a><a name="p35795302132"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="p18524175292"><a name="p18524175292"></a><a name="p18524175292"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="p05251782913"><a name="p05251782913"></a><a name="p05251782913"></a>Read/write type.</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="p152017102914"><a name="p152017102914"></a><a name="p152017102914"></a>This parameter is optional. If it is not specified, the default value of the storage backend is used. For details, see related storage documents.</p>
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
<tr id="row19156226876"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="p74551059151512"><a name="p74551059151512"></a><a name="p74551059151512"></a>OceanStor Dorado/OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="p115692619717"><a name="p115692619717"></a><a name="p115692619717"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="p41575261777"><a name="p41575261777"></a><a name="p41575261777"></a>Read/write type.</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="p1315717261879"><a name="p1315717261879"></a><a name="p1315717261879"></a>The value can be:</p>
<a name="ul121571261076"></a><a name="ul121571261076"></a><ul id="ul121571261076"><li><strong id="b78146864311"><a name="b78146864311"></a><a name="b78146864311"></a>2</strong>: read and write I/Os</li></ul>
</td>
</tr>
<tr id="row17157826078"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p2015762612718"><a name="p2015762612718"></a><a name="p2015762612718"></a>MAXBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p7157126276"><a name="p7157126276"></a><a name="p7157126276"></a>Maximum bandwidth. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p1515732617718"><a name="p1515732617718"></a><a name="p1515732617718"></a>The value is an integer ranging from 1 to 999999999, expressed in MB/s.</p>
</td>
</tr>
<tr id="row1215710263712"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p191576267720"><a name="p191576267720"></a><a name="p191576267720"></a>MINBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1215715261371"><a name="p1215715261371"></a><a name="p1215715261371"></a>Minimum bandwidth. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p8157426475"><a name="p8157426475"></a><a name="p8157426475"></a>The value is an integer ranging from 1 to 999999999, expressed in MB/s.</p>
</td>
</tr>
<tr id="row415742618720"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p01578266719"><a name="p01578266719"></a><a name="p01578266719"></a>MAXIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1515716261474"><a name="p1515716261474"></a><a name="p1515716261474"></a>Maximum IOPS. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p131571926873"><a name="p131571926873"></a><a name="p131571926873"></a>The value is an integer ranging from 100 to 999999999.</p>
</td>
</tr>
<tr id="row215718268711"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p01574267717"><a name="p01574267717"></a><a name="p01574267717"></a>MINIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p151571326777"><a name="p151571326777"></a><a name="p151571326777"></a>Minimum IOPS. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p15157102614718"><a name="p15157102614718"></a><a name="p15157102614718"></a>The value is an integer ranging from 100 to 999999999.</p>
</td>
</tr>
<tr id="row20157162619710"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p4157626475"><a name="p4157626475"></a><a name="p4157626475"></a>LATENCY</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p4157202613716"><a name="p4157202613716"></a><a name="p4157202613716"></a>Maximum latency. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="p111571264718"><a name="p111571264718"></a><a name="p111571264718"></a>The value can be <strong id="b635674414410"><a name="b635674414410"></a><a name="b635674414410"></a>0.5</strong> or <strong id="b5357174420445"><a name="b5357174420445"></a><a name="b5357174420445"></a>1.5</strong>, expressed in ms.</p>
</td>
</tr>
</tbody>
</table>

**Table  4**  Supported advanced volume creation parameters

<a name="_table034918373916"></a>
<table><thead align="left"><tr id="row756mcpsimp"><th class="cellrowborder" valign="top" width="16.85%" id="mcps1.2.4.1.1"><p id="p760mcpsimp"><a name="p760mcpsimp"></a><a name="p760mcpsimp"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="39.33%" id="mcps1.2.4.1.2"><p id="p762mcpsimp"><a name="p762mcpsimp"></a><a name="p762mcpsimp"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="43.82%" id="mcps1.2.4.1.3"><p id="p764mcpsimp"><a name="p764mcpsimp"></a><a name="p764mcpsimp"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row766mcpsimp"><td class="cellrowborder" valign="top" width="16.85%" headers="mcps1.2.4.1.1 "><p id="p770mcpsimp"><a name="p770mcpsimp"></a><a name="p770mcpsimp"></a>CAPACITYTHRESHOLD</p>
</td>
<td class="cellrowborder" valign="top" width="39.33%" headers="mcps1.2.4.1.2 "><p id="p773mcpsimp"><a name="p773mcpsimp"></a><a name="p773mcpsimp"></a>Total capacity alarm threshold.</p>
</td>
<td class="cellrowborder" valign="top" width="43.82%" headers="mcps1.2.4.1.3 "><p id="p775mcpsimp"><a name="p775mcpsimp"></a><a name="p775mcpsimp"></a>Parameter type: uint64.</p>
<p id="p776mcpsimp"><a name="p776mcpsimp"></a><a name="p776mcpsimp"></a>For details about the default value and value range, see the corresponding storage product manual.</p>
</td>
</tr>
</tbody>
</table>

