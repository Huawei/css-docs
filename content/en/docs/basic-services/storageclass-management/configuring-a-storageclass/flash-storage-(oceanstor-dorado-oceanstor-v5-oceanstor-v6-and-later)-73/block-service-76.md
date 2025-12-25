---
title: "Block Service"
linkTitle: "Block Service"
description: 
weight: 3
---

## Creating a StorageClass{#section432911256567}

1.  Prepare a StorageClass configuration file, for example,  **mysc.yaml**. For details about the StorageClass configuration, see the following example.
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

## Block Storage Class Configuration Example{#section19821415151111}

If LUNs are used as storage resources and the file system needs to be formatted to a local file system, refer to the following example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: lun-181
  pool: StoragePool001
  volumeType: lun
  allocType: thin
  fsType: ext4
```

## StorageClass Parameters Supported by Block Services{#section624915310113}

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
<p id="p061820373216"><a name="p061820373216"></a><a name="p061820373216"></a>The value is the same as that of <strong id="b9443556506"><a name="b9443556506"></a><a name="b9443556506"></a>driverName</strong> in the <strong id="b13444205611014"><a name="b13444205611014"></a><a name="b13444205611014"></a>values.yaml</strong> file.</p>
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
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p134321427192916"><a name="p134321427192916"></a><a name="p134321427192916"></a>List of mount parameters, which can be used to specify the parameters of the <strong id="b183021113101313"><a name="b183021113101313"></a><a name="b183021113101313"></a>-o</strong> option when the <strong id="b113021013131317"><a name="b113021013131317"></a><a name="b113021013131317"></a>mount</strong> command is executed on a host.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p2432227172910"><a name="p2432227172910"></a><a name="p2432227172910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1432112762919"><a name="p1432112762919"></a><a name="p1432112762919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1613355555915"><a name="p1613355555915"></a><a name="p1613355555915"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p15432162772912"><a name="p15432162772912"></a><a name="p15432162772912"></a>For details about common parameters in <strong id="b19102172414139"><a name="b19102172414139"></a><a name="b19102172414139"></a>mountOptions</strong>, see <a href="#table65545557506">Table 2</a>.</p>
<p id="p104322027152920"><a name="p104322027152920"></a><a name="p104322027152920"></a>You can also specify other mount parameters.</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1120145314312"><a name="p1120145314312"></a><a name="p1120145314312"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p2201185318312"><a name="p2201185318312"></a><a name="p2201185318312"></a>Name of the backend where the resource to be created is located. This field must be set if <strong id="b834202100114433"><a name="b834202100114433"></a><a name="b834202100114433"></a>parameters.pool</strong> is set.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p123704712528"><a name="p123704712528"></a><a name="p123704712528"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p33980109524"><a name="p33980109524"></a><a name="p33980109524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p10863133161415"><a name="p10863133161415"></a><a name="p10863133161415"></a>No</p>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p78631236144"><a name="p78631236144"></a><a name="p78631236144"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p99571317978"><a name="p99571317978"></a><a name="p99571317978"></a>If this parameter is not set, Huawei CSI will randomly select a storage pool that meets the capacity requirements from the selected backend to create resources. You are advised to specify a storage pool to ensure that the created resource is located in the expected storage pool.</p>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p2086315351417"><a name="p2086315351417"></a><a name="p2086315351417"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul165061538173414"></a><a name="ul165061538173414"></a><ul id="ul165061538173414"><li>The value can contain letters, digits, hyphens (-), underscores (_), and periods (.). This parameter cannot be left empty. The length of the generated storage resource name ranges from 1 to 255 characters.</li><li>Both the PVC namespace and PVC name must be configured.</li><li>To avoid duplicate resource names, the PVC UID is added to the end of the name as a unique identifier by default.</li></ul>
<p id="p3486174714359"><a name="p3486174714359"></a><a name="p3486174714359"></a></p>
<p id="p292mcpsimp"><a name="p292mcpsimp"></a><a name="p292mcpsimp"></a>Configuration example:</p>
<p id="p293mcpsimp"><a name="p293mcpsimp"></a><a name="p293mcpsimp"></a>PVC namespace: <strong id="b1772844111612"><a name="b1772844111612"></a><a name="b1772844111612"></a>namespace</strong>. PVC name: <strong id="b6721444171616"><a name="b6721444171616"></a><a name="b6721444171616"></a>pvc-1</strong>. PVC UID: <strong id="b8721544101619"><a name="b8721544101619"></a><a name="b8721544101619"></a>c2fd3f46-bf17-4a7d-b88e-2e3232bae434</strong>.</p>
<p id="p301mcpsimp"><a name="p301mcpsimp"></a><a name="p301mcpsimp"></a><strong id="b191391958141616"><a name="b191391958141616"></a><a name="b191391958141616"></a>volumeName</strong> is set to <strong id="b15139145819160"><a name="b15139145819160"></a><a name="b15139145819160"></a>prefix-{{ .PVCNamespace }}_{{ .PVCName }}</strong>.</p>
<p id="p302mcpsimp"><a name="p302mcpsimp"></a><a name="p302mcpsimp"></a>The ultimate storage resource name is <strong id="b138557135172"><a name="b138557135172"></a><a name="b138557135172"></a>prefix-namespace_pvc-1-c2fd3f46bf174a7db88e2e3232bae434</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p1775061119292"><a name="en-us_topic_0000001162111564_p1775061119292"></a><a name="en-us_topic_0000001162111564_p1775061119292"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p975011122920"><a name="en-us_topic_0000001162111564_p975011122920"></a><a name="en-us_topic_0000001162111564_p975011122920"></a>Type of the volume to be created. The following types are supported:</p>
<a name="ul1552484812564"></a><a name="ul1552484812564"></a><ul id="ul1552484812564"><li><strong id="b1733717591123"><a name="b1733717591123"></a><a name="b1733717591123"></a>lun</strong>: A LUN is provisioned on the storage side.</li><li><strong id="b10216124101312"><a name="b10216124101312"></a><a name="b10216124101312"></a>fs</strong>: A file system is provisioned on the storage side.</li><li><strong id="b13356202431717"><a name="b13356202431717"></a><a name="b13356202431717"></a>dtree</strong>: A volume of the dtree type is provisioned on the storage side.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1837014765216"><a name="p1837014765216"></a><a name="p1837014765216"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p5398141035217"><a name="p5398141035217"></a><a name="p5398141035217"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p686315351411"><a name="p686315351411"></a><a name="p686315351411"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p153691347193413"><a name="p153691347193413"></a><a name="p153691347193413"></a>The value is fixed to <strong id="b1454615611477"><a name="b1454615611477"></a><a name="b1454615611477"></a>lun</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p13750171110290"><a name="en-us_topic_0000001162111564_p13750171110290"></a><a name="en-us_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p67501211102911"><a name="en-us_topic_0000001162111564_p67501211102911"></a><a name="en-us_topic_0000001162111564_p67501211102911"></a>Allocation type of the volume to be created. The following types are supported:</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li><strong id="b12104350161812"><a name="b12104350161812"></a><a name="b12104350161812"></a>thin</strong>: Not all required space is allocated during creation. Instead, the space is dynamically allocated based on the usage.</li><li><strong id="b1073895421813"><a name="b1073895421813"></a><a name="b1073895421813"></a>thick</strong>: All required space is allocated during creation.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>thin</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p18863335147"><a name="p18863335147"></a><a name="p18863335147"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p57502011142910"><a name="en-us_topic_0000001162111564_p57502011142910"></a><a name="en-us_topic_0000001162111564_p57502011142910"></a>If this parameter is set to <strong id="b211501910933320"><a name="b211501910933320"></a><a name="b211501910933320"></a>thin</strong>, the required space is not allocated immediately when a volume is created. Instead, the space is dynamically allocated based on the usage.</p>
<p id="p371813715289"><a name="p371813715289"></a><a name="p371813715289"></a>OceanStor Dorado does not support <strong id="b156260097711475"><a name="b156260097711475"></a><a name="b156260097711475"></a>thick</strong>.</p>
</td>
</tr>
<tr id="row167642021133711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p18750171111299"><a name="en-us_topic_0000001162111564_p18750171111299"></a><a name="en-us_topic_0000001162111564_p18750171111299"></a>parameters.fsType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p19169191111571"><a name="p19169191111571"></a><a name="p19169191111571"></a>Type of a host file system. The supported types are:</p>
<a name="ul9614171916576"></a><a name="ul9614171916576"></a><ul id="ul9614171916576"><li>ext2</li><li>ext3</li><li>ext4</li><li>xfs</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p937047165217"><a name="p937047165217"></a><a name="p937047165217"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1439871055220"><a name="p1439871055220"></a><a name="p1439871055220"></a>ext4</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p10863113181414"><a name="p10863113181414"></a><a name="p10863113181414"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p8750311172910"><a name="en-us_topic_0000001162111564_p8750311172910"></a><a name="en-us_topic_0000001162111564_p8750311172910"></a>This parameter is available only when <strong id="b1620884191912"><a name="b1620884191912"></a><a name="b1620884191912"></a>volumeMode</strong> of the PVC is set to <strong id="b112083415194"><a name="b112083415194"></a><a name="b112083415194"></a>Filesystem</strong>.</p>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p208635341411"><a name="p208635341411"></a><a name="p208635341411"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p1775091110298"><a name="en-us_topic_0000001162111564_p1775091110298"></a><a name="en-us_topic_0000001162111564_p1775091110298"></a><strong id="b13914307194"><a name="b13914307194"></a><a name="b13914307194"></a>4</strong> indicates the highest speed. This parameter takes effect when a PVC is cloned or a PVC is created from a snapshot.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750161119295"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p133711471387"><a name="p133711471387"></a><a name="p133711471387"></a>parameters.applicationType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p153378472388"><a name="p153378472388"></a><a name="p153378472388"></a>Application type name of the LUN to be created.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p193700711523"><a name="p193700711523"></a><a name="p193700711523"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p8398201010524"><a name="p8398201010524"></a><a name="p8398201010524"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p886363141411"><a name="p886363141411"></a><a name="p886363141411"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p19352161314317"><a name="p19352161314317"></a><a name="p19352161314317"></a>Log in to DeviceManager and choose <strong id="b1694943220256"><a name="b1694943220256"></a><a name="b1694943220256"></a>Services</strong> &gt; <strong id="b0949432202510"><a name="b0949432202510"></a><a name="b0949432202510"></a>Block Service</strong> &gt; <strong id="b7949163213259"><a name="b7949163213259"></a><a name="b7949163213259"></a>LUN Groups</strong> (or <strong id="b79491732122510"><a name="b79491732122510"></a><a name="b79491732122510"></a>Namespace Groups</strong>) &gt; <strong id="b494963242513"><a name="b494963242513"></a><a name="b494963242513"></a>LUNs</strong> (or <strong id="b3949123252518"><a name="b3949123252518"></a><a name="b3949123252518"></a>Namespaces</strong>) &gt; <strong id="b17949173212515"><a name="b17949173212515"></a><a name="b17949173212515"></a>Create</strong> to obtain the application type name.</p>
</td>
</tr>
<tr id="row15478113119190"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p18478163131914"><a name="p18478163131914"></a><a name="p18478163131914"></a>parameters.qos</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15525175120211"><a name="p15525175120211"></a><a name="p15525175120211"></a>LUN/NAS QoS settings of the PV on the storage side.</p>
<p id="p12218174732111"><a name="p12218174732111"></a><a name="p12218174732111"></a>The value of the parameter is JSON character strings in dictionary format. A character string is enclosed by single quotation marks and the dictionary key by double quotation marks. Example: <strong id="b696811110334"><a name="b696811110334"></a><a name="b696811110334"></a>'{"maxMBPS": 999, "maxIOPS": 999}'</strong></p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p03704715211"><a name="p03704715211"></a><a name="p03704715211"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1439818100526"><a name="p1439818100526"></a><a name="p1439818100526"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p158633361418"><a name="p158633361418"></a><a name="p158633361418"></a>No</p>
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
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1886312301416"><a name="p1886312301416"></a><a name="p1886312301416"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p18909114043117"><a name="p18909114043117"></a><a name="p18909114043117"></a>For details about the configuration format, refer to the Linux permission settings, for example, 777 and 755.</p>
</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p12992202310228"><a name="p12992202310228"></a><a name="p12992202310228"></a>parameters.disableVerifyCapacity</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1899222312222"><a name="p1899222312222"></a><a name="p1899222312222"></a>Whether to disable volume capacity verification. After this function is disabled, the system will not verify whether the volume capacity is an integer multiple of the sector size.</p>
<p id="p4236912172515"><a name="p4236912172515"></a><a name="p4236912172515"></a>The value can be:</p>
<a name="ul7370193012510"></a><a name="ul7370193012510"></a><ul id="ul7370193012510"><li>"true": disables volume capacity verification.</li><li>"false": enables volume capacity verification.</li></ul>
<div class="notice" id="note163681158114916"><a name="note163681158114916"></a><a name="note163681158114916"></a><span class="noticetitle"> NOTICE: </span><div class="noticebody"><p id="p6368158104913"><a name="p6368158104913"></a><a name="p6368158104913"></a>When Red Hat OpenShift Virtualization is used to connect to CSI, this parameter must be set to <strong id="b1527161943419"><a name="b1527161943419"></a><a name="b1527161943419"></a>true</strong>.</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p149923239227"><a name="p149923239227"></a><a name="p149923239227"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p10992182382217"><a name="p10992182382217"></a><a name="p10992182382217"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1286333181417"><a name="p1286333181417"></a><a name="p1286333181417"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p0723450135618"><a name="p0723450135618"></a><a name="p0723450135618"></a>For OceanStor Dorado and OceanStor storage, the sector size is 512 bytes.</p>
</td>
</tr>
<tr id="row4937192492016"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1893710249209"><a name="p1893710249209"></a><a name="p1893710249209"></a>parameters.description</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p20937182432010"><a name="p20937182432010"></a><a name="p20937182432010"></a>Description of the LUN to be created.</p>
<p id="p259255182110"><a name="p259255182110"></a><a name="p259255182110"></a>Value type: character string</p>
<p id="p8541312112118"><a name="p8541312112118"></a><a name="p8541312112118"></a>The value contains 0 to 255 characters.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p15370175529"><a name="p15370175529"></a><a name="p15370175529"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p873262175517"><a name="p873262175517"></a><a name="p873262175517"></a>Created from Kubernetes CSI</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p2863193131413"><a name="p2863193131413"></a><a name="p2863193131413"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
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
<tbody><tr id="row15555205517503"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p202861156155119"><a name="p202861156155119"></a><a name="p202861156155119"></a>mountOptions.discard</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1928616565514"><a name="p1928616565514"></a><a name="p1928616565514"></a>Automatically triggers the Trim or Discard operation when a file system is mounted. This operation instructs a block device to release unused blocks.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p1328610561511"><a name="p1328610561511"></a><a name="p1328610561511"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p2286175613513"><a name="p2286175613513"></a><a name="p2286175613513"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p4286556155111"><a name="p4286556155111"></a><a name="p4286556155111"></a>The xfs and ext4 file systems are supported.</p>
</td>
</tr>
</tbody>
</table>

**Table  3**  Supported QoS configurations

<a name="table74841513116"></a>
<table><thead align="left"><tr id="en-us_topic_0000002427305089_row111561026772"><th class="cellrowborder" valign="top" width="13.278672132786722%" id="mcps1.2.5.1.1"><p id="en-us_topic_0000002427305089_p2579113031316"><a name="en-us_topic_0000002427305089_p2579113031316"></a><a name="en-us_topic_0000002427305089_p2579113031316"></a>Storage Type</p>
</th>
<th class="cellrowborder" valign="top" width="15.348465153484653%" id="mcps1.2.5.1.2"><p id="en-us_topic_0000002427305089_p1915611264713"><a name="en-us_topic_0000002427305089_p1915611264713"></a><a name="en-us_topic_0000002427305089_p1915611264713"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.167383261673834%" id="mcps1.2.5.1.3"><p id="en-us_topic_0000002427305089_p915615267717"><a name="en-us_topic_0000002427305089_p915615267717"></a><a name="en-us_topic_0000002427305089_p915615267717"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="45.205479452054796%" id="mcps1.2.5.1.4"><p id="en-us_topic_0000002427305089_p111561926172"><a name="en-us_topic_0000002427305089_p111561926172"></a><a name="en-us_topic_0000002427305089_p111561926172"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000002427305089_row18484951131113"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p35795302132"><a name="en-us_topic_0000002427305089_p35795302132"></a><a name="en-us_topic_0000002427305089_p35795302132"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p18524175292"><a name="en-us_topic_0000002427305089_p18524175292"></a><a name="en-us_topic_0000002427305089_p18524175292"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p05251782913"><a name="en-us_topic_0000002427305089_p05251782913"></a><a name="en-us_topic_0000002427305089_p05251782913"></a>Read/write type.</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000002427305089_p152017102914"><a name="en-us_topic_0000002427305089_p152017102914"></a><a name="en-us_topic_0000002427305089_p152017102914"></a>This parameter is optional. If it is not specified, the default value of the storage backend is used. For details, see related storage documents.</p>
<p id="en-us_topic_0000002427305089_p85218172294"><a name="en-us_topic_0000002427305089_p85218172294"></a><a name="en-us_topic_0000002427305089_p85218172294"></a>The value can be:</p>
<a name="en-us_topic_0000002427305089_ul5521517142918"></a><a name="en-us_topic_0000002427305089_ul5521517142918"></a><ul id="en-us_topic_0000002427305089_ul5521517142918"><li><strong id="en-us_topic_0000002427305089_b1996635010414"><a name="en-us_topic_0000002427305089_b1996635010414"></a><a name="en-us_topic_0000002427305089_b1996635010414"></a>0</strong>: read I/O</li><li><strong id="en-us_topic_0000002427305089_b1795565594114"><a name="en-us_topic_0000002427305089_b1795565594114"></a><a name="en-us_topic_0000002427305089_b1795565594114"></a>1</strong>: write I/O</li><li><strong id="en-us_topic_0000002427305089_b656215064213"><a name="en-us_topic_0000002427305089_b656215064213"></a><a name="en-us_topic_0000002427305089_b656215064213"></a>2</strong>: read and write I/Os</li></ul>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row1548485117111"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p155211732919"><a name="en-us_topic_0000002427305089_p155211732919"></a><a name="en-us_topic_0000002427305089_p155211732919"></a>MAXBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p952111772918"><a name="en-us_topic_0000002427305089_p952111772918"></a><a name="en-us_topic_0000002427305089_p952111772918"></a>Maximum bandwidth. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p352171716294"><a name="en-us_topic_0000002427305089_p352171716294"></a><a name="en-us_topic_0000002427305089_p352171716294"></a>The value is an integer greater than 0, expressed in MB/s.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row124848513110"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p9522175292"><a name="en-us_topic_0000002427305089_p9522175292"></a><a name="en-us_topic_0000002427305089_p9522175292"></a>MINBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p19522171298"><a name="en-us_topic_0000002427305089_p19522171298"></a><a name="en-us_topic_0000002427305089_p19522171298"></a>Minimum bandwidth. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p2052141711297"><a name="en-us_topic_0000002427305089_p2052141711297"></a><a name="en-us_topic_0000002427305089_p2052141711297"></a>The value is an integer greater than 0, expressed in MB/s.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row74854512113"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p1052417132916"><a name="en-us_topic_0000002427305089_p1052417132916"></a><a name="en-us_topic_0000002427305089_p1052417132916"></a>MAXIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p352117102912"><a name="en-us_topic_0000002427305089_p352117102912"></a><a name="en-us_topic_0000002427305089_p352117102912"></a>Maximum IOPS. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p165211714296"><a name="en-us_topic_0000002427305089_p165211714296"></a><a name="en-us_topic_0000002427305089_p165211714296"></a>The value is an integer greater than 0.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row1816819710019"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p1316813713016"><a name="en-us_topic_0000002427305089_p1316813713016"></a><a name="en-us_topic_0000002427305089_p1316813713016"></a>MINIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p0521917172915"><a name="en-us_topic_0000002427305089_p0521917172915"></a><a name="en-us_topic_0000002427305089_p0521917172915"></a>Minimum IOPS. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p105201742914"><a name="en-us_topic_0000002427305089_p105201742914"></a><a name="en-us_topic_0000002427305089_p105201742914"></a>The value is an integer greater than 0.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row1448555120112"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p1952517192913"><a name="en-us_topic_0000002427305089_p1952517192913"></a><a name="en-us_topic_0000002427305089_p1952517192913"></a>LATENCY</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p85211722911"><a name="en-us_topic_0000002427305089_p85211722911"></a><a name="en-us_topic_0000002427305089_p85211722911"></a>Maximum latency. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p352161718293"><a name="en-us_topic_0000002427305089_p352161718293"></a><a name="en-us_topic_0000002427305089_p352161718293"></a>The value is an integer greater than 0, expressed in ms.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row19156226876"><td class="cellrowborder" rowspan="6" valign="top" width="13.278672132786722%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p74551059151512"><a name="en-us_topic_0000002427305089_p74551059151512"></a><a name="en-us_topic_0000002427305089_p74551059151512"></a>OceanStor Dorado/OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="15.348465153484653%" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p115692619717"><a name="en-us_topic_0000002427305089_p115692619717"></a><a name="en-us_topic_0000002427305089_p115692619717"></a>IOTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="26.167383261673834%" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p41575261777"><a name="en-us_topic_0000002427305089_p41575261777"></a><a name="en-us_topic_0000002427305089_p41575261777"></a>Read/write type.</p>
</td>
<td class="cellrowborder" valign="top" width="45.205479452054796%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0000002427305089_p1315717261879"><a name="en-us_topic_0000002427305089_p1315717261879"></a><a name="en-us_topic_0000002427305089_p1315717261879"></a>The value can be:</p>
<a name="en-us_topic_0000002427305089_ul121571261076"></a><a name="en-us_topic_0000002427305089_ul121571261076"></a><ul id="en-us_topic_0000002427305089_ul121571261076"><li><strong id="en-us_topic_0000002427305089_b78146864311"><a name="en-us_topic_0000002427305089_b78146864311"></a><a name="en-us_topic_0000002427305089_b78146864311"></a>2</strong>: read and write I/Os</li></ul>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row17157826078"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p2015762612718"><a name="en-us_topic_0000002427305089_p2015762612718"></a><a name="en-us_topic_0000002427305089_p2015762612718"></a>MAXBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p7157126276"><a name="en-us_topic_0000002427305089_p7157126276"></a><a name="en-us_topic_0000002427305089_p7157126276"></a>Maximum bandwidth. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p1515732617718"><a name="en-us_topic_0000002427305089_p1515732617718"></a><a name="en-us_topic_0000002427305089_p1515732617718"></a>The value is an integer ranging from 1 to 999999999, expressed in MB/s.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row1215710263712"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p191576267720"><a name="en-us_topic_0000002427305089_p191576267720"></a><a name="en-us_topic_0000002427305089_p191576267720"></a>MINBANDWIDTH</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p1215715261371"><a name="en-us_topic_0000002427305089_p1215715261371"></a><a name="en-us_topic_0000002427305089_p1215715261371"></a>Minimum bandwidth. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p8157426475"><a name="en-us_topic_0000002427305089_p8157426475"></a><a name="en-us_topic_0000002427305089_p8157426475"></a>The value is an integer ranging from 1 to 999999999, expressed in MB/s.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row415742618720"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p01578266719"><a name="en-us_topic_0000002427305089_p01578266719"></a><a name="en-us_topic_0000002427305089_p01578266719"></a>MAXIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p1515716261474"><a name="en-us_topic_0000002427305089_p1515716261474"></a><a name="en-us_topic_0000002427305089_p1515716261474"></a>Maximum IOPS. This is a restriction policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p131571926873"><a name="en-us_topic_0000002427305089_p131571926873"></a><a name="en-us_topic_0000002427305089_p131571926873"></a>The value is an integer ranging from 100 to 999999999.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row215718268711"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p01574267717"><a name="en-us_topic_0000002427305089_p01574267717"></a><a name="en-us_topic_0000002427305089_p01574267717"></a>MINIOPS</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p151571326777"><a name="en-us_topic_0000002427305089_p151571326777"></a><a name="en-us_topic_0000002427305089_p151571326777"></a>Minimum IOPS. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p15157102614718"><a name="en-us_topic_0000002427305089_p15157102614718"></a><a name="en-us_topic_0000002427305089_p15157102614718"></a>The value is an integer ranging from 100 to 999999999.</p>
</td>
</tr>
<tr id="en-us_topic_0000002427305089_row20157162619710"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0000002427305089_p4157626475"><a name="en-us_topic_0000002427305089_p4157626475"></a><a name="en-us_topic_0000002427305089_p4157626475"></a>LATENCY</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0000002427305089_p4157202613716"><a name="en-us_topic_0000002427305089_p4157202613716"></a><a name="en-us_topic_0000002427305089_p4157202613716"></a>Maximum latency. This is a protection policy parameter.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.3 "><p id="en-us_topic_0000002427305089_p111571264718"><a name="en-us_topic_0000002427305089_p111571264718"></a><a name="en-us_topic_0000002427305089_p111571264718"></a>The value can be <strong id="en-us_topic_0000002427305089_b635674414410"><a name="en-us_topic_0000002427305089_b635674414410"></a><a name="en-us_topic_0000002427305089_b635674414410"></a>0.5</strong> or <strong id="en-us_topic_0000002427305089_b5357174420445"><a name="en-us_topic_0000002427305089_b5357174420445"></a><a name="en-us_topic_0000002427305089_b5357174420445"></a>1.5</strong>, expressed in ms.</p>
</td>
</tr>
</tbody>
</table>

