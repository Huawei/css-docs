---
title: "查询PVC变更"
linkTitle: "查询PVC变更"
description: 
weight: 2
---

本章节介绍如何使用Kubectl查询PVC变更状态，当前华为CSI通过CRD提供以下API。

## 查询VolumeModifyClaim{#section8423141610284}

使用kubectl查询VolumeModifyClaim步骤如下。

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，查询PVC变更。其中 _vmc-name_ 为VolumeModifyClaim资源名称。

    ```
    kubectl get volumemodifyclaims <vmc-name> -owide
    ```

    命令结果示例如下：

    ```
    NAME    STATUS      READY   SOURCEKIND     SOURCENAME   STARTEDAT              COMPLETEDAT            AGE
    myvmc   Completed   1/1     StorageClass   mysc         2024-06-06T03:19:13Z   2024-06-06T03:19:16Z   2m2s
    ```

    **表 1**  回显说明

    <a name="table15212002358"></a>
    <table><thead align="left"><tr id="row1212190113511"><th class="cellrowborder" valign="top" width="17.740000000000002%" id="mcps1.2.3.1.1"><p id="p62126013351"><a name="p62126013351"></a><a name="p62126013351"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="82.26%" id="mcps1.2.3.1.2"><p id="p521215083520"><a name="p521215083520"></a><a name="p521215083520"></a>说明</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row182122006353"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p1321219018350"><a name="p1321219018350"></a><a name="p1321219018350"></a>NAME</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p172121408352"><a name="p172121408352"></a><a name="p172121408352"></a>VolumeModifyClaim资源名称。</p>
    </td>
    </tr>
    <tr id="row621260203510"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p102121105357"><a name="p102121105357"></a><a name="p102121105357"></a>STATUS</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p1121211063514"><a name="p1121211063514"></a><a name="p1121211063514"></a>VolumeModifyClaim资源状态，可取值如下：</p>
    <a name="ul1132773514478"></a><a name="ul1132773514478"></a><ul id="ul1132773514478"><li>Pending：初始状态。</li><li>Creating：VolumeModifyClaim完成基本校验，且服务端已经接收变更任务，但是该任务还未执行完成。</li><li>Completed：所有关联的PVC均完成变更。</li><li>Rollback：关联的PVC部分完成变更时，用户执行了删除PVC变更操作。</li><li>Deleting：关联的PVC全部完成变更时，用户执行了删除PVC变更操作。</li></ul>
    </td>
    </tr>
    <tr id="row2212101353"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p8212409353"><a name="p8212409353"></a><a name="p8212409353"></a>READY</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p1221220193511"><a name="p1221220193511"></a><a name="p1221220193511"></a>完成变更PVC数量/全部待变更PVC数量。</p>
    </td>
    </tr>
    <tr id="row1421300183510"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p16213190103516"><a name="p16213190103516"></a><a name="p16213190103516"></a>SOURCEKIND</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p52136013518"><a name="p52136013518"></a><a name="p52136013518"></a>数据源类型，例如StorageClass。</p>
    </td>
    </tr>
    <tr id="row20585173813548"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p65857385540"><a name="p65857385540"></a><a name="p65857385540"></a>SOURCENAME</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p11585123815543"><a name="p11585123815543"></a><a name="p11585123815543"></a>数据源名称，例如StorageClass名称。</p>
    </td>
    </tr>
    <tr id="row5936134120543"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p4936941165417"><a name="p4936941165417"></a><a name="p4936941165417"></a>STARTEDAT</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p1493624120545"><a name="p1493624120545"></a><a name="p1493624120545"></a>变更开始时间，指服务端接收该任务并开始处理的时间戳。</p>
    </td>
    </tr>
    <tr id="row1410514475419"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p9106944135414"><a name="p9106944135414"></a><a name="p9106944135414"></a>COMPLETEDAT</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p910664414546"><a name="p910664414546"></a><a name="p910664414546"></a>变更完成时间，指所有关联的PVC均完成变更后的时时间戳，仅STATUS为Completed时，存在该值。</p>
    </td>
    </tr>
    <tr id="row203380055616"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p8797114560"><a name="p8797114560"></a><a name="p8797114560"></a>AGE</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p1033919020567"><a name="p1033919020567"></a><a name="p1033919020567"></a>VolumeModifyClaim从创建至当前的存活时间。</p>
    </td>
    </tr>
    </tbody>
    </table>

>![](/public_sys-resources/zh/icon-note.gif) 
>VolumeModifyClaim支持使用kubectl查看Events信息，当VolumeModifyClaim无法满足创建要求，或者创建过程中出现错误时，服务端将记录Events信息。参考命令如下：
>```
>kubectl describe volumemodifyclaims local-to-hypermetro 
>```

## 查询VolumeModifyContent{#section215854219281}

VolumeModifyContent由VolumeModifyClaim资源创建，记录了单个PVC的变更详情，使用kubectl查询VolumeModifyContent步骤如下。

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行命令，查询PVC变更。其中myvmc-uid为VolumeModifyContent资源名称。

    ```
    kubectl get volumemodifycontents myvmc-uid  -owide
    ```

    命令结果示例如下：

    ```
    NAME         STATUS      MODIFYCLAIMNAME     SOURCEVOLUME   STARTEDAT              COMPLETEDAT            AGE
    myvmc-uid    Completed   myvmc               default/mypvc  2024-06-06T03:19:07Z   2024-06-06T03:19:09Z   36m
    ```

    **表 2**  回显说明

    <a name="table410118315599"></a>
    <table><thead align="left"><tr id="row2010116313592"><th class="cellrowborder" valign="top" width="17.740000000000002%" id="mcps1.2.3.1.1"><p id="p8102153145912"><a name="p8102153145912"></a><a name="p8102153145912"></a>名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="82.26%" id="mcps1.2.3.1.2"><p id="p111026317599"><a name="p111026317599"></a><a name="p111026317599"></a>说明</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row4102203155914"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p151022315915"><a name="p151022315915"></a><a name="p151022315915"></a>NAME</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p1910216317597"><a name="p1910216317597"></a><a name="p1910216317597"></a>VolumeModifyContent资源名称，格式为：VolumeModifyClaim名称-关联PVC的UID。</p>
    </td>
    </tr>
    <tr id="row5102133165919"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p1710233175911"><a name="p1710233175911"></a><a name="p1710233175911"></a>STATUS</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p610220365916"><a name="p610220365916"></a><a name="p610220365916"></a>VolumeModifyContent资源状态，可取值如下：</p>
    <a name="ul710223125912"></a><a name="ul710223125912"></a><ul id="ul710223125912"><li>Pending：初始状态。</li><li>Creating：VolumeModifyContent完成基本校验，且服务端已经接收变更任务，但是该任务还未执行完成。</li><li>Completed：关联的PVC完成变更。</li><li>Rollback：正在回滚PVC变更。</li></ul>
    </td>
    </tr>
    <tr id="row6102193175915"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p1610212345919"><a name="p1610212345919"></a><a name="p1610212345919"></a>MODIFYCLAIMNAME</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p910219314597"><a name="p910219314597"></a><a name="p910219314597"></a>关联的VolumeModifyClaim名称。</p>
    </td>
    </tr>
    <tr id="row1810220311598"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p410217312596"><a name="p410217312596"></a><a name="p410217312596"></a>SOURCEVOLUME</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p61021731593"><a name="p61021731593"></a><a name="p61021731593"></a>关联的PVC信息，格式为：命名空间名称/PVC名称。</p>
    </td>
    </tr>
    <tr id="row101021033597"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p1110214314598"><a name="p1110214314598"></a><a name="p1110214314598"></a>STARTEDAT</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p61023395918"><a name="p61023395918"></a><a name="p61023395918"></a>PVC变更开始时间，指服务端接收该任务并开始处理的时间戳。</p>
    </td>
    </tr>
    <tr id="row1310214345917"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p81021319598"><a name="p81021319598"></a><a name="p81021319598"></a>COMPLETEDAT</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p16102193165912"><a name="p16102193165912"></a><a name="p16102193165912"></a>PVC变更完成时间，指所有关联的PVC均完成变更后的时时间戳，仅STATUS为Completed时，存在该值。</p>
    </td>
    </tr>
    <tr id="row10102193195915"><td class="cellrowborder" valign="top" width="17.740000000000002%" headers="mcps1.2.3.1.1 "><p id="p010212395912"><a name="p010212395912"></a><a name="p010212395912"></a>AGE</p>
    </td>
    <td class="cellrowborder" valign="top" width="82.26%" headers="mcps1.2.3.1.2 "><p id="p1810211375912"><a name="p1810211375912"></a><a name="p1810211375912"></a>即VolumeModifyContent从创建至当前的存活时间。</p>
    </td>
    </tr>
    </tbody>
    </table>

>![](/public_sys-resources/zh/icon-note.gif) 
>VolumeModifyContent支持使用kubectl查看Events信息，当VolumeModifyContent无法满足创建要求，或者变更PVC出现错误时，服务端将记录Events信息。参考命令如下：
>```
>kubectl describe volumemodifycontents myvmc-uid
>```

