---
title: "Managing PVs"
linkTitle: "Managing PVs"
description: 
weight: 3
---

Manage Volume Provisioning allows administrators to use resources created on storage as PVs and supports features of dynamic volumes, such as capacity expansion, snapshot, and clone. This is a custom capability of Huawei CSI. This feature applies to the following scenarios:

-   In the reconstruction containerized applications, existing storage volumes need to be used.
-   The Kubernetes cluster is rebuilt.
-   Storage data is migrated in disaster recovery \(DR\) scenarios.

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>Manage Volume Provisioning allows existing storage resources to be managed by Kubernetes. You are not allowed to manage a storage resource for multiple times and concurrently delete or create a storage resource.
>When a storage resource is managed by multiple clusters, operations on the managed volume in a single cluster take effect only in the cluster and will not be synchronized to other clusters. Instead, you need to perform these operations on the managed volume in other clusters.
>For example, when you expand the capacity of a PVC in a cluster, the capacity of the corresponding PVC in other clusters will not be automatically expanded. In this case, you need to manually expand the capacity in other clusters by running the expansion commands in  [Expanding the Capacity of a PV](/docs/basic-services/persistent-volume-management/managing-pvs-73/expanding-the-capacity-of-a-pv).

## Configuration Description{#section121779524353}

Perform the following steps to manage and use PVs:

-   [Preparation](#section65071656132313)
-   [Configuring a PVC](#section979723473817)
-   [Using a PVC](#section847932614377)

## Preparation{#section65071656132313}

-   You have registered the storage where the volume to be managed resides with CSI.
-   You have logged in to the storage device to obtain the name and capacity of the volume to be managed.
-   The StorageClass has been configured. For details, see  [Configuring a StorageClass](/docs/basic-services/storageclass-management/configuring-a-storageclass)  \(pay attention to the  **Whether the Volume Management Takes Effect**  field in the table\).

## Configuring a PVC{#section979723473817}

1.  Prepare the PVC configuration file  **mypv.yaml**. The following is an example. For details about other parameters, see  [Table 1](#en-us_topic_0150885187_table195731435604).

    ```yaml
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: mypvc
      annotations:
        csi.huawei.com/manageVolumeName: "*"  # Enter the storage resource name.
        csi.huawei.com/manageBackendName: "*" # Enter the storage backend name.
      labels:
        provisioner: csi.huawei.com
    spec:
      accessModes:
        - ReadWriteOnce
      volumeMode: Filesystem
      storageClassName: mysc
      resources:
        requests:
          storage: 100Gi
    ```

2.  Run the following command to create a PVC using the configuration file.

    ```
    kubectl create -f mypvc.yaml
    ```

3.  After a period of time, run the following command to view the information about the created PVC.

    ```
    kubectl get pvc mypvc
    ```

    The following is an example of the command output. If the PVC status is  **Bound**, the PVC has been created and can be used by a Pod.

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO            mysc           12s
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
    >-   After the PVC is created, if the PVC is in the  **Pending**  state after a long time \(for example, one minute\), refer to  [When a PVC Is Created, the PVC Is in the Pending State](/docs/troubleshooting/pvc-issues/when-a-pvc-is-created-the-pvc-is-in-the-pending-state).
    >-   You are advised to create or delete a maximum of 100 PVCs in a batch.

**Table  1**  PVC parameters for managing PVs

<a name="en-us_topic_0150885187_table195731435604"></a>
<table><thead align="left"><tr id="en-us_topic_0150885187_row35732351904"><th class="cellrowborder" valign="top" width="13.47134713471347%" id="mcps1.2.6.1.1"><p id="en-us_topic_0150885187_p1257333517017"><a name="en-us_topic_0150885187_p1257333517017"></a><a name="en-us_topic_0150885187_p1257333517017"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.852685268526855%" id="mcps1.2.6.1.2"><p id="en-us_topic_0150885187_p1457323512015"><a name="en-us_topic_0150885187_p1457323512015"></a><a name="en-us_topic_0150885187_p1457323512015"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="5.15051505150515%" id="mcps1.2.6.1.3"><p id="p19360047916"><a name="p19360047916"></a><a name="p19360047916"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="26.62266226622662%" id="mcps1.2.6.1.4"><p id="p9506371793"><a name="p9506371793"></a><a name="p9506371793"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="27.902790279027904%" id="mcps1.2.6.1.5"><p id="en-us_topic_0150885187_p85734352017"><a name="en-us_topic_0150885187_p85734352017"></a><a name="en-us_topic_0150885187_p85734352017"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row969014592044"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="p2690115912418"><a name="p2690115912418"></a><a name="p2690115912418"></a>metadata.annotations</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="p196189175512"><a name="p196189175512"></a><a name="p196189175512"></a>PVC object annotations. Set the following parameters:</p>
<a name="ul411121811565"></a><a name="ul411121811565"></a><ul id="ul411121811565"><li><em id="i16524101175216"><a name="i16524101175216"></a><a name="i16524101175216"></a>Driver name</em><strong id="b639125865111"><a name="b639125865111"></a><a name="b639125865111"></a>/manageVolumeName</strong>: volume name on the storage.</li><li><em id="i8140827145213"><a name="i8140827145213"></a><a name="i8140827145213"></a>Driver name</em><strong id="b4202142255215"><a name="b4202142255215"></a><a name="b4202142255215"></a>/manageBackendName</strong>: name of the backend to which the volume belongs.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p15360547910"><a name="p15360547910"></a><a name="p15360547910"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p8502191171218"><a name="p8502191171218"></a><a name="p8502191171218"></a>csi.huawei.com/manageVolumeName: *    csi.huawei.com/manageBackendName: *</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><a name="ul44235513567"></a><a name="ul44235513567"></a><ul id="ul44235513567"><li>For details about how to obtain <em id="i1022933811207"><a name="i1022933811207"></a><a name="i1022933811207"></a>Driver name</em>, see <a href="/css-docs/en/docs/installation-and-deployment/csi/installation/installation-using-helm/parameters-in-the-values-yaml-file-of-helm#table188162213437">Table 4</a>.</li><li><em id="i799016017533"><a name="i799016017533"></a><a name="i799016017533"></a>Driver name</em><strong id="b416055065219"><a name="b416055065219"></a><a name="b416055065219"></a>/manageVolumeName</strong>: name of an existing volume on the storage. Only English characters are supported.</li><li><em id="i1845622011537"><a name="i1845622011537"></a><a name="i1845622011537"></a>Driver name</em><strong id="b1795814159531"><a name="b1795814159531"></a><a name="b1795814159531"></a>/manageBackendName</strong>: name of the storage backend in CSI.</li></ul>
<p id="p176901459748"><a name="p176901459748"></a><a name="p176901459748"></a>You can run the <strong id="b128931112571"><a name="b128931112571"></a><a name="b128931112571"></a>oceanctl get backend -n huawei-csi</strong> command to obtain the backend name.</p>
</td>
</tr>
<tr id="row13644161649"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="p7644961942"><a name="p7644961942"></a><a name="p7644961942"></a>metadata.labels</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="p364436542"><a name="p364436542"></a><a name="p364436542"></a>PVC object labels.</p>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p3360941498"><a name="p3360941498"></a><a name="p3360941498"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p10506117498"><a name="p10506117498"></a><a name="p10506117498"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p168401138144212"><a name="p168401138144212"></a><a name="p168401138144212"></a>Format: <strong id="b3174194985317"><a name="b3174194985317"></a><a name="b3174194985317"></a>provisioner: </strong><em id="i1052635375316"><a name="i1052635375316"></a><a name="i1052635375316"></a>Driver name specified during installation</em></p>
<p id="p1067565015410"><a name="p1067565015410"></a><a name="p1067565015410"></a>Example: <strong id="b332927135419"><a name="b332927135419"></a><a name="b332927135419"></a>provisioner: csi.huawei.com</strong></p>
<p id="p19806312144118"><a name="p19806312144118"></a><a name="p19806312144118"></a>This parameter takes effect when a PVC is created. It is used to listen to PVC resources and obtain information about <strong id="b592498145411"><a name="b592498145411"></a><a name="b592498145411"></a>metadata.annotations</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row5573635907"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p3573335305"><a name="en-us_topic_0150885187_p3573335305"></a><a name="en-us_topic_0150885187_p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p205736355017"><a name="en-us_topic_0150885187_p205736355017"></a><a name="en-us_topic_0150885187_p205736355017"></a>User-defined name of a PVC object.</p>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p1736019415915"><a name="p1736019415915"></a><a name="p1736019415915"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p1506677916"><a name="p1506677916"></a><a name="p1506677916"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p20875193814315"><a name="p20875193814315"></a><a name="p20875193814315"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row696316316238"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p1896393118231"><a name="en-us_topic_0150885187_p1896393118231"></a><a name="en-us_topic_0150885187_p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="p1610614478451"><a name="p1610614478451"></a><a name="p1610614478451"></a>Volume mode. This parameter is optional. When LUN volumes are used, the following types are supported:</p>
<a name="ul823916101324"></a><a name="ul823916101324"></a><ul id="ul823916101324"><li><strong id="b899015017514"><a name="b899015017514"></a><a name="b899015017514"></a>Filesystem</strong>: local file system.</li><li><strong id="b14568105754"><a name="b14568105754"></a><a name="b14568105754"></a>Block</strong>: raw device.</li></ul>
<div class="note" id="note186041413175913"><a name="note186041413175913"></a><a name="note186041413175913"></a><span class="notetitle"> NOTE: </span><div class="notebody"><p id="p156042013105912"><a name="p156042013105912"></a><a name="p156042013105912"></a>This parameter takes effect when a PV is mounted. The use method of this parameter must be the same as that of the managed volume.</p>
<a name="ul10185528135916"></a><a name="ul10185528135916"></a><ul id="ul10185528135916"><li>If a volume is used as a raw volume before being managed, <strong id="b083117492061"><a name="b083117492061"></a><a name="b083117492061"></a>volumeMode</strong> must be set to <strong id="b1299511501666"><a name="b1299511501666"></a><a name="b1299511501666"></a>Block</strong>.</li><li>If a volume is used in ext2, ext3, or ext4 mode before being managed, <strong id="b144846311720"><a name="b144846311720"></a><a name="b144846311720"></a>volumeMode</strong> must be set to <strong id="b18438165674"><a name="b18438165674"></a><a name="b18438165674"></a>Filesystem</strong> and <strong id="b1687191020713"><a name="b1687191020713"></a><a name="b1687191020713"></a>fsType</strong> in the StorageClass must be set to <strong id="b16268213978"><a name="b16268213978"></a><a name="b16268213978"></a>ext2</strong>, <strong id="b1754251419713"><a name="b1754251419713"></a><a name="b1754251419713"></a>ext3</strong>, or <strong id="b1865616151174"><a name="b1865616151174"></a><a name="b1865616151174"></a>ext4</strong>.</li><li>If a volume is used in XFS mode before being managed, <strong id="b1249719171275"><a name="b1249719171275"></a><a name="b1249719171275"></a>volumeMode</strong> must be set to <strong id="b1549818171871"><a name="b1549818171871"></a><a name="b1549818171871"></a>Filesystem</strong> and <strong id="b154998177720"><a name="b154998177720"></a><a name="b154998177720"></a>fsType</strong> in the StorageClass must be set to <strong id="b550016177718"><a name="b550016177718"></a><a name="b550016177718"></a>xfs</strong>.</li></ul>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p153606414917"><a name="p153606414917"></a><a name="p153606414917"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p55061271915"><a name="p55061271915"></a><a name="p55061271915"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p62045214421"><a name="p62045214421"></a><a name="p62045214421"></a>This parameter takes effect when a PV is mounted.</p>
<a name="ul1518211174214"></a><a name="ul1518211174214"></a><ul id="ul1518211174214"><li><strong id="b56361018254"><a name="b56361018254"></a><a name="b56361018254"></a>Filesystem</strong> indicates that a container accesses a PV using a local file system. The local file system type is specified by the <strong id="b127897508512"><a name="b127897508512"></a><a name="b127897508512"></a>fsType</strong> field in the specified StorageClass.</li><li><strong id="b131506591954"><a name="b131506591954"></a><a name="b131506591954"></a>Block</strong> indicates that a PV is accessed in raw volume mode.</li></ul>
</td>
</tr>
<tr id="en-us_topic_0150885187_row25733352019"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p357320351304"><a name="en-us_topic_0150885187_p357320351304"></a><a name="en-us_topic_0150885187_p357320351304"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p135732351909"><a name="en-us_topic_0150885187_p135732351909"></a><a name="en-us_topic_0150885187_p135732351909"></a>Name of the StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p1736015413918"><a name="p1736015413918"></a><a name="p1736015413918"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p195061171092"><a name="p195061171092"></a><a name="p195061171092"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p1521791621216"><a name="p1521791621216"></a><a name="p1521791621216"></a>The configuration of the StorageClass must be the same as that of the managed volume.</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row1157316351102"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p9573035309"><a name="en-us_topic_0150885187_p9573035309"></a><a name="en-us_topic_0150885187_p9573035309"></a>spec.resources.requests.storage</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p1573183510015"><a name="en-us_topic_0150885187_p1573183510015"></a><a name="en-us_topic_0150885187_p1573183510015"></a>Size of the volume to be created. The format is ***Gi and the unit is GiB.</p>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p1436044990"><a name="p1436044990"></a><a name="p1436044990"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p18506147494"><a name="p18506147494"></a><a name="p18506147494"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p1525217519276"><a name="p1525217519276"></a><a name="p1525217519276"></a>The PVC capacity depends on storage specifications and host specifications. For example, OceanStor Dorado 6.1.2 or OceanStor Pacific series 8.1.0 is connected to CentOS 7. If ext4 file systems are used, see <a href="/css-docs/en/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#en-us_topic_0150885187_table178824527142">Table 2</a>. If XFS file systems are used, see <a href="/css-docs/en/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#en-us_topic_0150885187_table101951367104">Table 3</a>. If NFS or raw devices are used, the capacity must meet the specifications of the used Huawei storage device model and version.</p>
<p id="p63667162711"><a name="p63667162711"></a><a name="p63667162711"></a>If the PVC capacity does not meet the specifications, a PVC or Pod may fail to be created due to the limitations of storage specifications or host file system specifications.</p>
</td>
</tr>
<tr id="en-us_topic_0150885187_row6573635502"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p1657333515012"><a name="en-us_topic_0150885187_p1657333515012"></a><a name="en-us_topic_0150885187_p1657333515012"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="p51122302293"><a name="p51122302293"></a><a name="p51122302293"></a>Access mode of the volume.</p>
<a name="ul69743301323"></a><a name="ul69743301323"></a><ul id="ul69743301323"><li><strong id="b1777118191889"><a name="b1777118191889"></a><a name="b1777118191889"></a>RWO</strong> (ReadWriteOnce): A volume can be mounted to a node in read/write mode. This mode also allows multiple Pods running on the same node to access the volume.</li><li><strong id="b143841840999"><a name="b143841840999"></a><a name="b143841840999"></a>ROX</strong> (ReadOnlyMany): A volume can be mounted to multiple nodes in read-only mode.</li><li><strong id="b184245131017"><a name="b184245131017"></a><a name="b184245131017"></a>RWX</strong> (ReadWriteMany): A volume can be mounted to multiple nodes in read/write mode.</li><li><strong id="b14167203017109"><a name="b14167203017109"></a><a name="b14167203017109"></a>RWOP</strong> (ReadWriteOncePod): A volume can only be mounted to a single Pod in read/write mode. Kubernetes 1.22 and later versions support this feature.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p10360448912"><a name="p10360448912"></a><a name="p10360448912"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p65069712920"><a name="p65069712920"></a><a name="p65069712920"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><a name="ul16793434324"></a><a name="ul16793434324"></a><ul id="ul16793434324"><li>RWO/ROX/RWOP: supported by all types of volumes. RWOP is supported only by Kubernetes 1.22 and later versions. For versions earlier than Kubernetes 1.29, you need to enable this feature by following the instructions in <a href="/css-docs/en/docs/common-o-m-operations/enabling-the-readwriteoncepod-feature-gate">Enabling the ReadWriteOncePod Feature Gate</a>.</li><li>The support for RWX is as follows:<a name="ul10813936394"></a><a name="ul10813936394"></a><ul id="ul10813936394"><li>NAS storage: supported by all volumes</li><li>SAN storage: supported only by volumes whose <strong id="b21958219054026"><a name="b21958219054026"></a><a name="b21958219054026"></a>volumeMode</strong> is set to <strong id="b127928885754026"><a name="b127928885754026"></a><a name="b127928885754026"></a>Block</strong></li></ul>
</li></ul>
</td>
</tr>
</tbody>
</table>

## Using a PVC{#section847932614377}

The procedure is the same as that for  [Using a PVC](/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#section8172141413917)  for dynamic volume provisioning.

