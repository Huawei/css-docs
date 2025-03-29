---
title: "静态卷供应PV参数说明"
linkTitle: "静态卷供应PV参数说明"
description: 
weight: 1
---

**表 1**  静态卷供应参数

<a name="zh-cn_topic_0000001255922865_table055742511559"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001255922865_row555722555518"><th class="cellrowborder" valign="top" width="17.687074829931973%" id="mcps1.2.6.1.1"><p id="zh-cn_topic_0000001255922865_p1257333517017"><a name="zh-cn_topic_0000001255922865_p1257333517017"></a><a name="zh-cn_topic_0000001255922865_p1257333517017"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="28.49368318756074%" id="mcps1.2.6.1.2"><p id="zh-cn_topic_0000001255922865_p1457323512015"><a name="zh-cn_topic_0000001255922865_p1457323512015"></a><a name="zh-cn_topic_0000001255922865_p1457323512015"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="6.802721088435375%" id="mcps1.2.6.1.3"><p id="p153581815174412"><a name="p153581815174412"></a><a name="p153581815174412"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="13.80952380952381%" id="mcps1.2.6.1.4"><p id="p135944173447"><a name="p135944173447"></a><a name="p135944173447"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="33.20699708454811%" id="mcps1.2.6.1.5"><p id="zh-cn_topic_0000001255922865_p85734352017"><a name="zh-cn_topic_0000001255922865_p85734352017"></a><a name="zh-cn_topic_0000001255922865_p85734352017"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000001255922865_row955713252557"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p3573335305"><a name="zh-cn_topic_0150885187_p3573335305"></a><a name="zh-cn_topic_0150885187_p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0150885187_p205736355017"><a name="zh-cn_topic_0150885187_p205736355017"></a><a name="zh-cn_topic_0150885187_p205736355017"></a>自定义的PV对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p935815152442"><a name="p935815152442"></a><a name="p935815152442"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p4594101744415"><a name="p4594101744415"></a><a name="p4594101744415"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0150885187_p179301591191"><a name="zh-cn_topic_0150885187_p179301591191"></a><a name="zh-cn_topic_0150885187_p179301591191"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001255922865_row16557202515555"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p1896393118231"><a name="zh-cn_topic_0150885187_p1896393118231"></a><a name="zh-cn_topic_0150885187_p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p1610614478451"><a name="p1610614478451"></a><a name="p1610614478451"></a>卷模式。可选参数。 当使用LUN类型的卷时，支持配置以下类型：</p>
<a name="ul550911281034"></a><a name="ul550911281034"></a><ul id="ul550911281034"><li>Filesystem：本地文件系统。</li><li>Block：裸设备。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p183583151446"><a name="p183583151446"></a><a name="p183583151446"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p1779184518303"><a name="p1779184518303"></a><a name="p1779184518303"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p62045214421"><a name="p62045214421"></a><a name="p62045214421"></a>该参数在挂载PV时生效，默认为Filesystem。</p>
<a name="ul1527393212316"></a><a name="ul1527393212316"></a><ul id="ul1527393212316"><li>Filesystem表示在容器通过一个本地文件系统访问PV，本地文件系统类型为指定StorageClass中的fsType字段指定。</li><li>Block表示使用裸卷的方式访问访问PV。</li></ul>
</td>
</tr>
<tr id="zh-cn_topic_0000001255922865_row5486654134918"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001255922865_p357320351304"><a name="zh-cn_topic_0000001255922865_p357320351304"></a><a name="zh-cn_topic_0000001255922865_p357320351304"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001255922865_p135732351909"><a name="zh-cn_topic_0000001255922865_p135732351909"></a><a name="zh-cn_topic_0000001255922865_p135732351909"></a>StorageClass对象名称。必选参数。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p83581015194419"><a name="p83581015194419"></a><a name="p83581015194419"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p85951917184420"><a name="p85951917184420"></a><a name="p85951917184420"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001255922865_p1139501413438"><a name="zh-cn_topic_0000001255922865_p1139501413438"></a><a name="zh-cn_topic_0000001255922865_p1139501413438"></a>此处须设置为空字符串（即输入""）。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001255922865_row755722515552"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p1657333515012"><a name="zh-cn_topic_0150885187_p1657333515012"></a><a name="zh-cn_topic_0150885187_p1657333515012"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p51122302293"><a name="p51122302293"></a><a name="p51122302293"></a>指定卷访问模式。</p>
<a name="ul989211520315"></a><a name="ul989211520315"></a><ul id="ul989211520315"><li><span>RWO</span>（ReadWriteOnce）：卷可以被一个节点以读写方式挂载。 该模式也允许运行在同一节点上的多个 Pod 访问卷。</li><li><span>ROX</span>（ReadOnlyMany）：卷可以被多个节点以只读方式挂载。</li><li><span>RWX</span>（ReadWriteMany）：卷可以被多个节点以读写方式挂载。</li><li><span>RWOP</span>（ReadWriteOncePod）：卷只能被单个 Pod 以读写方式挂载。该特性需要 Kubernetes 1.22 以上版本。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p11358015174414"><a name="p11358015174414"></a><a name="p11358015174414"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p1959571724410"><a name="p1959571724410"></a><a name="p1959571724410"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><a name="ul13431556330"></a><a name="ul13431556330"></a><ul id="ul13431556330"><li><span>RWO/ROX/RWOP：</span>所有类型卷均支持，<span>RWOP</span>需<span>Kubernetes 1.22</span>版本以上支持。请参考<a href="/css-docs/docs/common-operations/enabling-the-readwriteoncepod-feature-gate">开启ReadWriteOncePod功能门</a>章节，检查您的<span>Kubernetes</span>集群是否开启该特性。</li><li><span>RWX</span>支持情况如下：<a name="ul201701421154515"></a><a name="ul201701421154515"></a><ul id="ul201701421154515"><li><a href="/css-docs/docs/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#li277121152812">NAS存储</a>：所有卷均支持。</li><li><a href="/css-docs/docs/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters#zh-cn_topic_0000001324610777_li5135242193418">SAN存储</a>：仅volumeMode设置为Block的卷支持。</li></ul>
</li></ul>
</td>
</tr>
<tr id="zh-cn_topic_0000001255922865_row9557202575510"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001255922865_p155717257554"><a name="zh-cn_topic_0000001255922865_p155717257554"></a><a name="zh-cn_topic_0000001255922865_p155717257554"></a>spec.csi.driver</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001255922865_p5557025165510"><a name="zh-cn_topic_0000001255922865_p5557025165510"></a><a name="zh-cn_topic_0000001255922865_p5557025165510"></a>CSI驱动名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p935821564411"><a name="p935821564411"></a><a name="p935821564411"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p059518172448"><a name="p059518172448"></a><a name="p059518172448"></a>csi.huawei.com</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001255922865_p25576254553"><a name="zh-cn_topic_0000001255922865_p25576254553"></a><a name="zh-cn_topic_0000001255922865_p25576254553"></a>该字段需要指定为安装华为CSI时设置的驱动名称。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001255922865_row18141551408"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001255922865_p141411251907"><a name="zh-cn_topic_0000001255922865_p141411251907"></a><a name="zh-cn_topic_0000001255922865_p141411251907"></a>spec.csi.volumeHandle</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p10302308143"><a name="p10302308143"></a><a name="p10302308143"></a>存储资源的唯一标志。必选参数。</p>
<p id="zh-cn_topic_0000001255922865_p2141135115012"><a name="zh-cn_topic_0000001255922865_p2141135115012"></a><a name="zh-cn_topic_0000001255922865_p2141135115012"></a>格式为：&lt;backendName&gt;.&lt;volume-name&gt;</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p10358141513449"><a name="p10358141513449"></a><a name="p10358141513449"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p11595121794411"><a name="p11595121794411"></a><a name="p11595121794411"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001255922865_p105611631131211"><a name="zh-cn_topic_0000001255922865_p105611631131211"></a><a name="zh-cn_topic_0000001255922865_p105611631131211"></a>该参数值由以下两部分构成：</p>
<a name="zh-cn_topic_0000001255922865_ul317520442816"></a><a name="zh-cn_topic_0000001255922865_ul317520442816"></a><ul id="zh-cn_topic_0000001255922865_ul317520442816"><li>&lt;backendName&gt;：该卷所在的后端名称，可使用如下命令获取配置的后端信息：<p id="p101424597119"><a name="p101424597119"></a><a name="p101424597119"></a><strong id="b1736283518212"><a name="b1736283518212"></a><a name="b1736283518212"></a>oceanctl get backend</strong></p>
</li><li>&lt;volume-name&gt;：存储上资源（LUN/文件系统）的名称，可通过DeviceManager查看。</li></ul>
</td>
</tr>
<tr id="zh-cn_topic_0000001255922865_row197581481108"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001255922865_p110831210"><a name="zh-cn_topic_0000001255922865_p110831210"></a><a name="zh-cn_topic_0000001255922865_p110831210"></a>spec.csi.fsType</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p648319179411"><a name="p648319179411"></a><a name="p648319179411"></a>指定主机文件系统类型。可选参数。支持类型为：</p>
<a name="ul35039276418"></a><a name="ul35039276418"></a><ul id="ul35039276418"><li>ext2</li><li>ext3</li><li>ext4</li><li>xfs</li></ul>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1735841534417"><a name="p1735841534417"></a><a name="p1735841534417"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p1959531715445"><a name="p1959531715445"></a><a name="p1959531715445"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p748584017914"><a name="p748584017914"></a><a name="p748584017914"></a>如果不设置，默认为ext4。仅当volumeMode配置为“Filesystem”时生效。</p>
</td>
</tr>
<tr id="row1894264183210"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p1294211453210"><a name="p1294211453210"></a><a name="p1294211453210"></a>spec.csi.volumeAttributes.dTreeParentName</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p189421447325"><a name="p189421447325"></a><a name="p189421447325"></a>卷资源类型为DTree时，其父文件系统名称。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1694217415328"><a name="p1694217415328"></a><a name="p1694217415328"></a>条件必选</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p169421345328"><a name="p169421345328"></a><a name="p169421345328"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p139424420325"><a name="p139424420325"></a><a name="p139424420325"></a>纳管对象为DTree资源，且存储后端中未配置parentname参数时，必须配置该参数。</p>
<p id="p1545865605919"><a name="p1545865605919"></a><a name="p1545865605919"></a>若仅在PV中配置了dTreeParentName，而对应的存储后端中未配置parentname时，要求在安装CSI时根据<a href="/css-docs/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table258712427285">表5</a>将CSIDriverObject.attachRequired设置为true。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001255922865_row1455742510558"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001255922865_p055732595515"><a name="zh-cn_topic_0000001255922865_p055732595515"></a><a name="zh-cn_topic_0000001255922865_p055732595515"></a>spec.capacity.storage</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001255922865_p1573183510015"><a name="zh-cn_topic_0000001255922865_p1573183510015"></a><a name="zh-cn_topic_0000001255922865_p1573183510015"></a>指定卷大小。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1035831513448"><a name="p1035831513448"></a><a name="p1035831513448"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p659511704418"><a name="p659511704418"></a><a name="p659511704418"></a>100Gi</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001255922865_p6871647174317"><a name="zh-cn_topic_0000001255922865_p6871647174317"></a><a name="zh-cn_topic_0000001255922865_p6871647174317"></a>请确保与存储上对应资源的容量保持一致。Kubernetes并不会调用CSI检查此字段值的正确性，所以在PV容量与存储上对应资源的容量不一致也能被成功创建。</p>
</td>
</tr>
<tr id="row160819410575"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p1036995916474"><a name="p1036995916474"></a><a name="p1036995916474"></a>spec.mountOptions.nfsvers</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p16369105917476"><a name="p16369105917476"></a><a name="p16369105917476"></a>主机侧NFS挂载选项。支持如下挂载选项：</p>
<p id="p3366172411524"><a name="p3366172411524"></a><a name="p3366172411524"></a>nfsvers：挂载NFS时的协议版本。支持配置的参数值为“3”，“4”，“4.0”，“4.1”和“4.2”。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p7358615164410"><a name="p7358615164410"></a><a name="p7358615164410"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p95951917154413"><a name="p95951917154413"></a><a name="p95951917154413"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p775515413439"><a name="p775515413439"></a><a name="p775515413439"></a>在主机执行mount命令时-o参数后的可选选项。列表格式。</p>
<p id="p486929143316"><a name="p486929143316"></a><a name="p486929143316"></a>指定NFS版本挂载时，当前支持NFS 3/4.0/4.1/4.2协议（需存储设备支持且开启）。当配置参数为nfsvers=4时，因为操作系统配置的不同，实际挂载可能为NFS 4的最高版本协议，如4.2，当需要使用4.0协议时，建议配置nfsvers=4.0。</p>
</td>
</tr>
<tr id="row19538145720"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p743994313307"><a name="p743994313307"></a><a name="p743994313307"></a>spec.mountOptions.acl</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p7439243173012"><a name="p7439243173012"></a><a name="p7439243173012"></a>DPC命名空间支持ACL功能。DPC客户端支持POSIX ACL、NFSv4 ACL、NT ACL的鉴权行为。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1335861512440"><a name="p1335861512440"></a><a name="p1335861512440"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p12595121774413"><a name="p12595121774413"></a><a name="p12595121774413"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p1451716198319"><a name="p1451716198319"></a><a name="p1451716198319"></a>acl、aclonlyposix、cnflush、cflush参数描述仅供参考，详细参数说明请参考<a href="https://support.huawei.com/enterprise/zh/distributed-storage/oceanstor-pacific-9520-pid-251711061" target="_blank" rel="noopener noreferrer">《OceanStor Pacific系列 产品文档》</a> &gt; 配置 &gt; 文件服务基础业务配置指南 &gt; 配置基础业务（DPC场景） &gt; 客户端访问DPC共享 &gt; 步骤2。</p>
</td>
</tr>
<tr id="row1046785975611"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p184399439309"><a name="p184399439309"></a><a name="p184399439309"></a>spec.mountOptions.aclonlyposix</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p13950103563719"><a name="p13950103563719"></a><a name="p13950103563719"></a>DPC命名空间支持POSIX ACL功能，DPC客户端支持POSIX ACL的鉴权行为。</p>
<p id="p1943913439308"><a name="p1943913439308"></a><a name="p1943913439308"></a>支持POSIX ACL的协议有：DPC、NFSv3、HDFS。如使用NFSv4 ACL或NT ACL，会导致DPC客户端无法识别该类型的ACL，从而导致该类型的ACL不会生效。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p2358191544418"><a name="p2358191544418"></a><a name="p2358191544418"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p65951417164420"><a name="p65951417164420"></a><a name="p65951417164420"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p718315423511"><a name="p718315423511"></a><a name="p718315423511"></a>aclonlyposix与acl参数同时使用时，仅acl参数生效，即命名空间支持ACL功能。</p>
</td>
</tr>
<tr id="row10116155295616"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p867705717358"><a name="p867705717358"></a><a name="p867705717358"></a>spec.mountOptions.cnflush</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p7533510163615"><a name="p7533510163615"></a><a name="p7533510163615"></a>异步刷盘模式，即关闭命名空间下的文件时不会立即刷盘。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p835881513448"><a name="p835881513448"></a><a name="p835881513448"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p1159501724414"><a name="p1159501724414"></a><a name="p1159501724414"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p46771657123516"><a name="p46771657123516"></a><a name="p46771657123516"></a>异步刷盘模式，当文件关闭时不会同步将Cache的数据持久化到存储介质中，而是通过Cache异步刷盘的方式将数据写入存储介质，Cache的后台刷盘将在写业务完成后根据刷盘周期定时刷盘。在多客户端场景下，对同一文件进行并行操作，文件Size的更新会受刷盘周期的影响，即当刷盘动作完成后才会更新文件的Size，更新通常会在数秒内完成。同步I/O不受刷盘周期影响。</p>
</td>
</tr>
<tr id="row9773155135618"><td class="cellrowborder" valign="top" width="17.687074829931973%" headers="mcps1.2.6.1.1 "><p id="p13444191520365"><a name="p13444191520365"></a><a name="p13444191520365"></a>spec.mountOptions.cflush</p>
</td>
<td class="cellrowborder" valign="top" width="28.49368318756074%" headers="mcps1.2.6.1.2 "><p id="p194444156366"><a name="p194444156366"></a><a name="p194444156366"></a>同步刷盘模式，即关闭命名空间下的文件时立即刷盘。</p>
</td>
<td class="cellrowborder" valign="top" width="6.802721088435375%" headers="mcps1.2.6.1.3 "><p id="p1835861516442"><a name="p1835861516442"></a><a name="p1835861516442"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="13.80952380952381%" headers="mcps1.2.6.1.4 "><p id="p35951517104413"><a name="p35951517104413"></a><a name="p35951517104413"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="33.20699708454811%" headers="mcps1.2.6.1.5 "><p id="p18444315183615"><a name="p18444315183615"></a><a name="p18444315183615"></a>默认使用同步刷盘模式。</p>
</td>
</tr>
</tbody>
</table>

