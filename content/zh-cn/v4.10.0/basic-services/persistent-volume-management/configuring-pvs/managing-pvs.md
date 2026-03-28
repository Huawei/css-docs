---
title: "纳管持久卷"
linkTitle: "纳管持久卷"
description: 
weight: 3
---

纳管卷供应（Manage Volume Provisioning）允许管理员使用已经在存储侧创建的资源做为PV，并能够支持动态卷的特性，例如：扩容，快照，克隆等，属于华为CSI自定义能力。使用该特性可满足如下场景：

-   容器化应用的改造场景，需要使用已有的存储卷。
-   重建Kubernetes集群。
-   容灾场景下，对存储数据进行迁移。

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>纳管卷供应支持将已有存储资源纳管至Kubernetes，不允许将一个存储资源纳管多次和针对同一个存储资源进行并发删除/创建操作。
>当同一个存储资源被多个集群纳管时，在单个集群中针对该纳管卷的操作仅在当前集群内生效，不会同步到其他集群中，需要使用者自行在其他集群中对该纳管卷进行数据同步操作。
>例如：在某一集群中对PVC进行扩容时，其他集群对应的PVC不会自动扩容，需要在其他集群中手动根据[扩容持久卷](/docs/basic-services/persistent-volume-management/managing-pvs-87/expanding-the-capacity-of-a-pv)中的扩容命令进行扩容。

## 配置说明{#section121779524353}

请根据以下步骤纳管使用持久卷：

-   [前置准备](#section65071656132313)
-   [配置PVC](#section979723473817)
-   [使用PVC](#section847932614377)

## 前置准备{#section65071656132313}

-   已在CSI中注册需要纳管卷所在存储。
-   已登录存储设备获取需要纳管卷的名称和容量。
-   已完成StorageClass的配置，参考[配置存储类](/docs/basic-services/storageclass-management/configuring-a-storageclass)（关注表格中的“纳管卷是否生效”字段）。

## 配置PVC{#section979723473817}

1.  准备PVC配置文件mypvc.yaml，示例如下，其他配置参数请参考[表1](#zh-cn_topic_0150885187_table195731435604)。

    ```yaml
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: mypvc
      annotations:
        csi.huawei.com/manageVolumeName: "*"  # 存储资源名称
        csi.huawei.com/manageBackendName: "*" # 存储后端名称
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

2.  执行命令，使用配置文件创建PVC。

    ```
    kubectl create -f mypvc.yaml
    ```

3.  等待一段时间后，执行以下命令，查看已经创建的PVC信息。

    ```
    kubectl get pvc mypvc
    ```

    命令结果示例如下，如果PVC的状态是“Bound”时，则说明该PVC已经创建成功，后续可以被Pod使用。

    ```
    NAME        STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
    mypvc       Bound    pvc-840054d3-1d5b-4153-b73f-826f980abf9e   100Gi      RWO            mysc           12s
    ```

    >![](/css-docs/public_sys-resources/zh-cn/icon-notice.gif)  
    >-   完成创建PVC操作后，如果长时间后（如一分钟后）PVC的状态是Pending，请参考[创建PVC时， PVC的状态为Pending](/docs/troubleshooting/pvc-issues/when-a-pvc-is-created-the-pvc-is-in-the-pending-state)。
    >-   建议每批次最多批量创建/删除100个PVC。

**表 1**  纳管持久卷PVC参数说明

<a name="zh-cn_topic_0150885187_table195731435604"></a>
<table><thead align="left"><tr id="zh-cn_topic_0150885187_row35732351904"><th class="cellrowborder" valign="top" width="13.47134713471347%" id="mcps1.2.6.1.1"><p id="zh-cn_topic_0150885187_p1257333517017"><a name="zh-cn_topic_0150885187_p1257333517017"></a><a name="zh-cn_topic_0150885187_p1257333517017"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="26.852685268526855%" id="mcps1.2.6.1.2"><p id="zh-cn_topic_0150885187_p1457323512015"><a name="zh-cn_topic_0150885187_p1457323512015"></a><a name="zh-cn_topic_0150885187_p1457323512015"></a>说明</p>
</th>
<th class="cellrowborder" valign="top" width="5.15051505150515%" id="mcps1.2.6.1.3"><p id="p19360047916"><a name="p19360047916"></a><a name="p19360047916"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="26.62266226622662%" id="mcps1.2.6.1.4"><p id="p9506371793"><a name="p9506371793"></a><a name="p9506371793"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="27.902790279027904%" id="mcps1.2.6.1.5"><p id="zh-cn_topic_0150885187_p85734352017"><a name="zh-cn_topic_0150885187_p85734352017"></a><a name="zh-cn_topic_0150885187_p85734352017"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row969014592044"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="p2690115912418"><a name="p2690115912418"></a><a name="p2690115912418"></a>metadata.annotations</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="p196189175512"><a name="p196189175512"></a><a name="p196189175512"></a>PVC对象的注释。配置以下参数：</p>
<a name="ul411121811565"></a><a name="ul411121811565"></a><ul id="ul411121811565"><li>驱动名称/manageVolumeName：卷在存储侧的名称。</li><li>驱动名称/manageBackendName：卷所属后端的名称。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p15360547910"><a name="p15360547910"></a><a name="p15360547910"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p8502191171218"><a name="p8502191171218"></a><a name="p8502191171218"></a>csi.huawei.com/manageVolumeName: *    csi.huawei.com/manageBackendName: *</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><a name="ul44235513567"></a><a name="ul44235513567"></a><ul id="ul44235513567"><li>驱动名称获取请参考<a href="/css-docs/docs/installation-and-deployment/csi/installation/installation-using-helm/parameters-in-the-values-yaml-file-of-helm#table188162213437">表4</a>。</li><li>驱动名称/manageVolumeName：为存储上已有卷的名称，除英文字符外，其他国家字符不支持。</li><li>驱动名称/manageBackendName：CSI中存储后端的名称。</li></ul>
<p id="p176901459748"><a name="p176901459748"></a><a name="p176901459748"></a>可执行<strong id="b128931112571"><a name="b128931112571"></a><a name="b128931112571"></a>oceanctl get backend -n huawei-csi</strong>命令获取后端名称。</p>
</td>
</tr>
<tr id="row13644161649"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="p7644961942"><a name="p7644961942"></a><a name="p7644961942"></a>metadata.labels</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="p364436542"><a name="p364436542"></a><a name="p364436542"></a>PVC对象的标签。</p>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p3360941498"><a name="p3360941498"></a><a name="p3360941498"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p10506117498"><a name="p10506117498"></a><a name="p10506117498"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p168401138144212"><a name="p168401138144212"></a><a name="p168401138144212"></a>格式：provisioner: 安装时指定的驱动名称。</p>
<p id="p1067565015410"><a name="p1067565015410"></a><a name="p1067565015410"></a>例如 provisioner: csi.huawei.com。</p>
<p id="p19806312144118"><a name="p19806312144118"></a><a name="p19806312144118"></a>该参数在创建PVC时生效，用于监听PVC资源，获取metadata.annotations信息。</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row5573635907"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p3573335305"><a name="zh-cn_topic_0150885187_p3573335305"></a><a name="zh-cn_topic_0150885187_p3573335305"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0150885187_p205736355017"><a name="zh-cn_topic_0150885187_p205736355017"></a><a name="zh-cn_topic_0150885187_p205736355017"></a>自定义的PVC对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p1736019415915"><a name="p1736019415915"></a><a name="p1736019415915"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p1506677916"><a name="p1506677916"></a><a name="p1506677916"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p20875193814315"><a name="p20875193814315"></a><a name="p20875193814315"></a>以Kubernetes v1.22.1为例，支持数字、小写字母、中划线（-）和点（.）的组合，并且必须以字母数字开头和结尾。</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row696316316238"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p1896393118231"><a name="zh-cn_topic_0150885187_p1896393118231"></a><a name="zh-cn_topic_0150885187_p1896393118231"></a>spec.volumeMode</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="p1610614478451"><a name="p1610614478451"></a><a name="p1610614478451"></a>卷模式。可选参数。 当使用LUN类型的卷时，支持配置以下类型：</p>
<a name="ul823916101324"></a><a name="ul823916101324"></a><ul id="ul823916101324"><li>Filesystem：本地文件系统。</li><li>Block：裸设备。</li></ul>
<div class="note" id="note186041413175913"><a name="note186041413175913"></a><a name="note186041413175913"></a><span class="notetitle"> 说明： </span><div class="notebody"><p id="p156042013105912"><a name="p156042013105912"></a><a name="p156042013105912"></a>该参数在挂载PV时生效，需要与纳管卷的使用方式保持一致。</p>
<a name="ul10185528135916"></a><a name="ul10185528135916"></a><ul id="ul10185528135916"><li>如果卷纳管之前是以裸卷方式使用，volumeMode必须配置为Block。</li><li>如果卷纳管之前是以ext2/ext3/ext4方式使用，volumeMode必须配置为Filesystem，且StorageClass中fsType必须指定为ext2/ext3/ext4。</li><li>如果卷纳管之前是以XFS方式使用，volumeMode必须配置为Filesystem，且StorageClass中fsType必须指定为xfs。</li></ul>
</div></div>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p153606414917"><a name="p153606414917"></a><a name="p153606414917"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p55061271915"><a name="p55061271915"></a><a name="p55061271915"></a>Filesystem</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p62045214421"><a name="p62045214421"></a><a name="p62045214421"></a>该参数在挂载PV时生效。</p>
<a name="ul1518211174214"></a><a name="ul1518211174214"></a><ul id="ul1518211174214"><li>Filesystem表示在容器通过一个本地文件系统访问PV，本地文件系统类型为指定StorageClass中的fsType字段指定。</li><li>Block表示使用裸卷的方式访问访问PV。</li></ul>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row25733352019"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p357320351304"><a name="zh-cn_topic_0150885187_p357320351304"></a><a name="zh-cn_topic_0150885187_p357320351304"></a>spec.storageClassName</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0150885187_p135732351909"><a name="zh-cn_topic_0150885187_p135732351909"></a><a name="zh-cn_topic_0150885187_p135732351909"></a>StorageClass对象名称。</p>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p1736015413918"><a name="p1736015413918"></a><a name="p1736015413918"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p195061171092"><a name="p195061171092"></a><a name="p195061171092"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p1521791621216"><a name="p1521791621216"></a><a name="p1521791621216"></a>StorageClass的配置需要与纳管卷的配置保持一致。</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row1157316351102"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p9573035309"><a name="zh-cn_topic_0150885187_p9573035309"></a><a name="zh-cn_topic_0150885187_p9573035309"></a>spec.resources.requests.storage</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0150885187_p1573183510015"><a name="zh-cn_topic_0150885187_p1573183510015"></a><a name="zh-cn_topic_0150885187_p1573183510015"></a>指定待创建卷大小，格式为***Gi，单位为GiB。</p>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p1436044990"><a name="p1436044990"></a><a name="p1436044990"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p18506147494"><a name="p18506147494"></a><a name="p18506147494"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><p id="p1525217519276"><a name="p1525217519276"></a><a name="p1525217519276"></a>PVC容量的规格取决于存储规格限制和主机规格限制。以OceanStor Dorado 6.1.2/OceanStor Pacific系列 8.1.0对接CentOS 7为例，当使用的是ext4文件系统时，容量限制见<a href="/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#zh-cn_topic_0150885187_table178824527142">表2</a>；当使用的是XFS文件系统时，容量限制见<a href="/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#zh-cn_topic_0150885187_table101951367104">表3</a>。如果使用的是NFS或者裸设备，容量需满足使用的华为存储设备型号和版本所要求的规格约束。</p>
<p id="p63667162711"><a name="p63667162711"></a><a name="p63667162711"></a>如果PVC容量不在规格范围内，可能会由于存储规格限制或主机文件系统规格限制导致创建PVC或Pod失败。</p>
</td>
</tr>
<tr id="zh-cn_topic_0150885187_row6573635502"><td class="cellrowborder" valign="top" width="13.47134713471347%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0150885187_p1657333515012"><a name="zh-cn_topic_0150885187_p1657333515012"></a><a name="zh-cn_topic_0150885187_p1657333515012"></a>spec.accessModes</p>
</td>
<td class="cellrowborder" valign="top" width="26.852685268526855%" headers="mcps1.2.6.1.2 "><p id="p51122302293"><a name="p51122302293"></a><a name="p51122302293"></a>指定卷访问模式。</p>
<a name="ul69743301323"></a><a name="ul69743301323"></a><ul id="ul69743301323"><li><span>RWO</span>（ReadWriteOnce）：卷可以被一个节点以读写方式挂载。 该模式也允许运行在同一节点上的多个 Pod 访问卷。</li><li><span>ROX</span>（ReadOnlyMany）：卷可以被多个节点以只读方式挂载。</li><li><span>RWX</span>（ReadWriteMany）：卷可以被多个节点以读写方式挂载。</li><li><span>RWOP</span>（ReadWriteOncePod）：卷只能被单个 Pod 以读写方式挂载。该特性需要 Kubernetes 1.22 以上版本。</li></ul>
</td>
<td class="cellrowborder" valign="top" width="5.15051505150515%" headers="mcps1.2.6.1.3 "><p id="p10360448912"><a name="p10360448912"></a><a name="p10360448912"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="26.62266226622662%" headers="mcps1.2.6.1.4 "><p id="p65069712920"><a name="p65069712920"></a><a name="p65069712920"></a>ReadWriteOnce</p>
</td>
<td class="cellrowborder" valign="top" width="27.902790279027904%" headers="mcps1.2.6.1.5 "><a name="ul16793434324"></a><a name="ul16793434324"></a><ul id="ul16793434324"><li><span>RWO/ROX/RWOP：</span>所有类型卷均支持，<span>RWOP</span>需<span>Kubernetes 1.22</span>版本以上支持。Kubernetes 1.29版本以下需要参考<a href="/css-docs/docs/common-o-m-operations/enabling-the-readwriteoncepod-feature-gate">开启ReadWriteOncePod功能门</a>章节开启该特性。</li><li><span>RWX</span>支持情况如下：<a name="ul10813936394"></a><a name="ul10813936394"></a><ul id="ul10813936394"><li>NAS存储：所有卷均支持。</li><li>SAN存储：仅volumeMode设置为Block的卷支持。</li></ul>
</li></ul>
</td>
</tr>
</tbody>
</table>

## 使用PVC{#section847932614377}

与动态卷供应[使用PVC](/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#section8172141413917)方式相同。

