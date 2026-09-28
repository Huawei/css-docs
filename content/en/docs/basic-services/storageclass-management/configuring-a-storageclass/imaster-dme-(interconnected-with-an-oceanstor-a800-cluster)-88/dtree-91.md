---
title: "Dtree"
linkTitle: "Dtree"
description: 
weight: 3
---

## Creating a StorageClass{#section826673014506}

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

## NFS Protocol Configuration Example{#section18328546173619}

When a container uses the NFS protocol to connect to dtree resources, refer to the following StorageClass configuration example. In this example, NFS version 3 is specified for mounting.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: nfs-dtree-181
  volumeType: dtree
  allocType: thin
  authClient: "*"
mountOptions:
  - nfsvers=3 # Specify the version 3 for NFS mounting.
```

## DataTurbo Protocol Configuration Example{#section17204182983712}

When a container uses the DataTurbo protocol to connect to dtree resources, refer to the following configuration example. In this example, the DataTurbo share user name is  **user01**.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: mysc
provisioner: csi.huawei.com
parameters:
  backend: dtfs-nas-181
  volumeType: dtree
  allocType: thin
  authUser: user01
```

## StorageClass Parameters Supported by Dtrees{#section17270153014505}

**Table  1**  StorageClass configuration parameters

<a name="en-us_topic_0000001162111564_table1975019113299"></a>
<table><thead align="left"><tr id="en-us_topic_0000001162111564_row1175051115295"><th class="cellrowborder" valign="top" width="18.481557577536446%" id="mcps1.2.7.1.1"><p id="p4360205445916"><a name="p4360205445916"></a><a name="p4360205445916"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="23.089717248801485%" id="mcps1.2.7.1.2"><p id="p3360185410592"><a name="p3360185410592"></a><a name="p3360185410592"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="6.848644946678408%" id="mcps1.2.7.1.3"><p id="p5360854155919"><a name="p5360854155919"></a><a name="p5360854155919"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="8.453184619900206%" id="mcps1.2.7.1.4"><p id="p53602054105911"><a name="p53602054105911"></a><a name="p53602054105911"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="7.35740142843166%" id="mcps1.2.7.1.5"><p id="p193607544599"><a name="p193607544599"></a><a name="p193607544599"></a>Whether the Volume Management Takes Effect</p>
</th>
<th class="cellrowborder" valign="top" width="35.7694941786518%" id="mcps1.2.7.1.6"><p id="p19360135495917"><a name="p19360135495917"></a><a name="p19360135495917"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14360115415917"><a name="p14360115415917"></a><a name="p14360115415917"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p836011544596"><a name="p836011544596"></a><a name="p836011544596"></a>User-defined name of a StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1736085411593"><a name="p1736085411593"></a><a name="p1736085411593"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p03601954125910"><a name="p03601954125910"></a><a name="p03601954125910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p11360145417590"><a name="p11360145417590"></a><a name="p11360145417590"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1360554145914"><a name="p1360554145914"></a><a name="p1360554145914"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p136014549598"><a name="p136014549598"></a><a name="p136014549598"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p536045495915"><a name="p536045495915"></a><a name="p536045495915"></a>Name of the provisioner.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1436035415598"><a name="p1436035415598"></a><a name="p1436035415598"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p036018545593"><a name="p036018545593"></a><a name="p036018545593"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p153609549594"><a name="p153609549594"></a><a name="p153609549594"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p16360654125917"><a name="p16360654125917"></a><a name="p16360654125917"></a>Set this parameter to the driver name set during Huawei CSI installation.</p>
<p id="p17360205455917"><a name="p17360205455917"></a><a name="p17360205455917"></a>The value is the same as that of <strong id="b79258211711"><a name="b79258211711"></a><a name="b79258211711"></a>driverName</strong> in the <strong id="b1392592113716"><a name="b1392592113716"></a><a name="b1392592113716"></a>values.yaml</strong> file.</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p536015495918"><a name="p536015495918"></a><a name="p536015495918"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1736035416597"><a name="p1736035416597"></a><a name="p1736035416597"></a>Reclamation policy. The following types are supported:</p>
<a name="ul1360115415918"></a><a name="ul1360115415918"></a><ul id="ul1360115415918"><li><strong id="b36023291379"><a name="b36023291379"></a><a name="b36023291379"></a>Delete</strong>: Resources are automatically reclaimed.</li><li><strong id="b1353414335714"><a name="b1353414335714"></a><a name="b1353414335714"></a>Retain</strong>: Resources are manually reclaimed.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p9360155413597"><a name="p9360155413597"></a><a name="p9360155413597"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p036055475913"><a name="p036055475913"></a><a name="p036055475913"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p536015415599"><a name="p536015415599"></a><a name="p536015415599"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul4360554145916"></a><a name="ul4360554145916"></a><ul id="ul4360554145916"><li><strong id="b697916401279"><a name="b697916401279"></a><a name="b697916401279"></a>Delete</strong>: When a PV/PVC is deleted, resources on the storage device are also deleted.</li><li><strong id="b54305914715"><a name="b54305914715"></a><a name="b54305914715"></a>Retain</strong>: When a PV/PVC is deleted, resources on the storage device are not deleted.</li></ul>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1936045416598"><a name="p1936045416598"></a><a name="p1936045416598"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p136065419593"><a name="p136065419593"></a><a name="p136065419593"></a>Whether to allow volume expansion. If this parameter is set to <strong id="b147713181882"><a name="b147713181882"></a><a name="b147713181882"></a>true</strong>, the capacity of the PV that uses the StorageClass can be expanded.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p123601054195913"><a name="p123601054195913"></a><a name="p123601054195913"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p536015546597"><a name="p536015546597"></a><a name="p536015546597"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p18360205415914"><a name="p18360205415914"></a><a name="p18360205415914"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p6360185415915"><a name="p6360185415915"></a><a name="p6360185415915"></a>This function can only be used to expand PV capacity but cannot be used to reduce PV capacity.</p>
</td>
</tr>
<tr id="row63343268297"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14360205410597"><a name="p14360205410597"></a><a name="p14360205410597"></a>mountOptions</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p7360115475917"><a name="p7360115475917"></a><a name="p7360115475917"></a>List of mount parameters, which can be used to specify the parameters of the <strong id="b93716466820"><a name="b93716466820"></a><a name="b93716466820"></a>-o</strong> option when the <strong id="b537164619818"><a name="b537164619818"></a><a name="b537164619818"></a>mount</strong> command is executed on a host.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p3360135435914"><a name="p3360135435914"></a><a name="p3360135435914"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p236015543598"><a name="p236015543598"></a><a name="p236015543598"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p4360154175917"><a name="p4360154175917"></a><a name="p4360154175917"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1936045445914"><a name="p1936045445914"></a><a name="p1936045445914"></a>For details about common parameters in <strong id="b88401059388"><a name="b88401059388"></a><a name="b88401059388"></a>mountOptions</strong>, see <a href="#table133792080248">Table 2</a>.</p>
<p id="p14360854175917"><a name="p14360854175917"></a><a name="p14360854175917"></a>You can also specify other mount parameters.</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p2360854165918"><a name="p2360854165918"></a><a name="p2360854165918"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p7360115414591"><a name="p7360115414591"></a><a name="p7360115414591"></a>Name of the backend where the resource to be created is located.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p173601654145917"><a name="p173601654145917"></a><a name="p173601654145917"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1036195435913"><a name="p1036195435913"></a><a name="p1036195435913"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p14361165411595"><a name="p14361165411595"></a><a name="p14361165411595"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p2023133002520"><a name="p2023133002520"></a><a name="p2023133002520"></a>If this parameter is not set, Huawei CSI will randomly select a backend that meets the capacity requirements to create resources.</p>
<p id="p020135316313"><a name="p020135316313"></a><a name="p020135316313"></a>You are advised to specify a backend to ensure that the created resource is located on the expected backend.</p>
<p id="p1746961523912"><a name="p1746961523912"></a><a name="p1746961523912"></a>This parameter is mandatory if <strong id="b287023483719"><a name="b287023483719"></a><a name="b287023483719"></a>parameters.parentname</strong> is set.</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p346918322193"><a name="p346918322193"></a><a name="p346918322193"></a>parameters.parentname</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1046913215196"><a name="p1046913215196"></a><a name="p1046913215196"></a>Name of a file system on the current storage device. Dtree is created in the file system.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p34696327196"><a name="p34696327196"></a><a name="p34696327196"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p19469032191910"><a name="p19469032191910"></a><a name="p19469032191910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p11469163213191"><a name="p11469163213191"></a><a name="p11469163213191"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1146912323198"><a name="p1146912323198"></a><a name="p1146912323198"></a>This parameter is mandatory when <strong id="b11416185610157"><a name="b11416185610157"></a><a name="b11416185610157"></a>parentname</strong> is not set for the backend.</p>
<p id="p17469143218194"><a name="p17469143218194"></a><a name="p17469143218194"></a>If <strong id="b647882513161"><a name="b647882513161"></a><a name="b647882513161"></a>parentname</strong> is configured only in the StorageClass but not configured in the storage backend, set <strong id="b10478102514161"><a name="b10478102514161"></a><a name="b10478102514161"></a>CSIDriverObject.attachRequired</strong> to <strong id="b74781725181615"><a name="b74781725181615"></a><a name="b74781725181615"></a>true</strong> during CSI installation.</p>
</td>
</tr>
<tr id="row12968565337"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p10361145455915"><a name="p10361145455915"></a><a name="p10361145455915"></a>parameters.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p12361125411596"><a name="p12361125411596"></a><a name="p12361125411596"></a>Name of the storage resource created by dynamic volume provisioning.</p>
<p id="p636111549590"><a name="p636111549590"></a><a name="p636111549590"></a>You can configure a placeholder to customize the storage resource name. The following placeholders are supported:</p>
<a name="ul0361354175919"></a><a name="ul0361354175919"></a><ul id="ul0361354175919"><li>PVC namespace: {{ .PVCNamespace }}</li><li>PVC name: {{ .PVCName }}</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1361175425912"><a name="p1361175425912"></a><a name="p1361175425912"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p236115412598"><a name="p236115412598"></a><a name="p236115412598"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p236114548594"><a name="p236114548594"></a><a name="p236114548594"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><a name="ul5361145475918"></a><a name="ul5361145475918"></a><ul id="ul5361145475918"><li>The value can contain letters, digits, hyphens (-), underscores (_), and periods (.). This parameter cannot be left empty. The length of the generated storage resource name ranges from 1 to 255 characters.</li><li>Both the PVC namespace and PVC name must be configured.</li><li>To avoid duplicate resource names, the PVC UID is added to the end of the name as a unique identifier by default.</li></ul>
<p id="p7361105465918"><a name="p7361105465918"></a><a name="p7361105465918"></a></p>
<p id="p23613547598"><a name="p23613547598"></a><a name="p23613547598"></a>Configuration example:</p>
<p id="p20361454185915"><a name="p20361454185915"></a><a name="p20361454185915"></a>PVC namespace: <strong id="b1388175574217"><a name="b1388175574217"></a><a name="b1388175574217"></a>namespace</strong>. PVC name: <strong id="b38885534215"><a name="b38885534215"></a><a name="b38885534215"></a>pvc-1</strong>. PVC UID: <strong id="b19883555427"><a name="b19883555427"></a><a name="b19883555427"></a>c2fd3f46-bf17-4a7d-b88e-2e3232bae434</strong>.</p>
<p id="p1136105425912"><a name="p1136105425912"></a><a name="p1136105425912"></a><strong id="b1094412334315"><a name="b1094412334315"></a><a name="b1094412334315"></a>volumeName</strong> is set to <strong id="b78991513134318"><a name="b78991513134318"></a><a name="b78991513134318"></a>prefix-</strong><em id="i6361161415431"><a name="i6361161415431"></a><a name="i6361161415431"></a>{{ .PVCNamespace }}</em><em id="i11415419134316"><a name="i11415419134316"></a><a name="i11415419134316"></a>_{{ .PVCName }}</em>.</p>
<p id="p14361145475913"><a name="p14361145475913"></a><a name="p14361145475913"></a>The ultimate storage resource name is <strong id="b1227117164312"><a name="b1227117164312"></a><a name="b1227117164312"></a>prefix-namespace_pvc-1-c2fd3f46bf174a7db88e2e3232bae434</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p336111545595"><a name="p336111545595"></a><a name="p336111545595"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1236105414591"><a name="p1236105414591"></a><a name="p1236105414591"></a>Type of the volume to be created. The following types are supported:</p>
<a name="ul83612547596"></a><a name="ul83612547596"></a><ul id="ul83612547596"><li><strong id="b92080441610534"><a name="b92080441610534"></a><a name="b92080441610534"></a>lun</strong>: A LUN is provisioned on the storage side.</li><li><strong id="b148308394310538"><a name="b148308394310538"></a><a name="b148308394310538"></a>fs</strong>: A file system is provisioned on the storage side.</li><li><strong id="b203429726105318"><a name="b203429726105318"></a><a name="b203429726105318"></a>dtree</strong>: A volume of the dtree type is provisioned on the storage side.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p5361115414595"><a name="p5361115414595"></a><a name="p5361115414595"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p836125405919"><a name="p836125405919"></a><a name="p836125405919"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1236119545592"><a name="p1236119545592"></a><a name="p1236119545592"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p11361354145911"><a name="p11361354145911"></a><a name="p11361354145911"></a><strong id="b1252413124719"><a name="b1252413124719"></a><a name="b1252413124719"></a>dtree</strong>: A volume of the dtree type is provisioned on the storage side.</p>
</td>
</tr>
<tr id="row20604911148"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="en-us_topic_0000001162111564_p13750171110290"><a name="en-us_topic_0000001162111564_p13750171110290"></a><a name="en-us_topic_0000001162111564_p13750171110290"></a>parameters.allocType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="en-us_topic_0000001162111564_p67501211102911"><a name="en-us_topic_0000001162111564_p67501211102911"></a><a name="en-us_topic_0000001162111564_p67501211102911"></a>Allocation type of the volume to be created. The following types are supported:</p>
<a name="ul4981655175619"></a><a name="ul4981655175619"></a><ul id="ul4981655175619"><li><strong id="b1332152074714"><a name="b1332152074714"></a><a name="b1332152074714"></a>thin</strong>: Not all required space is allocated during creation. Instead, the space is dynamically allocated based on the usage.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1637027125216"><a name="p1637027125216"></a><a name="p1637027125216"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p6398910155219"><a name="p6398910155219"></a><a name="p6398910155219"></a>thin</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p9722056181617"><a name="p9722056181617"></a><a name="p9722056181617"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="en-us_topic_0000001162111564_p57502011142910"><a name="en-us_topic_0000001162111564_p57502011142910"></a><a name="en-us_topic_0000001162111564_p57502011142910"></a>If this parameter is set to <strong id="b1123975524718"><a name="b1123975524718"></a><a name="b1123975524718"></a>thin</strong>, the required space is not allocated immediately when a volume is created. Instead, the space is dynamically allocated based on the usage.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1636105411595"><a name="p1636105411595"></a><a name="p1636105411595"></a>parameters.authClient</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1361145414593"><a name="p1361145414593"></a><a name="p1361145414593"></a>IP address of the NFS client that can access the volume. This parameter is mandatory when the <strong id="b748716313487"><a name="b748716313487"></a><a name="b748716313487"></a>nfs</strong> or <strong id="b3487338481"><a name="b3487338481"></a><a name="b3487338481"></a>nfs+</strong> protocol is used.</p>
<p id="p03611454155915"><a name="p03611454155915"></a><a name="p03611454155915"></a>You can enter the client host name (a full domain name is recommended), client IP address, or client IP address segment.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p17361175425917"><a name="p17361175425917"></a><a name="p17361175425917"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p636110547592"><a name="p636110547592"></a><a name="p636110547592"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p736185495917"><a name="p736185495917"></a><a name="p736185495917"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1636119549596"><a name="p1636119549596"></a><a name="p1636119549596"></a>The asterisk (*) can be used to indicate any client. If you are not sure about the IP address of the access client, you are advised to use the asterisk (*) to prevent the client access from being rejected by the storage system.</p>
<p id="p336155414598"><a name="p336155414598"></a><a name="p336155414598"></a>If the client host name is used, you are advised to use the full domain name.</p>
<p id="p536119542595"><a name="p536119542595"></a><a name="p536119542595"></a>The IP addresses can be IPv4 addresses, IPv6 addresses, or a combination of IPv4 and IPv6 addresses.</p>
<p id="p636118544595"><a name="p636118544595"></a><a name="p636118544595"></a>You can enter multiple host names, IP addresses, or IP address segments and separate them with semicolons (;). Example: <strong id="b13210718513"><a name="b13210718513"></a><a name="b13210718513"></a>192.168.0.10;192.168.0.0/24;myserver1.test</strong></p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p236119547597"><a name="p236119547597"></a><a name="p236119547597"></a>parameters.authUser</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p63611054195911"><a name="p63611054195911"></a><a name="p63611054195911"></a>DataTurbo user who can access the DataTurbo share. This parameter is mandatory when the <strong id="b10125162717519"><a name="b10125162717519"></a><a name="b10125162717519"></a>DataTurbo(dtfs)</strong> protocol is used.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p11361115415913"><a name="p11361115415913"></a><a name="p11361115415913"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1736175419593"><a name="p1736175419593"></a><a name="p1736175419593"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p136165435918"><a name="p136165435918"></a><a name="p136165435918"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p10361185420590"><a name="p10361185420590"></a><a name="p10361185420590"></a>You can enter multiple DataTurbo users at a time and separate them with semicolons (;). Example: <strong id="b125251474510"><a name="b125251474510"></a><a name="b125251474510"></a>auth_user1;auth_user2;auth_user3</strong></p>
</td>
</tr>
<tr id="row2531173517323"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p15361205411598"><a name="p15361205411598"></a><a name="p15361205411598"></a>parameters.fsPermission</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15361175418593"><a name="p15361175418593"></a><a name="p15361175418593"></a>Permission on the directory mounted to a container.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p23611549592"><a name="p23611549592"></a><a name="p23611549592"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p15361195495910"><a name="p15361195495910"></a><a name="p15361195495910"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p83610540593"><a name="p83610540593"></a><a name="p83610540593"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1836195415918"><a name="p1836195415918"></a><a name="p1836195415918"></a>For details about the configuration format, refer to the Linux permission settings, for example, 777 and 755.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750161119295"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p636195475915"><a name="p636195475915"></a><a name="p636195475915"></a>parameters.rootSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p15361854105912"><a name="p15361854105912"></a><a name="p15361854105912"></a>Controls the <strong id="b1517411210522"><a name="b1517411210522"></a><a name="b1517411210522"></a>root</strong> permission of the client.</p>
<p id="p19361454175914"><a name="p19361454175914"></a><a name="p19361454175914"></a>The value can be:</p>
<a name="ul1736165435912"></a><a name="ul1736165435912"></a><ul id="ul1736165435912"><li><strong id="b1272532011529"><a name="b1272532011529"></a><a name="b1272532011529"></a>root_squash</strong>: The client cannot access the storage system as user <strong id="b12725132085215"><a name="b12725132085215"></a><a name="b12725132085215"></a>root</strong>. If a client accesses the storage system as user <strong id="b1472518205522"><a name="b1472518205522"></a><a name="b1472518205522"></a>root</strong>, the client will be mapped as an anonymous user.</li><li><strong id="b872214342525"><a name="b872214342525"></a><a name="b872214342525"></a>no_root_squash</strong>: A client can access the storage system as user <strong id="b1172220348529"><a name="b1172220348529"></a><a name="b1172220348529"></a>root</strong> and has the permission of user <strong id="b1372203411528"><a name="b1372203411528"></a><a name="b1372203411528"></a>root</strong>.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p436165495914"><a name="p436165495914"></a><a name="p436165495914"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p20361105405917"><a name="p20361105405917"></a><a name="p20361105405917"></a>no_root_squash</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p436115425914"><a name="p436115425914"></a><a name="p436115425914"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row990944017312"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p6361354175916"><a name="p6361354175916"></a><a name="p6361354175916"></a>parameters.allSquash</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p10361054155920"><a name="p10361054155920"></a><a name="p10361054155920"></a>Whether to retain the user ID (UID) and group ID (GID) of a shared directory.</p>
<p id="p13361195410596"><a name="p13361195410596"></a><a name="p13361195410596"></a>The value can be:</p>
<a name="ul736116546593"></a><a name="ul736116546593"></a><ul id="ul736116546593"><li><strong id="b79261248145219"><a name="b79261248145219"></a><a name="b79261248145219"></a>all_squash</strong>: The UID and GID of the shared directory are mapped to anonymous users.</li><li><strong id="b13553511526"><a name="b13553511526"></a><a name="b13553511526"></a>no_all_squash</strong>: The UID and GID of the shared directory are retained.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1636112547597"><a name="p1636112547597"></a><a name="p1636112547597"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1936125495916"><a name="p1936125495916"></a><a name="p1936125495916"></a>no_all_squash</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p63619545598"><a name="p63619545598"></a><a name="p63619545598"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14362135495917"><a name="p14362135495917"></a><a name="p14362135495917"></a>parameters.disableVerifyCapacity</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p636216541599"><a name="p636216541599"></a><a name="p636216541599"></a>Whether to disable volume capacity verification. After this function is disabled, the system will not verify whether the volume capacity is an integer multiple of the sector size.</p>
<p id="p3362145495919"><a name="p3362145495919"></a><a name="p3362145495919"></a>The value can be:</p>
<a name="ul123624548592"></a><a name="ul123624548592"></a><ul id="ul123624548592"><li>"true": disables volume capacity verification.</li><li>"false": enables volume capacity verification.</li></ul>
<div class="notice" id="note03621054175911"><a name="note03621054175911"></a><a name="note03621054175911"></a><span class="noticetitle"> NOTICE: </span><div class="noticebody"><p id="p1836218544599"><a name="p1836218544599"></a><a name="p1836218544599"></a>When Red Hat OpenShift Virtualization is used to connect to CSI, this parameter must be set to <strong id="b5601248185118"><a name="b5601248185118"></a><a name="b5601248185118"></a>"true"</strong>.</p>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p2362054145917"><a name="p2362054145917"></a><a name="p2362054145917"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p63625549594"><a name="p63625549594"></a><a name="p63625549594"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1136295417590"><a name="p1136295417590"></a><a name="p1136295417590"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p13621954105917"><a name="p13621954105917"></a><a name="p13621954105917"></a>For iMaster DME dtrees, the sector size is 1 KB.</p>
</td>
</tr>
</tbody>
</table>

**Table  2**  Common parameters in mountOptions

<a name="table133792080248"></a>
<table><thead align="left"><tr id="row7379880247"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.1"><p id="p736255418592"><a name="p736255418592"></a><a name="p736255418592"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.2"><p id="p1336225415916"><a name="p1336225415916"></a><a name="p1336225415916"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.3"><p id="p15362195417595"><a name="p15362195417595"></a><a name="p15362195417595"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.4"><p id="p2362155419596"><a name="p2362155419596"></a><a name="p2362155419596"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.5"><p id="p16362754175910"><a name="p16362754175910"></a><a name="p16362754175910"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row17379182241"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p162853569513"><a name="p162853569513"></a><a name="p162853569513"></a>mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1928585612516"><a name="p1928585612516"></a><a name="p1928585612516"></a>NFS mount option on the host. The following mount option is supported:</p>
<p id="p328516567514"><a name="p328516567514"></a><a name="p328516567514"></a><strong id="b107122574351"><a name="b107122574351"></a><a name="b107122574351"></a>nfsvers</strong>: protocol version for NFS mounting. The value can be <strong id="b11932161133613"><a name="b11932161133613"></a><a name="b11932161133613"></a>3</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p15285356185114"><a name="p15285356185114"></a><a name="p15285356185114"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p182851756145119"><a name="p182851756145119"></a><a name="p182851756145119"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p228545619510"><a name="p228545619510"></a><a name="p228545619510"></a>This parameter is optional after the <strong id="b457380165105913"><a name="b457380165105913"></a><a name="b457380165105913"></a>-o</strong> parameter when the <strong id="b382391537105913"><a name="b382391537105913"></a><a name="b382391537105913"></a>mount</strong> command is executed on the host. The value is in list format.</p>
<p id="p13285856115110"><a name="p13285856115110"></a><a name="p13285856115110"></a>If the NFS version is specified for mounting, the NFS 3 protocol is supported (the protocol must be supported and enabled on storage devices).</p>
</td>
</tr>
<tr id="row437958102416"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p3371343123317"><a name="p3371343123317"></a><a name="p3371343123317"></a>mountOptions.proto</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p5379432333"><a name="p5379432333"></a><a name="p5379432333"></a>Transmission protocol used for NFS mounting.</p>
<p id="p43784311336"><a name="p43784311336"></a><a name="p43784311336"></a>The value can be <strong id="b880341413545"><a name="b880341413545"></a><a name="b880341413545"></a>rdma</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p637743143311"><a name="p637743143311"></a><a name="p637743143311"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p13371243193313"><a name="p13371243193313"></a><a name="p13371243193313"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row3379182244"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p183744319338"><a name="p183744319338"></a><a name="p183744319338"></a>mountOptions.port</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p1237943163315"><a name="p1237943163315"></a><a name="p1237943163315"></a>Protocol port used for NFS mounting.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p19371043103315"><a name="p19371043103315"></a><a name="p19371043103315"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p143774323313"><a name="p143774323313"></a><a name="p143774323313"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p13371743113311"><a name="p13371743113311"></a><a name="p13371743113311"></a>If the transmission protocol is <strong id="b6563926125417"><a name="b6563926125417"></a><a name="b6563926125417"></a>rdma</strong>, set this parameter to <strong id="b456312267549"><a name="b456312267549"></a><a name="b456312267549"></a>20049</strong>.</p>
</td>
</tr>
<tr id="row937988202418"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.1 "><p id="p63621054105914"><a name="p63621054105914"></a><a name="p63621054105914"></a>mountOptions.dn</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.2 "><p id="p236215411596"><a name="p236215411596"></a><a name="p236215411596"></a>Domain name of the logical port used for mounting when the <strong id="b4884331548"><a name="b4884331548"></a><a name="b4884331548"></a>DataTurbo(dtfs)</strong> protocol is used.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p123626548593"><a name="p123626548593"></a><a name="p123626548593"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p2036235420592"><a name="p2036235420592"></a><a name="p2036235420592"></a>WWN of a storage device.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p153621754155919"><a name="p153621754155919"></a><a name="p153621754155919"></a>To mount the HyperScale cluster file system, enter the domain name of the HyperScale cluster.</p>
<p id="p1136210542597"><a name="p1136210542597"></a><a name="p1136210542597"></a>The description of the <strong id="b14902115065413"><a name="b14902115065413"></a><a name="b14902115065413"></a>dn</strong> parameter is for reference only. For details about other mounting parameters of the DataTurbo protocol, see <a href="https://support.huawei.com/enterprise/en/doc/EDOC1100539414/a8d5b478/mounting-a-file-system?idPath=7919749|251366268|250389224|263153904|264568316" target="_blank" rel="noopener noreferrer">AI Storage Kit 25.x.x DTFS User Guide</a>.</p>
</td>
</tr>
</tbody>
</table>

