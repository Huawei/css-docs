---
title: "Configuring a Static PV"
linkTitle: "Configuring a Static PV"
description: 
weight: 2
---

Static volume provisioning allows administrators to use a resource created on the storage side as a PV for containers in the cluster.

## Configuration Description{#section1426372873615}

Perform the following steps to configure a static PV:

-   [Preparation](#section4107171112475)
-   [Configuring a PV](#section651114483616)
-   [Configuring a PVC](#section05111743361)
-   [Using a PVC](#section2949728204519)

## Preparation{#section4107171112475}

A storage resource, such as a LUN or file system, required by the PV to be created exists on the storage device. If the storage resource is a file system, you also need to create the share and client information of the file system.

## Configuring a PV{#section651114483616}

1.  Prepare the PV configuration file  **mypv.yaml**. The following is an example. For details about other parameters, see  [Table 1](#en-us_topic_0000001255922865_table055742511559).

    ```yaml
    kind: PersistentVolume
    apiVersion: v1
    metadata:
      name: mypv
    spec:
      volumeMode: Filesystem
      storageClassName: "" # The value must be to "".
      accessModes:
        - ReadWriteOnce
      csi:
        driver: csi.huawei.com # Enter the CSI driver name.
        volumeHandle: iscsi-dorado-181.lun0001 # Enter the volume name.
        fsType: xfs # Set the file system type.
      capacity:
        storage: 100Gi
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >In the configuration file for static volume provisioning,  **storageClassName**  must be set to  **""**. Otherwise, Kubernetes will use the default StorageClass.

2.  Run the following command to create a PV based on the prepared .yaml file.

    ```
    kubectl create -f mypv.yaml
    ```

3.  After a period of time, run the following command to view the information about the created PV.

    ```
    kubectl get pv
    ```

    The following is an example of the command output. If the PV status is  **Available**, the PV is successfully created.

    ```
    NAME       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM               STORAGECLASS   REASON   AGE
    mypv       100Gi      RWO            Retain           Available                                               4s
    ```

**Table  1**  Parameters for configuring a static PV

<a name="en-us_topic_0000001255922865_table055742511559"></a>
<table><thead align="left"><tr id="en-us_topic_0000001255922865_row555722555518"><th class="cellrowborder" valign="top" width="17.687074829931973%" id="mcps1.2.6.1.1"><p id="en-us_topic_0000001255922865_p1257333517017"><a name="en-us_topic_0000001255922865_p1257333517017"></a><a name="en-us_topic_0000001255922865_p1257333517017"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="28.49368318756074%" id="mcps1.2.6.1.2"><p id="en-us_topic_0000001255922865_p1457323512015"><a name="en-us_topic_0000001255922865_p1457323512015"></a><a name="en-us_topic_0000001255922865_p1457323512015"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="6.802721088435375%" id="mcps1.2.6.1.3"><p id="p153581815174412"><a name="p153581815174412"></a><a name="p153581815174412"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="13.80952380952381%" id="mcps1.2.6.1.4"><p id="p135944173447"><a name="p135944173447"></a><a name="p135944173447"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="33.20699708454811%" id="mcps1.2.6.1.5"><p id="en-us_topic_0000001255922865_p85734352017"><a name="en-us_topic_0000001255922865_p85734352017"></a><a name="en-us_topic_0000001255922865_p85734352017"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000001255922865_row955713252557"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p3573335305"><a name="en-us_topic_0150885187_p3573335305"></a><a name="en-us_topic_0150885187_p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p205736355017"><a name="en-us_topic_0150885187_p205736355017"></a><a name="en-us_topic_0150885187_p205736355017"></a>User-defined name of a PV object.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p935815152442"><a name="p935815152442"></a><a name="p935815152442"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p4594101744415"><a name="p4594101744415"></a><a name="p4594101744415"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0150885187_p179301591191"><a name="en-us_topic_0150885187_p179301591191"></a><a name="en-us_topic_0150885187_p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="en-us_topic_0000001255922865_row16557202515555"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p1896393118231"><a name="en-us_topic_0150885187_p1896393118231"></a><a name="en-us_topic_0150885187_p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p1610614478451"><a name="p1610614478451"></a><a name="p1610614478451"></a>Volume mode. This parameter is optional. When LUN volumes are used, the following types are supported:</p>
<a name="ul550911281034"></a><a name="ul550911281034"></a><ul id="ul550911281034"><li><strong id="b148289292110"><a name="b148289292110"></a><a name="b148289292110"></a>Filesystem</strong>: local file system.</li><li><strong id="b133631047219"><a name="b133631047219"></a><a name="b133631047219"></a>Block</strong>: raw device.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p183583151446"><a name="p183583151446"></a><a name="p183583151446"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p1779184518303"><a name="p1779184518303"></a><a name="p1779184518303"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p62045214421"><a name="p62045214421"></a><a name="p62045214421"></a>This parameter takes effect when a PV is mounted. The default value is <strong id="b1235917562112"><a name="b1235917562112"></a><a name="b1235917562112"></a>Filesystem</strong>.</p>
<a name="ul1527393212316"></a><a name="ul1527393212316"></a><ul id="ul1527393212316"><li><strong id="b962411622110"><a name="b962411622110"></a><a name="b962411622110"></a>Filesystem</strong> indicates that a container accesses a PV using a local file system. The local file system type is specified by the <strong id="b106245614217"><a name="b106245614217"></a><a name="b106245614217"></a>fsType</strong> field in the specified StorageClass.</li><li><strong id="b114112862120"><a name="b114112862120"></a><a name="b114112862120"></a>Block</strong> indicates that a PV is accessed in raw volume mode.</li></ul>
</td>
</tr>
<tr id="en-us_topic_0000001255922865_row5486654134918"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001255922865_p357320351304"><a name="en-us_topic_0000001255922865_p357320351304"></a><a name="en-us_topic_0000001255922865_p357320351304"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001255922865_p135732351909"><a name="en-us_topic_0000001255922865_p135732351909"></a><a name="en-us_topic_0000001255922865_p135732351909"></a>Name of the StorageClass object. This parameter is mandatory.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p83581015194419"><a name="p83581015194419"></a><a name="p83581015194419"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p85951917184420"><a name="p85951917184420"></a><a name="p85951917184420"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001255922865_p1139501413438"><a name="en-us_topic_0000001255922865_p1139501413438"></a><a name="en-us_topic_0000001255922865_p1139501413438"></a>Set the parameter to an empty string, that is, enter <strong id="b1713031416217"><a name="b1713031416217"></a><a name="b1713031416217"></a>""</strong>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001255922865_row755722515552"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0150885187_p1657333515012"><a name="en-us_topic_0150885187_p1657333515012"></a><a name="en-us_topic_0150885187_p1657333515012"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p51122302293"><a name="p51122302293"></a><a name="p51122302293"></a>Access mode of the volume.</p>
<a name="ul989211520315"></a><a name="ul989211520315"></a><ul id="ul989211520315"><li><strong id="b2062211291309"><a name="b2062211291309"></a><a name="b2062211291309"></a>RWO</strong> (ReadWriteOnce): A volume can be mounted to a node in read/write mode. This mode also allows multiple Pods running on the same node to access the volume.</li><li><strong id="b682416318301"><a name="b682416318301"></a><a name="b682416318301"></a>ROX</strong> (ReadOnlyMany): A volume can be mounted to multiple nodes in read-only mode.</li><li><strong id="b13775173263019"><a name="b13775173263019"></a><a name="b13775173263019"></a>RWX</strong> (ReadWriteMany): A volume can be mounted to multiple nodes in read/write mode.</li><li><strong id="b19735193373016"><a name="b19735193373016"></a><a name="b19735193373016"></a>RWOP</strong> (ReadWriteOncePod): A volume can only be mounted to a single Pod in read/write mode. Kubernetes 1.22 and later versions support this feature.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p11358015174414"><a name="p11358015174414"></a><a name="p11358015174414"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p1959571724410"><a name="p1959571724410"></a><a name="p1959571724410"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><a name="ul13431556330"></a><a name="ul13431556330"></a><ul id="ul13431556330"><li>RWO/ROX/RWOP: supported by all types of volumes. RWOP is supported only by Kubernetes 1.22 and later versions. Check whether this feature is enabled for your Kubernetes cluster by referring to <a href="/css-docs/en/docs/common-o-m-operations/enabling-the-readwriteoncepod-feature-gate">Enabling the ReadWriteOncePod Feature Gate</a>.</li><li>The support for RWX is as follows:<a name="ul201701421154515"></a><a name="ul201701421154515"></a><ul id="ul201701421154515"><li>NAS storage: supported by all volumes</li><li>SAN storage: supported only by volumes whose <strong id="b197801206454024"><a name="b197801206454024"></a><a name="b197801206454024"></a>volumeMode</strong> is set to <strong id="b211643035154024"><a name="b211643035154024"></a><a name="b211643035154024"></a>Block</strong></li></ul>
</li></ul>
</td>
</tr>
<tr id="en-us_topic_0000001255922865_row9557202575510"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001255922865_p155717257554"><a name="en-us_topic_0000001255922865_p155717257554"></a><a name="en-us_topic_0000001255922865_p155717257554"></a>spec.csi.driver</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001255922865_p5557025165510"><a name="en-us_topic_0000001255922865_p5557025165510"></a><a name="en-us_topic_0000001255922865_p5557025165510"></a>CSI driver name.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p935821564411"><a name="p935821564411"></a><a name="p935821564411"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p059518172448"><a name="p059518172448"></a><a name="p059518172448"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001255922865_p25576254553"><a name="en-us_topic_0000001255922865_p25576254553"></a><a name="en-us_topic_0000001255922865_p25576254553"></a>Set this parameter to the driver name set during Huawei CSI installation.</p>
</td>
</tr>
<tr id="en-us_topic_0000001255922865_row18141551408"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001255922865_p141411251907"><a name="en-us_topic_0000001255922865_p141411251907"></a><a name="en-us_topic_0000001255922865_p141411251907"></a>spec.csi.volumeHandle</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p10302308143"><a name="p10302308143"></a><a name="p10302308143"></a>Unique identifier of a storage resource. This parameter is mandatory.</p>
<p id="en-us_topic_0000001255922865_p2141135115012"><a name="en-us_topic_0000001255922865_p2141135115012"></a><a name="en-us_topic_0000001255922865_p2141135115012"></a>Format: <em id="i2298182442216"><a name="i2298182442216"></a><a name="i2298182442216"></a>&lt;backendName&gt;</em><strong id="b101527265229"><a name="b101527265229"></a><a name="b101527265229"></a>.</strong><em id="i9925112811222"><a name="i9925112811222"></a><a name="i9925112811222"></a>&lt;volume-name&gt;</em></p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p10358141513449"><a name="p10358141513449"></a><a name="p10358141513449"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p11595121794411"><a name="p11595121794411"></a><a name="p11595121794411"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001255922865_p105611631131211"><a name="en-us_topic_0000001255922865_p105611631131211"></a><a name="en-us_topic_0000001255922865_p105611631131211"></a>The value of this parameter consists of the following parts:</p>
<a name="en-us_topic_0000001255922865_ul317520442816"></a><a name="en-us_topic_0000001255922865_ul317520442816"></a><ul id="en-us_topic_0000001255922865_ul317520442816"><li><em id="i11303163992212"><a name="i11303163992212"></a><a name="i11303163992212"></a>&lt;backendName&gt;</em>: indicates the name of the backend where the volume resides. You can run the following command to obtain the configured backend information.<p id="p101424597119"><a name="p101424597119"></a><a name="p101424597119"></a><strong id="b1736283518212"><a name="b1736283518212"></a><a name="b1736283518212"></a>oceanctl get backend</strong></p>
</li><li><em id="i12322151610233"><a name="i12322151610233"></a><a name="i12322151610233"></a>&lt;volume-name&gt;</em>: indicates the name of a resource (LUN/file system) on the storage. You can obtain the value from DeviceManager.</li></ul>
</td>
</tr>
<tr id="en-us_topic_0000001255922865_row197581481108"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001255922865_p110831210"><a name="en-us_topic_0000001255922865_p110831210"></a><a name="en-us_topic_0000001255922865_p110831210"></a>spec.csi.fsType</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p648319179411"><a name="p648319179411"></a><a name="p648319179411"></a>Type of a host file system. This parameter is optional. The supported types are:</p>
<a name="ul35039276418"></a><a name="ul35039276418"></a><ul id="ul35039276418"><li>ext2</li><li>ext3</li><li>ext4</li><li>xfs</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1735841534417"><a name="p1735841534417"></a><a name="p1735841534417"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p1959531715445"><a name="p1959531715445"></a><a name="p1959531715445"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p748584017914"><a name="p748584017914"></a><a name="p748584017914"></a>If this parameter is not set, the default value <strong id="b1741124652319"><a name="b1741124652319"></a><a name="b1741124652319"></a>ext4</strong> is used. This parameter is available only when <strong id="b8787155232319"><a name="b8787155232319"></a><a name="b8787155232319"></a>volumeMode</strong> is set to <strong id="b1788175212317"><a name="b1788175212317"></a><a name="b1788175212317"></a>Filesystem</strong>.</p>
</td>
</tr>
<tr id="row1894264183210"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p1294211453210"><a name="p1294211453210"></a><a name="p1294211453210"></a>spec.csi.volumeAttributes.dTreeParentName</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p189421447325"><a name="p189421447325"></a><a name="p189421447325"></a>Name of the parent file system when the volume resource type is dtree.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1694217415328"><a name="p1694217415328"></a><a name="p1694217415328"></a>Conditionally mandatory</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p169421345328"><a name="p169421345328"></a><a name="p169421345328"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p139424420325"><a name="p139424420325"></a><a name="p139424420325"></a>This parameter is mandatory when the managed object is a dtree resource and the <strong id="b133521222218"><a name="b133521222218"></a><a name="b133521222218"></a>parentname</strong> parameter is not configured in the storage backend.</p>
<p id="p1545865605919"><a name="p1545865605919"></a><a name="p1545865605919"></a>If <strong id="b106757519292"><a name="b106757519292"></a><a name="b106757519292"></a>dTreeParentName</strong> is configured only in the PV but <strong id="b12614134202920"><a name="b12614134202920"></a><a name="b12614134202920"></a>parentname</strong> is not configured in the corresponding storage backend, set <strong id="b1567545102912"><a name="b1567545102912"></a><a name="b1567545102912"></a>CSIDriverObject.attachRequired</strong> to <strong id="b15675105112912"><a name="b15675105112912"></a><a name="b15675105112912"></a>true</strong> during CSI installation according to <a href="/css-docs/en/docs/installation-and-deployment/csi/installation/installation-using-helm/parameters-in-the-values-yaml-file-of-helm#table258712427285">Table 5</a>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001255922865_row1455742510558"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0000001255922865_p055732595515"><a name="en-us_topic_0000001255922865_p055732595515"></a><a name="en-us_topic_0000001255922865_p055732595515"></a>spec.capacity.storage</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001255922865_p1573183510015"><a name="en-us_topic_0000001255922865_p1573183510015"></a><a name="en-us_topic_0000001255922865_p1573183510015"></a>Volume size.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1035831513448"><a name="p1035831513448"></a><a name="p1035831513448"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p659511704418"><a name="p659511704418"></a><a name="p659511704418"></a>100Gi</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0000001255922865_p6871647174317"><a name="en-us_topic_0000001255922865_p6871647174317"></a><a name="en-us_topic_0000001255922865_p6871647174317"></a>Ensure that the size is the same as that of the corresponding resource on the storage. Kubernetes will not invoke CSI to check whether the value of this parameter is correct. Therefore, the PV can be successfully created even if its capacity is inconsistent with that of the corresponding resource on the storage.</p>
</td>
</tr>
<tr id="row160819410575"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p1036995916474"><a name="p1036995916474"></a><a name="p1036995916474"></a>spec.mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p16369105917476"><a name="p16369105917476"></a><a name="p16369105917476"></a>NFS mount option on the host. The following mount option is supported:</p>
<p id="p3366172411524"><a name="p3366172411524"></a><a name="p3366172411524"></a><strong id="b23582052514"><a name="b23582052514"></a><a name="b23582052514"></a>nfsvers</strong>: protocol version for NFS mounting. The value can be <strong id="b17128111044018"><a name="b17128111044018"></a><a name="b17128111044018"></a>3</strong>, <strong id="b712871044016"><a name="b712871044016"></a><a name="b712871044016"></a>4</strong>, <strong id="b21281710174015"><a name="b21281710174015"></a><a name="b21281710174015"></a>4.0</strong>, <strong id="b3129010134013"><a name="b3129010134013"></a><a name="b3129010134013"></a>4.1</strong>, or <strong id="b1112911094019"><a name="b1112911094019"></a><a name="b1112911094019"></a>4.2</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p7358615164410"><a name="p7358615164410"></a><a name="p7358615164410"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p95951917154413"><a name="p95951917154413"></a><a name="p95951917154413"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p775515413439"><a name="p775515413439"></a><a name="p775515413439"></a>This parameter is optional after the <strong id="b5799152218253"><a name="b5799152218253"></a><a name="b5799152218253"></a>-o</strong> parameter when the <strong id="b19800132213251"><a name="b19800132213251"></a><a name="b19800132213251"></a>mount</strong> command is executed on the host. The value is in list format.</p>
<p id="p486929143316"><a name="p486929143316"></a><a name="p486929143316"></a>If the NFS version is specified for mounting, NFS 3, 4.0, 4.1, and 4.2 protocols are supported (the protocol must be supported and enabled on storage devices). If <strong id="b14752182915401"><a name="b14752182915401"></a><a name="b14752182915401"></a>nfsvers</strong> is set to <strong id="b7752142974018"><a name="b7752142974018"></a><a name="b7752142974018"></a>4</strong>, the latest protocol version NFS 4 may be used for mounting due to different OS configurations, for example, 4.2. If the 4.0 protocol is required, you are advised to set <strong id="b575342919402"><a name="b575342919402"></a><a name="b575342919402"></a>nfsvers</strong> to <strong id="b20753112910401"><a name="b20753112910401"></a><a name="b20753112910401"></a>4.0</strong>.</p>
</td>
</tr>
<tr id="row19538145720"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p743994313307"><a name="p743994313307"></a><a name="p743994313307"></a>spec.mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p7439243173012"><a name="p7439243173012"></a><a name="p7439243173012"></a>The DPC namespace supports the ACL function. The DPC client supports POSIX ACL, NFSv4 ACL, and NT ACL authentication.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1335861512440"><a name="p1335861512440"></a><a name="p1335861512440"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p12595121774413"><a name="p12595121774413"></a><a name="p12595121774413"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p1451716198319"><a name="p1451716198319"></a><a name="p1451716198319"></a>The descriptions of <strong id="b6804888395379"><a name="b6804888395379"></a><a name="b6804888395379"></a>acl</strong>, <strong id="b2556128335379"><a name="b2556128335379"></a><a name="b2556128335379"></a>aclonlyposix</strong>, <strong id="b109942945379"><a name="b109942945379"></a><a name="b109942945379"></a>cnflush</strong>, and <strong id="b11772349915379"><a name="b11772349915379"></a><a name="b11772349915379"></a>cflush</strong> are for reference only. For details about the parameters, see <a href="https://support.huawei.com/enterprise/en/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">OceanStor Pacific Series Product Documentation</a> and choose <strong id="b20200361975379"><a name="b20200361975379"></a><a name="b20200361975379"></a>Configuration</strong> &gt; <strong id="b11899759175379"><a name="b11899759175379"></a><a name="b11899759175379"></a>Basic Service Configuration Guide for File</strong> &gt; <strong id="b14958274015379"><a name="b14958274015379"></a><a name="b14958274015379"></a>Configuring Basic Services (DPC Scenario)</strong> &gt; <strong id="b2849056205379"><a name="b2849056205379"></a><a name="b2849056205379"></a>Accessing a DPC Share on a Client</strong> &gt; <strong id="b13786891605379"><a name="b13786891605379"></a><a name="b13786891605379"></a>Step 2</strong>.</p>
</td>
</tr>
<tr id="row1046785975611"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p184399439309"><a name="p184399439309"></a><a name="p184399439309"></a>spec.mountOptions.aclonlyposix</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p13950103563719"><a name="p13950103563719"></a><a name="p13950103563719"></a>The DPC namespace supports POSIX ACL, and the DPC client supports POSIX ACL authentication.</p>
<p id="p1943913439308"><a name="p1943913439308"></a><a name="p1943913439308"></a>The following protocols support POSIX ACL: DPC, NFSv3, and HDFS. If NFSv4 ACL or NT ACL is used, the DPC client cannot identify the ACL of this type. As a result, the ACL of this type does not take effect.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p2358191544418"><a name="p2358191544418"></a><a name="p2358191544418"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p65951417164420"><a name="p65951417164420"></a><a name="p65951417164420"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p718315423511"><a name="p718315423511"></a><a name="p718315423511"></a>If <strong id="b15702153682513"><a name="b15702153682513"></a><a name="b15702153682513"></a>aclonlyposix</strong> and <strong id="b8703143611257"><a name="b8703143611257"></a><a name="b8703143611257"></a>acl</strong> are used together, only <strong id="b270310364252"><a name="b270310364252"></a><a name="b270310364252"></a>acl</strong> takes effect. That is, the namespace supports the ACL function.</p>
</td>
</tr>
<tr id="row10116155295616"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p867705717358"><a name="p867705717358"></a><a name="p867705717358"></a>spec.mountOptions.cnflush</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p7533510163615"><a name="p7533510163615"></a><a name="p7533510163615"></a>Asynchronous disk flushing mode. That is, data is not flushed to disks immediately when files in the namespace are closed.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p835881513448"><a name="p835881513448"></a><a name="p835881513448"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p1159501724414"><a name="p1159501724414"></a><a name="p1159501724414"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p46771657123516"><a name="p46771657123516"></a><a name="p46771657123516"></a>Asynchronous flushing mode: When a file is closed, data in the cache is not flushed to storage media in synchronous mode. Instead, data is written from the cache to the storage media in asynchronous flushing mode. After the write service is complete, data is flushed from the cache to disks periodically based on the flushing period. In a multi-client scenario, if concurrent operations are performed on the same file, the file size update is affected by the disk flushing period. That is, the file size is updated only after the disk flushing is complete. Generally, the update is completed within several seconds. Synchronous I/Os are not affected by the disk flushing period.</p>
</td>
</tr>
<tr id="row9773155135618"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p13444191520365"><a name="p13444191520365"></a><a name="p13444191520365"></a>spec.mountOptions.cflush</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p194444156366"><a name="p194444156366"></a><a name="p194444156366"></a>Synchronous disk flushing mode. That is, data is flushed to disks immediately when files in the namespace are closed.</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1835861516442"><a name="p1835861516442"></a><a name="p1835861516442"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p35951517104413"><a name="p35951517104413"></a><a name="p35951517104413"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p18444315183615"><a name="p18444315183615"></a><a name="p18444315183615"></a>By default, the synchronous disk flushing mode is used.</p>
</td>
</tr>
</tbody>
</table>

## Configuring a PVC{#section05111743361}

After a PV is created in static volume provisioning mode, you can create a PVC based on the PV for containers.

1.  Prepare the PVC configuration file  **mypvc.yaml**. The following is an example. For details about other parameters, see  [Table 2](#table195731435604).

    ```yaml
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: mypvc
    spec:
      storageClassName: ""
      accessModes:
        - ReadWriteOnce
      volumeMode: Filesystem
      resources:
        requests:
          storage: 100Gi
      volumeName: mypv # Enter the name of the corresponding PV.
    ```

2.  Run the following command to create a PVC based on the configured .yaml file.

    ```
    kubectl create -f mypvc.yaml
    ```

3.  After a period of time, run the following command to view the information about the created PVC.

    ```
    kubectl get pvc
    ```

    The following is an example of the command output. If the PVC status is  **Bound**, the PVC is successfully created.

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO                           12s
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >-   After the PVC is created, if the PVC is in the  **Pending**  state after a long time, see  [When a PVC Is Created, the PVC Is in the Pending State](/docs/troubleshooting/pvc-issues/when-a-pvc-is-created-the-pvc-is-in-the-pending-state).
    >-   You are advised to create or delete a maximum of 100 PVCs in a batch.

**Table  2**  PVC parameters for configuring a static PV

<a name="table195731435604"></a>
<table><thead align="left"><tr id="row35732351904"><th class="cellrowborder" valign="top" width="13.47865213478652%" id="mcps1.2.6.1.1"><p id="p1257333517017"><a name="p1257333517017"></a><a name="p1257333517017"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="30.12698730126987%" id="mcps1.2.6.1.2"><p id="p1457323512015"><a name="p1457323512015"></a><a name="p1457323512015"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="5.899410058994099%" id="mcps1.2.6.1.3"><p id="p1223918284404"><a name="p1223918284404"></a><a name="p1223918284404"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="8.57914208579142%" id="mcps1.2.6.1.4"><p id="p193751530154015"><a name="p193751530154015"></a><a name="p193751530154015"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="41.91580841915808%" id="mcps1.2.6.1.5"><p id="p85734352017"><a name="p85734352017"></a><a name="p85734352017"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row5573635907"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p3573335305"><a name="p3573335305"></a><a name="p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p205736355017"><a name="p205736355017"></a><a name="p205736355017"></a>User-defined name of a PVC object.</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p15360547910"><a name="p15360547910"></a><a name="p15360547910"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p1637510306406"><a name="p1637510306406"></a><a name="p1637510306406"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="p179301591191"><a name="p179301591191"></a><a name="p179301591191"></a>Take Kubernetes v1.22.1 as an example. The value can contain digits, lowercase letters, hyphens (-), and periods (.), and must start and end with a letter or digit.</p>
</td>
</tr>
<tr id="row10874152212484"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p0833642172413"><a name="p0833642172413"></a><a name="p0833642172413"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p2083384212416"><a name="p2083384212416"></a><a name="p2083384212416"></a>Access mode of the volume.</p>
<a name="ul18620120655"></a><a name="ul18620120655"></a><ul id="ul18620120655"><li><strong id="b1920971745"><a name="b1920971745"></a><a name="b1920971745"></a>RWO</strong> (ReadWriteOnce): A volume can be mounted to a node in read/write mode. This mode also allows multiple Pods running on the same node to access the volume.</li><li><strong id="b1245755049"><a name="b1245755049"></a><a name="b1245755049"></a>ROX</strong> (ReadOnlyMany): A volume can be mounted to multiple nodes in read-only mode.</li><li><strong id="b890416672"><a name="b890416672"></a><a name="b890416672"></a>RWX</strong> (ReadWriteMany): A volume can be mounted to multiple nodes in read/write mode.</li><li><strong id="b1190976238"><a name="b1190976238"></a><a name="b1190976238"></a>RWOP</strong> (ReadWriteOncePod): A volume can only be mounted to a single Pod in read/write mode. Kubernetes 1.22 and later versions support this feature.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p1823972854011"><a name="p1823972854011"></a><a name="p1823972854011"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p18375123074018"><a name="p18375123074018"></a><a name="p18375123074018"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><a name="ul096872054"></a><a name="ul096872054"></a><ul id="ul096872054"><li>RWO/ROX/RWOP: supported by all types of volumes. RWOP is supported only by Kubernetes 1.22 and later versions. For versions earlier than Kubernetes 1.29, you need to enable this feature by following the instructions in <a href="/css-docs/en/docs/common-o-m-operations/enabling-the-readwriteoncepod-feature-gate">Enabling the ReadWriteOncePod Feature Gate</a>.</li><li>The support for RWX is as follows:<a name="ul283313421245"></a><a name="ul283313421245"></a><ul id="ul283313421245"><li>NAS storage: supported by all volumes</li><li>SAN storage: supported only by volumes whose <strong id="b209190380754024"><a name="b209190380754024"></a><a name="b209190380754024"></a>volumeMode</strong> is set to <strong id="b170161632254024"><a name="b170161632254024"></a><a name="b170161632254024"></a>Block</strong></li></ul>
</li></ul>
</td>
</tr>
<tr id="row696316316238"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p1896393118231"><a name="p1896393118231"></a><a name="p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p1996311317238"><a name="p1996311317238"></a><a name="p1996311317238"></a>Volume mode.</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p8239182864010"><a name="p8239182864010"></a><a name="p8239182864010"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p1237553064011"><a name="p1237553064011"></a><a name="p1237553064011"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="p10963143119234"><a name="p10963143119234"></a><a name="p10963143119234"></a>This parameter is optional. The value can be <strong id="b1950217454301"><a name="b1950217454301"></a><a name="b1950217454301"></a>Filesystem</strong> or <strong id="b3502445163020"><a name="b3502445163020"></a><a name="b3502445163020"></a>Block</strong>. The default value is <strong id="b175031145163015"><a name="b175031145163015"></a><a name="b175031145163015"></a>Filesystem</strong>. This parameter takes effect when a Pod is created. <strong id="b122791854203017"><a name="b122791854203017"></a><a name="b122791854203017"></a>Filesystem</strong> indicates that a file system is created on a PVC to access the storage. <strong id="b142791654143010"><a name="b142791654143010"></a><a name="b142791654143010"></a>Block</strong> indicates that a raw volume is used to access the storage.</p>
</td>
</tr>
<tr id="row18428153715212"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p94281537112112"><a name="p94281537112112"></a><a name="p94281537112112"></a>spec.resources.requests.storage</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p124283376211"><a name="p124283376211"></a><a name="p124283376211"></a>Size of the volume to be created.</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p1623917289400"><a name="p1623917289400"></a><a name="p1623917289400"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p1375730144016"><a name="p1375730144016"></a><a name="p1375730144016"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0150885187_p1573183510015"><a name="en-us_topic_0150885187_p1573183510015"></a><a name="en-us_topic_0150885187_p1573183510015"></a>Size of the volume to be created. The format is ***Gi and the unit is GiB.</p>
<p id="p1525217519276"><a name="p1525217519276"></a><a name="p1525217519276"></a>The PVC capacity depends on storage specifications and host specifications. For example, OceanStor Dorado 6.1.2 or OceanStor Pacific series 8.1.0 is connected to CentOS 7. If ext4 file systems are used, see <a href="/css-docs/en/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#en-us_topic_0150885187_table178824527142">Table 2</a>. If XFS file systems are used, see <a href="/css-docs/en/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#en-us_topic_0150885187_table101951367104">Table 3</a>. If NFS or raw devices are used, the capacity must meet the specifications of the used Huawei storage device model and version.</p>
<p id="p63667162711"><a name="p63667162711"></a><a name="p63667162711"></a>If the PVC capacity does not meet the specifications, a PVC or Pod may fail to be created due to the limitations of storage specifications or host file system specifications.</p>
<p id="p14102426144517"><a name="p14102426144517"></a><a name="p14102426144517"></a>When a PVC is created using a static PV and the PVC capacity is smaller than the capacity of the bound PV, the PVC capacity is set to the capacity of the bound PV. If the PVC capacity is greater than the capacity of the bound PV, the PVC cannot be created.</p>
</td>
</tr>
<tr id="row25733352019"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p2820143513433"><a name="p2820143513433"></a><a name="p2820143513433"></a>spec.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p38203355433"><a name="p38203355433"></a><a name="p38203355433"></a>Name of the PV object.</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p16239128124013"><a name="p16239128124013"></a><a name="p16239128124013"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p193751301406"><a name="p193751301406"></a><a name="p193751301406"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="p2082083524316"><a name="p2082083524316"></a><a name="p2082083524316"></a>This parameter is mandatory when a PVC is created statically.</p>
</td>
</tr>
<tr id="row1346813210239"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p16469332162317"><a name="p16469332162317"></a><a name="p16469332162317"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0150885187_p135732351909"><a name="en-us_topic_0150885187_p135732351909"></a><a name="en-us_topic_0150885187_p135732351909"></a>Name of the StorageClass object.</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p15469113232316"><a name="p15469113232316"></a><a name="p15469113232316"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p124691932162310"><a name="p124691932162310"></a><a name="p124691932162310"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="p1469332112312"><a name="p1469332112312"></a><a name="p1469332112312"></a>When a PVC is created, an empty character string is transferred. If this parameter is not set, the default StorageClass object name will be used.</p>
</td>
</tr>
</tbody>
</table>

## Using a PVC{#section2949728204519}

The use method is the same as that for dynamic volume provisioning in  [Using a PVC](/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#section8172141413917).

