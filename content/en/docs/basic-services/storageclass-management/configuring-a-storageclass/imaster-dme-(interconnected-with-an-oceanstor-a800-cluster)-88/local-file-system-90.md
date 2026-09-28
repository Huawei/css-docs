---
title: "Local File System"
linkTitle: "Local File System"
description: 
weight: 2
---

## Creating a StorageClass{#section4456164612616}

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

## KV Cache Configuration Example{#section1826982521216}

If the container uses KV cache to connect to the iMaster DME local file system and the storage system supports KV cache, refer to the following configuration example.

```yaml
kind: StorageClass
apiVersion: storage.k8s.io/v1
metadata:
  name: kvcache-nas-sc
provisioner: csi.huawei.com
reclaimPolicy: Delete
parameters:
  backend: dme-a800-backend
  pool: StoragePool001
  zoneVstoreName: System_vstore
  volumeType: fs
  enableKVCache: "true"
  enableTimeAwareGc: "true"
  gcTimeThreshold: "30"
  disableVerifyCapacity: "true"
mountOptions:
  - nfsvers=3 # Specify the version 3 for NFS mounting.
```

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
<tbody><tr id="en-us_topic_0000001162111564_row1575014112294"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p7351266291"><a name="p7351266291"></a><a name="p7351266291"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p5351186152912"><a name="p5351186152912"></a><a name="p5351186152912"></a>User-defined name of a StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1135114692910"><a name="p1135114692910"></a><a name="p1135114692910"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p15351176122912"><a name="p15351176122912"></a><a name="p15351176122912"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1135136112914"><a name="p1135136112914"></a><a name="p1135136112914"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p193511568294"><a name="p193511568294"></a><a name="p193511568294"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row77501711142917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p2351136152918"><a name="p2351136152918"></a><a name="p2351136152918"></a>provisioner</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p6351465291"><a name="p6351465291"></a><a name="p6351465291"></a>Name of the provisioner.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1435186202914"><a name="p1435186202914"></a><a name="p1435186202914"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p8351465293"><a name="p8351465293"></a><a name="p8351465293"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1035117620294"><a name="p1035117620294"></a><a name="p1035117620294"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p13511632912"><a name="p13511632912"></a><a name="p13511632912"></a>Set this parameter to the driver name set during Huawei CSI installation. The value is the same as that of <strong id="b7600142710419"><a name="b7600142710419"></a><a name="b7600142710419"></a>driverName</strong> in the <strong id="b20600182720411"><a name="b20600182720411"></a><a name="b20600182720411"></a>values.yaml</strong> file.</p>
</td>
</tr>
<tr id="row1290925314317"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p163519610297"><a name="p163519610297"></a><a name="p163519610297"></a>reclaimPolicy</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p73511060291"><a name="p73511060291"></a><a name="p73511060291"></a>Reclamation policy. The following types are supported: <strong id="b1366312592063"><a name="b1366312592063"></a><a name="b1366312592063"></a>Delete:</strong> Resources are automatically reclaimed. <strong id="b167626416719"><a name="b167626416719"></a><a name="b167626416719"></a>Retain</strong>: Resources are manually reclaimed.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p16351866298"><a name="p16351866298"></a><a name="p16351866298"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p43515622918"><a name="p43515622918"></a><a name="p43515622918"></a>Delete</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1735111622915"><a name="p1735111622915"></a><a name="p1735111622915"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p7351126132915"><a name="p7351126132915"></a><a name="p7351126132915"></a><strong id="b1798910203713"><a name="b1798910203713"></a><a name="b1798910203713"></a>Delete</strong>: When a PV/PVC is deleted, resources on the storage device are also deleted. <strong id="b1990033711817"><a name="b1990033711817"></a><a name="b1990033711817"></a>Retain</strong>: When a PV/PVC is deleted, resources on the storage device are not deleted. Note: When a KV cache resource is deleted, the file system share is also deleted.</p>
</td>
</tr>
<tr id="row0276132116506"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p635186112917"><a name="p635186112917"></a><a name="p635186112917"></a>allowVolumeExpansion</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p83519614299"><a name="p83519614299"></a><a name="p83519614299"></a>Whether to allow volume expansion. If this parameter is set to <strong id="b3776617398"><a name="b3776617398"></a><a name="b3776617398"></a>true</strong>, the capacity of the PV that uses the StorageClass can be expanded.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p235115672910"><a name="p235115672910"></a><a name="p235115672910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1135196102918"><a name="p1135196102918"></a><a name="p1135196102918"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p73513642910"><a name="p73513642910"></a><a name="p73513642910"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p12351769299"><a name="p12351769299"></a><a name="p12351769299"></a>This function can only be used to expand PV capacity but cannot be used to reduce PV capacity.</p>
</td>
</tr>
<tr id="row63343268297"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1635176112913"><a name="p1635176112913"></a><a name="p1635176112913"></a>mountOptions</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p135113610291"><a name="p135113610291"></a><a name="p135113610291"></a>List of mount parameters, which can be used to specify the parameters of the <strong id="b1210742693"><a name="b1210742693"></a><a name="b1210742693"></a>-o</strong> option when the <strong id="b161044211919"><a name="b161044211919"></a><a name="b161044211919"></a>mount</strong> command is executed on a host.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1435114612910"><a name="p1435114612910"></a><a name="p1435114612910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p635119610294"><a name="p635119610294"></a><a name="p635119610294"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p103515672915"><a name="p103515672915"></a><a name="p103515672915"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1936045445914"><a name="p1936045445914"></a><a name="p1936045445914"></a>For details about common parameters in <strong id="b7171828204018"><a name="b7171828204018"></a><a name="b7171828204018"></a>mountOptions</strong>, see <a href="#table65545557506">Table 2</a>.</p>
<p id="p14360854175917"><a name="p14360854175917"></a><a name="p14360854175917"></a>You can also specify other mount parameters.</p>
</td>
</tr>
<tr id="row172016531531"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p17351061291"><a name="p17351061291"></a><a name="p17351061291"></a>parameters.backend</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p835114612912"><a name="p835114612912"></a><a name="p835114612912"></a>Name of the backend where the resource to be created is located. This field must be set if <strong id="b267111312116"><a name="b267111312116"></a><a name="b267111312116"></a>parameters.pool</strong> is set.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p135220682919"><a name="p135220682919"></a><a name="p135220682919"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p535216642917"><a name="p535216642917"></a><a name="p535216642917"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p835246142911"><a name="p835246142911"></a><a name="p835246142911"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1635216192917"><a name="p1635216192917"></a><a name="p1635216192917"></a>When creating a KV cache in the local file system of iMaster DME, you need to specify the backend to be used.</p>
</td>
</tr>
<tr id="row1995791713711"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p1735296182915"><a name="p1735296182915"></a><a name="p1735296182915"></a>parameters.pool</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1235214611293"><a name="p1235214611293"></a><a name="p1235214611293"></a>Name of the storage resource pool where the resource to be created is located.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p335215602910"><a name="p335215602910"></a><a name="p335215602910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p635206172918"><a name="p635206172918"></a><a name="p635206172918"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p535246162914"><a name="p535246162914"></a><a name="p535246162914"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p133521965295"><a name="p133521965295"></a><a name="p133521965295"></a>If this parameter is not set, Huawei CSI will select a storage pool with the largest remaining capacity from the selected backend to create resources. You are advised to specify a storage pool to ensure that the created resource is located in the expected storage pool.</p>
</td>
</tr>
<tr id="row12968565337"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p148909442443"><a name="p148909442443"></a><a name="p148909442443"></a>parameters.zoneVstoreName</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p8890244174410"><a name="p8890244174410"></a><a name="p8890244174410"></a>vStore name of the storage device.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p138909443445"><a name="p138909443445"></a><a name="p138909443445"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p9890154416446"><a name="p9890154416446"></a><a name="p9890154416446"></a>System_vStore</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p849004934413"><a name="p849004934413"></a><a name="p849004934413"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p166922509449"><a name="p166922509449"></a><a name="p166922509449"></a>This parameter is valid only when a zone SN is specified. On the iMaster DME, choose <strong id="b16445011163810"><a name="b16445011163810"></a><a name="b16445011163810"></a>Infrastructure</strong> &gt; <strong id="b3164101520381"><a name="b3164101520381"></a><a name="b3164101520381"></a>Storage Devices</strong> &gt; <strong id="b20269102311381"><a name="b20269102311381"></a><a name="b20269102311381"></a>System</strong> &gt; <strong id="b1070103012414"><a name="b1070103012414"></a><a name="b1070103012414"></a>vStores</strong>. Obtain the name of a non-global vStore in the corresponding zone.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row18750151182917"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p203528613295"><a name="p203528613295"></a><a name="p203528613295"></a>parameters.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p035210642914"><a name="p035210642914"></a><a name="p035210642914"></a>Name of the storage resource created by dynamic volume provisioning. You can configure a placeholder to customize the storage resource name. The following placeholders are supported: PVC namespace: <em id="i1675875811516"><a name="i1675875811516"></a><a name="i1675875811516"></a>{{ .PVCNamespace }}</em>; PVC name: <em id="i134911325213"><a name="i134911325213"></a><a name="i134911325213"></a>{{ .PVCName }}</em></p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p113526662911"><a name="p113526662911"></a><a name="p113526662911"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p43524612299"><a name="p43524612299"></a><a name="p43524612299"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p7352106142918"><a name="p7352106142918"></a><a name="p7352106142918"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p03524662910"><a name="p03524662910"></a><a name="p03524662910"></a>The value can contain letters, digits, underscores (_), and hyphens (-). It cannot be left empty. The name length of the generated storage resource ranges from 1 to 255 characters. Both the PVC namespace and PVC name must be configured. To avoid duplicate resource names, the PVC UID is added to the end of the name as a unique identifier by default.</p>
</td>
</tr>
<tr id="en-us_topic_0000001162111564_row15750171172918"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p11856152785018"><a name="p11856152785018"></a><a name="p11856152785018"></a>parameters.volumeType</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p198561027135014"><a name="p198561027135014"></a><a name="p198561027135014"></a>Type of the volume to be created. The following types are supported:</p>
<a name="ul8856102725020"></a><a name="ul8856102725020"></a><ul id="ul8856102725020"><li><strong id="b6902909531"><a name="b6902909531"></a><a name="b6902909531"></a>lun</strong>: A LUN is provisioned on the storage side.</li><li><strong id="b62244435313"><a name="b62244435313"></a><a name="b62244435313"></a>fs</strong>: A file system is provisioned on the storage side.</li><li><strong id="b310191295317"><a name="b310191295317"></a><a name="b310191295317"></a>dtree</strong>: A volume of the dtree type is provisioned on the storage side.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p14856327155015"><a name="p14856327155015"></a><a name="p14856327155015"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p19856627135013"><a name="p19856627135013"></a><a name="p19856627135013"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p1785612755013"><a name="p1785612755013"></a><a name="p1785612755013"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p208561927135012"><a name="p208561927135012"></a><a name="p208561927135012"></a>To use the file service, you must set this parameter to <strong id="b2471321115320"><a name="b2471321115320"></a><a name="b2471321115320"></a>fs</strong>.</p>
</td>
</tr>
<tr id="row89405211470"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p14352176102917"><a name="p14352176102917"></a><a name="p14352176102917"></a>parameters.disableVerifyCapacity</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p135216662913"><a name="p135216662913"></a><a name="p135216662913"></a>Whether to disable volume capacity verification. After this function is disabled, the system will not verify whether the volume capacity is an integer multiple of the sector size. The value can be <strong id="b154041546115315"><a name="b154041546115315"></a><a name="b154041546115315"></a>"true"</strong> (disables volume capacity verification) or <strong id="b13997174915311"><a name="b13997174915311"></a><a name="b13997174915311"></a>"false"</strong> (enables volume capacity verification). When Red Hat OpenShift Virtualization is used to connect to CSI, this parameter must be set to <strong id="b77161958155314"><a name="b77161958155314"></a><a name="b77161958155314"></a>"true"</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p235211611296"><a name="p235211611296"></a><a name="p235211611296"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p133524615295"><a name="p133524615295"></a><a name="p133524615295"></a>"true"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p10352116142916"><a name="p10352116142916"></a><a name="p10352116142916"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p10352069295"><a name="p10352069295"></a><a name="p10352069295"></a>The sector size of OceanStor A series is 512 bytes.</p>
</td>
</tr>
<tr id="row2531173517323"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p235216692919"><a name="p235216692919"></a><a name="p235216692919"></a>parameters.description</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p1235256112912"><a name="p1235256112912"></a><a name="p1235256112912"></a>Description of the file system to be created. Value type: string; length limit: 1 to 255 characters.</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p53524613294"><a name="p53524613294"></a><a name="p53524613294"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p12352868299"><a name="p12352868299"></a><a name="p12352868299"></a>Created from Kubernetes CSI</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p133526622919"><a name="p133526622919"></a><a name="p133526622919"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 ">&nbsp;&nbsp;</td>
</tr>
<tr id="row19718344103110"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p12352565293"><a name="p12352565293"></a><a name="p12352565293"></a>parameters.enableKVCache</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p035211611294"><a name="p035211611294"></a><a name="p035211611294"></a>Whether to create a KV cache store. The options include <strong id="b1463294920545"><a name="b1463294920545"></a><a name="b1463294920545"></a>"false"</strong> (disabled) and <strong id="b463254955411"><a name="b463254955411"></a><a name="b463254955411"></a>"true"</strong> (enabled).</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p535219620294"><a name="p535219620294"></a><a name="p535219620294"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p1935296122916"><a name="p1935296122916"></a><a name="p1935296122916"></a>"false"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p835217614298"><a name="p835217614298"></a><a name="p835217614298"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p1035216122919"><a name="p1035216122919"></a><a name="p1035216122919"></a>This parameter must be set to <strong id="b32912221554"><a name="b32912221554"></a><a name="b32912221554"></a>true</strong> when a single-zone resource is created in the current scenario.</p>
</td>
</tr>
<tr id="row751831445010"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p235212642913"><a name="p235212642913"></a><a name="p235212642913"></a>parameters.enableTimeAwareGc</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p11352965293"><a name="p11352965293"></a><a name="p11352965293"></a>Whether to enable proactive clearing for a KV cache. The options include <strong id="b858184116567"><a name="b858184116567"></a><a name="b858184116567"></a>"false"</strong> (disabled) and <strong id="b2058134113569"><a name="b2058134113569"></a><a name="b2058134113569"></a>"true"</strong> (enabled).</p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p4353361292"><a name="p4353361292"></a><a name="p4353361292"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p18353156162913"><a name="p18353156162913"></a><a name="p18353156162913"></a>"false"</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p335356122917"><a name="p335356122917"></a><a name="p335356122917"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p335316672919"><a name="p335316672919"></a><a name="p335316672919"></a>No matter whether this parameter is set to <strong id="b313674716566"><a name="b313674716566"></a><a name="b313674716566"></a>"true"</strong> or <strong id="b01365479566"><a name="b01365479566"></a><a name="b01365479566"></a>"false"</strong>, the background clears the KV cache when the memory store capacity is insufficient. When this parameter is set to <strong id="b13136144725619"><a name="b13136144725619"></a><a name="b13136144725619"></a>"true"</strong>, the background clears the expired KV cache.</p>
</td>
</tr>
<tr id="row1199202362211"><td class="cellrowborder" valign="top" width="18.481557577536446%" headers="mcps1.2.7.1.1 "><p id="p8353966294"><a name="p8353966294"></a><a name="p8353966294"></a>parameters.gcTimeThreshold</p>
</td>
<td class="cellrowborder" valign="top" width="23.089717248801485%" headers="mcps1.2.7.1.2 "><p id="p83531160297"><a name="p83531160297"></a><a name="p83531160297"></a>KV cache expiration time. The value ranges from 1 to 3650 days. Example: <strong id="b16708162205712"><a name="b16708162205712"></a><a name="b16708162205712"></a>1</strong></p>
</td>
<td class="cellrowborder" valign="top" width="6.848644946678408%" headers="mcps1.2.7.1.3 "><p id="p1353166132913"><a name="p1353166132913"></a><a name="p1353166132913"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="8.453184619900206%" headers="mcps1.2.7.1.4 "><p id="p183533615290"><a name="p183533615290"></a><a name="p183533615290"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="7.35740142843166%" headers="mcps1.2.7.1.5 "><p id="p17353156172910"><a name="p17353156172910"></a><a name="p17353156172910"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="35.7694941786518%" headers="mcps1.2.7.1.6 "><p id="p113530692915"><a name="p113530692915"></a><a name="p113530692915"></a>This parameter is mandatory when <strong id="b16331511195714"><a name="b16331511195714"></a><a name="b16331511195714"></a>parameters.enableTimeAwareGc</strong> is set to <strong id="b333411195714"><a name="b333411195714"></a><a name="b333411195714"></a>"true"</strong>.</p>
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
<p id="p328516567514"><a name="p328516567514"></a><a name="p328516567514"></a><strong id="b1834394395814"><a name="b1834394395814"></a><a name="b1834394395814"></a>nfsvers</strong>: protocol version for NFS mounting. The value can be <strong id="b7469485403"><a name="b7469485403"></a><a name="b7469485403"></a>3</strong>, <strong id="b11461148104012"><a name="b11461148104012"></a><a name="b11461148104012"></a>4</strong>, <strong id="b74624818405"><a name="b74624818405"></a><a name="b74624818405"></a>4.0</strong>, <strong id="b24715486407"><a name="b24715486407"></a><a name="b24715486407"></a>4.1</strong>, or <strong id="b1947348174011"><a name="b1947348174011"></a><a name="b1947348174011"></a>4.2</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.3 "><p id="p15285356185114"><a name="p15285356185114"></a><a name="p15285356185114"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.4 "><p id="p182851756145119"><a name="p182851756145119"></a><a name="p182851756145119"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p228545619510"><a name="p228545619510"></a><a name="p228545619510"></a>This parameter is optional after the <strong id="b109717571585"><a name="b109717571585"></a><a name="b109717571585"></a>-o</strong> parameter when the <strong id="b397175765816"><a name="b397175765816"></a><a name="b397175765816"></a>mount</strong> command is executed on the host. The value is in list format.</p>
<p id="p13285856115110"><a name="p13285856115110"></a><a name="p13285856115110"></a>If the NFS version is specified for mounting, NFS 3, 4.0, 4.1, and 4.2 protocols are supported (the protocol must be supported and enabled on storage devices). If <strong id="b411541013411"><a name="b411541013411"></a><a name="b411541013411"></a>nfsvers</strong> is set to <strong id="b17115131044115"><a name="b17115131044115"></a><a name="b17115131044115"></a>4</strong>, the latest protocol version NFS 4 may be used for mounting due to different OS configurations, for example, 4.2. If the 4.0 protocol is required, you are advised to set <strong id="b8116131017415"><a name="b8116131017415"></a><a name="b8116131017415"></a>nfsvers</strong> to <strong id="b811731024111"><a name="b811731024111"></a><a name="b811731024111"></a>4.0</strong>.</p>
</td>
</tr>
</tbody>
</table>

