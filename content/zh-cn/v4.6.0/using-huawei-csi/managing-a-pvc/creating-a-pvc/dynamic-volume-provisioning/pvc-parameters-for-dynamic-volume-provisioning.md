---
title: "动态卷供应PVC参数说明"
linkTitle: "动态卷供应PVC参数说明"
description: 
weight: 3
---

在完成配置StorageClass以后，就可以用该StorageClass来配置PVC。PVC的配置模板请参考华为CSI软件包中的examples目录下的pvc\*.yaml文件示例。

**表 1**  pvc\*.yaml文件示例参数说明

<a name="zh-cn_topic_0150885187_table195731435604"></a>
<table><thead align="left"><tr id="zh-cn_topic_0150885187_row35732351904"><th class="cellrowborder" valign="top" width="15.721572157215721%" id="mcps1.2.6.1.1"><p id="zh-cn_topic_0150885187_p1257333517017"><a name="zh-cn_topic_0150885187_p1257333517017"></a><a name="zh-cn_topic_0150885187_p1257333517017"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="24.652465246524653%" id="mcps1.2.6.1.2"><p id="zh-cn_topic_0150885187_p1457323512015"><a name="zh-cn_topic_0150885187_p1457323512015"></a><a name="zh-cn_topic_0150885187_p1457323512015"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="6.9006900690069015%" id="mcps1.2.6.1.3"><p id="p1173514981420"><a name="p1173514981420"></a><a name="p1173514981420"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="8.8008800880088%" id="mcps1.2.6.1.4"><p id="p1589881291419"><a name="p1589881291419"></a><a name="p1589881291419"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="43.92439243924392%" id="mcps1.2.6.1.5"><p id="zh-cn_topic_0150885187_p85734352017"><a name="zh-cn_topic_0150885187_p85734352017"></a><a name="zh-cn_topic_0150885187_p85734352017"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0150885187_row5573635907"><td class="cellrowborder" valign="top" width="15.721572157215721%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p3573335305"><a name="zh-cn_topic_0150885187_p3573335305"></a><a name="zh-cn_topic_0150885187_p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="24.652465246524653%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0150885187_p205736355017"><a name="zh-cn_topic_0150885187_p205736355017"></a><a name="zh-cn_topic_0150885187_p205736355017"></a>自定义的PVC对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.9006900690069015%" headers="mcps1.2.6.1.3 "><p id="p7736109151413"><a name="p7736109151413"></a><a name="p7736109151413"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.8008800880088%" headers="mcps1.2.6.1.4 "><p id="p1589841231412"><a name="p1589841231412"></a><a name="p1589841231412"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="43.92439243924392%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0150885187_p179301591191"><a name="zh-cn_topic_0150885187_p179301591191"></a><a name="zh-cn_topic_0150885187_p179301591191"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row696316316238"><td class="cellrowborder" valign="top" width="15.721572157215721%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p1896393118231"><a name="zh-cn_topic_0150885187_p1896393118231"></a><a name="zh-cn_topic_0150885187_p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="24.652465246524653%" headers="mcps1.2.6.1.2 "><p id="p1610614478451"><a name="p1610614478451"></a><a name="p1610614478451"></a>卷模式。可选参数。 当使用LUN类型的卷时，支持配置以下类型：</p>
<a name="ul823916101324"></a><a name="ul823916101324"></a><ul id="ul823916101324"><li>Filesystem：本地文件系统。</li><li>Block：裸设备。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.9006900690069015%" headers="mcps1.2.6.1.3 "><p id="p1373612911410"><a name="p1373612911410"></a><a name="p1373612911410"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="8.8008800880088%" headers="mcps1.2.6.1.4 "><p id="p0898191211148"><a name="p0898191211148"></a><a name="p0898191211148"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="43.92439243924392%" headers="mcps1.2.6.1.5 "><p id="p62045214421"><a name="p62045214421"></a><a name="p62045214421"></a>该参数在挂载PV时生效，默认为Filesystem。</p>
<a name="ul1518211174214"></a><a name="ul1518211174214"></a><ul id="ul1518211174214"><li>Filesystem表示在容器通过一个本地文件系统访问PV，本地文件系统类型为指定StorageClass中的fsType字段指定, Dtree类型存储也使用此参数进行描述。</li><li>Block表示使用裸卷的方式访问访问PV。</li></ul>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row25733352019"><td class="cellrowborder" valign="top" width="15.721572157215721%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p357320351304"><a name="zh-cn_topic_0150885187_p357320351304"></a><a name="zh-cn_topic_0150885187_p357320351304"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="24.652465246524653%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0150885187_p135732351909"><a name="zh-cn_topic_0150885187_p135732351909"></a><a name="zh-cn_topic_0150885187_p135732351909"></a>StorageClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.9006900690069015%" headers="mcps1.2.6.1.3 "><p id="p127361496143"><a name="p127361496143"></a><a name="p127361496143"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.8008800880088%" headers="mcps1.2.6.1.4 "><p id="p1989831211414"><a name="p1989831211414"></a><a name="p1989831211414"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="43.92439243924392%" headers="mcps1.2.6.1.5 "><p id="p1521791621216"><a name="p1521791621216"></a><a name="p1521791621216"></a>业务需要的StorageClass对象名称。</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row1157316351102"><td class="cellrowborder" valign="top" width="15.721572157215721%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p9573035309"><a name="zh-cn_topic_0150885187_p9573035309"></a><a name="zh-cn_topic_0150885187_p9573035309"></a>spec.resources.requests.storage</p>
</td>
<td class="cellrowborder" valign="top" width="24.652465246524653%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0150885187_p1573183510015"><a name="zh-cn_topic_0150885187_p1573183510015"></a><a name="zh-cn_topic_0150885187_p1573183510015"></a>指定待创建卷大小，格式为***Gi，单位为GiB。需要满足大小为512字节的整数倍。</p>
</td>
<td class="cellrowborder" valign="top" width="6.9006900690069015%" headers="mcps1.2.6.1.3 "><p id="p87363981412"><a name="p87363981412"></a><a name="p87363981412"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.8008800880088%" headers="mcps1.2.6.1.4 "><p id="p489841251410"><a name="p489841251410"></a><a name="p489841251410"></a>10Gi</p>
</td>
<td class="cellrowborder" valign="top" width="43.92439243924392%" headers="mcps1.2.6.1.5 "><p id="p1525217519276"><a name="p1525217519276"></a><a name="p1525217519276"></a>PVC容量的规格取决于存储规格限制和主机规格限制。以OceanStor Dorado 6.1.2/OceanStor Pacific系列 8.1.0对接CentOS 7为例，当使用的是ext4文件系统时，容量限制见<a href="#zh-cn_topic_0150885187_table178824527142">表2</a>；当使用的是XFS文件系统时，容量限制见<a href="#zh-cn_topic_0150885187_table101951367104">表3</a>。如果使用的是NFS或者裸设备，容量需满足使用的华为存储设备型号和版本所要求的规格约束。</p>
<p id="p63667162711"><a name="p63667162711"></a><a name="p63667162711"></a>如果PVC容量不在规格范围内，可能会由于存储规格限制或主机文件系统规格限制导致创建PVC或Pod失败。</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row6573635502"><td class="cellrowborder" valign="top" width="15.721572157215721%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p1657333515012"><a name="zh-cn_topic_0150885187_p1657333515012"></a><a name="zh-cn_topic_0150885187_p1657333515012"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="24.652465246524653%" headers="mcps1.2.6.1.2 "><p id="p51122302293"><a name="p51122302293"></a><a name="p51122302293"></a>指定卷访问模式。</p>
<a name="ul69743301323"></a><a name="ul69743301323"></a><ul id="ul69743301323"><li><span>RWO</span>（ReadWriteOnce）：卷可以被一个节点以读写方式挂载。 该模式也允许运行在同一节点上的多个 Pod 访问卷。</li><li><span>ROX</span>（ReadOnlyMany）：卷可以被多个节点以只读方式挂载。</li><li><span>RWX</span>（ReadWriteMany）：卷可以被多个节点以读写方式挂载。</li><li><span>RWOP</span>（ReadWriteOncePod）：卷只能被单个 Pod 以读写方式挂载。该特性需要 Kubernetes 1.22 以上版本。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.9006900690069015%" headers="mcps1.2.6.1.3 "><p id="p87361891145"><a name="p87361891145"></a><a name="p87361891145"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="8.8008800880088%" headers="mcps1.2.6.1.4 "><p id="p1589841251413"><a name="p1589841251413"></a><a name="p1589841251413"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="43.92439243924392%" headers="mcps1.2.6.1.5 "><a name="ul16793434324"></a><a name="ul16793434324"></a><ul id="ul16793434324"><li><span>RWO/ROX/RWOP：</span>所有类型卷均支持，<span>RWOP</span>需<span>Kubernetes 1.22</span>版本以上支持。Kubernetes 1.29版本以下需要参考<a href="/css-docs/v4.6.0/common-operations/enabling-the-readwriteoncepod-feature-gate">开启ReadWriteOncePod功能门</a>章节开启该特性。</li><li><span>RWX</span>支持情况如下：<a name="ul201701421154515"></a><a name="ul201701421154515"></a><ul id="ul201701421154515"><li><a href="/css-docs/v4.6.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#li277121152812">NAS存储</a>：所有卷均支持。</li><li><a href="/css-docs/v4.6.0/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#zh-cn_topic_0000001324610777_li5135242193418">SAN存储</a>：仅volumeMode设置为Block的卷支持。</li></ul>
</li></ul>
</td>
</tr>
</tbody>
</table>

**表 2**  ext4容量的规格

<a name="zh-cn_topic_0150885187_table178824527142"></a>
<table><thead align="left"><tr id="zh-cn_topic_0150885187_row12882145215140"><th class="cellrowborder" valign="top" width="33.23%" id="mcps1.2.5.1.1"><p id="zh-cn_topic_0150885187_p18826529140"><a name="zh-cn_topic_0150885187_p18826529140"></a><a name="zh-cn_topic_0150885187_p18826529140"></a>存储类型</p>
</th>
<th class="cellrowborder" valign="top" width="19.89%" id="mcps1.2.5.1.2"><p id="zh-cn_topic_0150885187_p28820526146"><a name="zh-cn_topic_0150885187_p28820526146"></a><a name="zh-cn_topic_0150885187_p28820526146"></a>存储规格限制</p>
</th>
<th class="cellrowborder" valign="top" width="23.44%" id="mcps1.2.5.1.3"><p id="zh-cn_topic_0150885187_p58821552161412"><a name="zh-cn_topic_0150885187_p58821552161412"></a><a name="zh-cn_topic_0150885187_p58821552161412"></a>ext4规格限制</p>
</th>
<th class="cellrowborder" valign="top" width="23.44%" id="mcps1.2.5.1.4"><p id="zh-cn_topic_0150885187_p9882252201418"><a name="zh-cn_topic_0150885187_p9882252201418"></a><a name="zh-cn_topic_0150885187_p9882252201418"></a>CSI规格限制</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0150885187_row11882205261417"><td class="cellrowborder" valign="top" width="33.23%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0150885187_p1788211526142"><a name="zh-cn_topic_0150885187_p1788211526142"></a><a name="zh-cn_topic_0150885187_p1788211526142"></a>OceanStor Dorado</p>
</td>
<td class="cellrowborder" valign="top" width="19.89%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0150885187_p265163441310"><a name="zh-cn_topic_0150885187_p265163441310"></a><a name="zh-cn_topic_0150885187_p265163441310"></a>512Ki~256Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.44%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0150885187_p1988245219141"><a name="zh-cn_topic_0150885187_p1988245219141"></a><a name="zh-cn_topic_0150885187_p1988245219141"></a><span>50Ti</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.44%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0150885187_p15882185241416"><a name="zh-cn_topic_0150885187_p15882185241416"></a><a name="zh-cn_topic_0150885187_p15882185241416"></a>512Ki~50Ti</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row1230184492014"><td class="cellrowborder" valign="top" width="33.23%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0150885187_p9499133571212"><a name="zh-cn_topic_0150885187_p9499133571212"></a><a name="zh-cn_topic_0150885187_p9499133571212"></a>OceanStor Pacific系列</p>
</td>
<td class="cellrowborder" valign="top" width="19.89%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0150885187_p7650193417133"><a name="zh-cn_topic_0150885187_p7650193417133"></a><a name="zh-cn_topic_0150885187_p7650193417133"></a>64Mi~512Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.44%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0150885187_p1424338151414"><a name="zh-cn_topic_0150885187_p1424338151414"></a><a name="zh-cn_topic_0150885187_p1424338151414"></a><span>50Ti</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.44%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0150885187_p138617554183"><a name="zh-cn_topic_0150885187_p138617554183"></a><a name="zh-cn_topic_0150885187_p138617554183"></a>64Mi~50Ti</p>
</td>
</tr>
</tbody>
</table>

**表 3**  XFS容量的规格

<a name="zh-cn_topic_0150885187_table101951367104"></a>
<table><thead align="left"><tr id="zh-cn_topic_0150885187_row17195566105"><th class="cellrowborder" valign="top" width="33.07330733073307%" id="mcps1.2.5.1.1"><p id="zh-cn_topic_0150885187_p51951067101"><a name="zh-cn_topic_0150885187_p51951067101"></a><a name="zh-cn_topic_0150885187_p51951067101"></a>存储类型</p>
</th>
<th class="cellrowborder" valign="top" width="20.412041204120417%" id="mcps1.2.5.1.2"><p id="zh-cn_topic_0150885187_p141951062104"><a name="zh-cn_topic_0150885187_p141951062104"></a><a name="zh-cn_topic_0150885187_p141951062104"></a>存储规格限制</p>
</th>
<th class="cellrowborder" valign="top" width="23.512351235123514%" id="mcps1.2.5.1.3"><p id="zh-cn_topic_0150885187_p17195136151010"><a name="zh-cn_topic_0150885187_p17195136151010"></a><a name="zh-cn_topic_0150885187_p17195136151010"></a>XFS规格限制</p>
</th>
<th class="cellrowborder" valign="top" width="23.002300230023007%" id="mcps1.2.5.1.4"><p id="zh-cn_topic_0150885187_p1819520616108"><a name="zh-cn_topic_0150885187_p1819520616108"></a><a name="zh-cn_topic_0150885187_p1819520616108"></a>CSI规格限制</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0150885187_row12195156161015"><td class="cellrowborder" valign="top" width="33.07330733073307%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0150885187_p1919526121011"><a name="zh-cn_topic_0150885187_p1919526121011"></a><a name="zh-cn_topic_0150885187_p1919526121011"></a>OceanStor Dorado</p>
</td>
<td class="cellrowborder" valign="top" width="20.412041204120417%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0150885187_p131951613101"><a name="zh-cn_topic_0150885187_p131951613101"></a><a name="zh-cn_topic_0150885187_p131951613101"></a>512Ki~256Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.512351235123514%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0150885187_p919518613107"><a name="zh-cn_topic_0150885187_p919518613107"></a><a name="zh-cn_topic_0150885187_p919518613107"></a><span>500Ti</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.002300230023007%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0150885187_p15195865109"><a name="zh-cn_topic_0150885187_p15195865109"></a><a name="zh-cn_topic_0150885187_p15195865109"></a>512Ki~500Ti</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row171951969107"><td class="cellrowborder" valign="top" width="33.07330733073307%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0150885187_p1519514631010"><a name="zh-cn_topic_0150885187_p1519514631010"></a><a name="zh-cn_topic_0150885187_p1519514631010"></a>OceanStor Pacific系列</p>
</td>
<td class="cellrowborder" valign="top" width="20.412041204120417%" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0150885187_p1619519612104"><a name="zh-cn_topic_0150885187_p1619519612104"></a><a name="zh-cn_topic_0150885187_p1619519612104"></a>64Mi~512Ti</p>
</td>
<td class="cellrowborder" valign="top" width="23.512351235123514%" headers="mcps1.2.5.1.3 "><p id="zh-cn_topic_0150885187_p171963681017"><a name="zh-cn_topic_0150885187_p171963681017"></a><a name="zh-cn_topic_0150885187_p171963681017"></a><span>500Ti</span></p>
</td>
<td class="cellrowborder" valign="top" width="23.002300230023007%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0150885187_p3196126121011"><a name="zh-cn_topic_0150885187_p3196126121011"></a><a name="zh-cn_topic_0150885187_p3196126121011"></a>64Mi~500Ti</p>
</td>
</tr>
</tbody>
</table>

