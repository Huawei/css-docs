---
title: "静态卷供应PVC参数说明"
linkTitle: "静态卷供应PVC参数说明"
description: 
weight: 2
---

**表 1**  PVC参数说明

<a name="table195731435604"></a>
<table><thead align="left"><tr id="row35732351904"><th class="cellrowborder" valign="top" width="13.47865213478652%" id="mcps1.2.6.1.1"><p id="p1257333517017"><a name="p1257333517017"></a><a name="p1257333517017"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="30.12698730126987%" id="mcps1.2.6.1.2"><p id="p1457323512015"><a name="p1457323512015"></a><a name="p1457323512015"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="5.899410058994099%" id="mcps1.2.6.1.3"><p id="p1223918284404"><a name="p1223918284404"></a><a name="p1223918284404"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="8.57914208579142%" id="mcps1.2.6.1.4"><p id="p193751530154015"><a name="p193751530154015"></a><a name="p193751530154015"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="41.91580841915808%" id="mcps1.2.6.1.5"><p id="p85734352017"><a name="p85734352017"></a><a name="p85734352017"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row5573635907"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p3573335305"><a name="p3573335305"></a><a name="p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p205736355017"><a name="p205736355017"></a><a name="p205736355017"></a>自定义的PVC对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p15360547910"><a name="p15360547910"></a><a name="p15360547910"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p1637510306406"><a name="p1637510306406"></a><a name="p1637510306406"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="p179301591191"><a name="p179301591191"></a><a name="p179301591191"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="row10874152212484"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p1657333515012"><a name="zh-cn_topic_0150885187_p1657333515012"></a><a name="zh-cn_topic_0150885187_p1657333515012"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p51122302293"><a name="p51122302293"></a><a name="p51122302293"></a>指定卷访问模式。</p>
<a name="ul18620120655"></a><a name="ul18620120655"></a><ul id="ul18620120655"><li>RWO（ReadWriteOnce）：卷可以被一个节点以读写方式挂载。 该模式也允许运行在同一节点上的多个 Pod 访问卷。</li><li>ROX（ReadOnlyMany）：卷可以被多个节点以只读方式挂载。</li><li>RWX（ReadWriteMany）：卷可以被多个节点以读写方式挂载。</li><li>RWOP（ReadWriteOncePod）：卷只能被单个 Pod 以读写方式挂载。该特性需要 Kubernetes 1.22 以上版本。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p1823972854011"><a name="p1823972854011"></a><a name="p1823972854011"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p18375123074018"><a name="p18375123074018"></a><a name="p18375123074018"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><a name="ul096872054"></a><a name="ul096872054"></a><ul id="ul096872054"><li>RWO/ROX/RWOP：所有类型卷均支持，RWOP需Kubernetes 1.22版本以上支持。Kubernetes 1.29版本以下需要参考<a href="/css-docs/v4.7.0/common-operations/enabling-the-readwriteoncepod-feature-gate">开启ReadWriteOncePod功能门</a>章节开启该特性。</li><li><span>RWX</span>支持情况如下：<a name="ul201701421154515"></a><a name="ul201701421154515"></a><ul id="ul201701421154515"><li><a href="/css-docs/v4.7.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#li277121152812">NAS存储</a>：所有卷均支持。</li><li><a href="/css-docs/v4.7.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#zh-cn_topic_0000001324610777_li5135242193418">SAN存储</a>：仅volumeMode设置为Block的卷支持。</li></ul>
</li></ul>
</td>
</tr>
<tr id="row696316316238"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p1896393118231"><a name="p1896393118231"></a><a name="p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p1996311317238"><a name="p1996311317238"></a><a name="p1996311317238"></a>卷模式。</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p8239182864010"><a name="p8239182864010"></a><a name="p8239182864010"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p1237553064011"><a name="p1237553064011"></a><a name="p1237553064011"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="p10963143119234"><a name="p10963143119234"></a><a name="p10963143119234"></a>可选， 支持Filesystem或Block， 默认为Filesystem。该参数在创建Pod时生效，其中Filesystem表示在PVC上创建一个文件系统访问存储， Block表示使用裸卷的方式访问存储。</p>
</td>
</tr>
<tr id="row18428153715212"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p94281537112112"><a name="p94281537112112"></a><a name="p94281537112112"></a>spec.resources.requests.storage</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p124283376211"><a name="p124283376211"></a><a name="p124283376211"></a>指定待创建卷大小。</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p1623917289400"><a name="p1623917289400"></a><a name="p1623917289400"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p1375730144016"><a name="p1375730144016"></a><a name="p1375730144016"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0150885187_p1573183510015"><a name="zh-cn_topic_0150885187_p1573183510015"></a><a name="zh-cn_topic_0150885187_p1573183510015"></a>指定待创建卷大小，格式为***Gi，单位为GiB。</p>
<p id="p1525217519276"><a name="p1525217519276"></a><a name="p1525217519276"></a>PVC容量的规格取决于存储规格限制和主机规格限制。以OceanStor Dorado 6.1.2/OceanStor Pacific系列 8.1.0对接CentOS 7为例，当使用的是ext4文件系统时，容量限制见<a href="/css-docs/v4.7.0/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning#zh-cn_topic_0150885187_table178824527142">表2</a>；当使用的是XFS文件系统时，容量限制见<a href="/css-docs/v4.7.0/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning#zh-cn_topic_0150885187_table101951367104">表3</a>。如果使用的是NFS或者裸设备，容量需满足使用的华为存储设备型号和版本所要求的规格约束。</p>
<p id="p63667162711"><a name="p63667162711"></a><a name="p63667162711"></a>如果PVC容量不在规格范围内，可能会由于存储规格限制或主机文件系统规格限制导致创建PVC或Pod失败。</p>
<p id="p14102426144517"><a name="p14102426144517"></a><a name="p14102426144517"></a>在通过静态PV创建PVC时，若PVC容量小于绑定PV容量，最终PVC容量大小为绑定PV容量，若PVC容量大于绑定PV容量，PVC将无法被创建。</p>
</td>
</tr>
<tr id="row25733352019"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p2820143513433"><a name="p2820143513433"></a><a name="p2820143513433"></a>spec.volumeName</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="p38203355433"><a name="p38203355433"></a><a name="p38203355433"></a>PV对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p16239128124013"><a name="p16239128124013"></a><a name="p16239128124013"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p193751301406"><a name="p193751301406"></a><a name="p193751301406"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="p2082083524316"><a name="p2082083524316"></a><a name="p2082083524316"></a>静态创建PVC时必选。</p>
</td>
</tr>
<tr id="row1346813210239"><td class="cellrowborder" valign="top" width="13.47865213478652%" headers="mcps1.2.6.1.1 "><p id="p16469332162317"><a name="p16469332162317"></a><a name="p16469332162317"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="30.12698730126987%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0150885187_p135732351909"><a name="zh-cn_topic_0150885187_p135732351909"></a><a name="zh-cn_topic_0150885187_p135732351909"></a>StorageClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.899410058994099%" headers="mcps1.2.6.1.3 "><p id="p15469113232316"><a name="p15469113232316"></a><a name="p15469113232316"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.57914208579142%" headers="mcps1.2.6.1.4 "><p id="p124691932162310"><a name="p124691932162310"></a><a name="p124691932162310"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="41.91580841915808%" headers="mcps1.2.6.1.5 "><p id="p1469332112312"><a name="p1469332112312"></a><a name="p1469332112312"></a>创建PVC时传空字符串，不设置该参数会使用默认的StorageClass对象名称。</p>
</td>
</tr>
</tbody>
</table>

