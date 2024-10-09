---
title: "Querying a PVC Change"
linkTitle: "Querying a PVC Change"
description: 
weight: 2
---

This section describes how to use Kubectl to query the PVC change status. Currently, Huawei CSI provides the following APIs through CRD.

## Querying a VolumeModifyClaim{#section8423141610284}

To query a VolumeModifyClaim using kubectl, perform the following steps.

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to query a PVC change. In the command,  _vmc-name_  indicates the name of the VolumeModifyClaim resource.

    ```
    kubectl get volumemodifyclaims <vmc-name> -owide
    ```

    The following is an example of the command output.

    ```
    NAME    STATUS      READY   SOURCEKIND     SOURCENAME   STARTEDAT              COMPLETEDAT            AGE
    myvmc   Completed   1/1     StorageClass   mysc         2024-06-06T03:19:13Z   2024-06-06T03:19:16Z   2m2s
    ```

    **Table  1**  Command output description

    <a name="table15212002358"></a>
    <table><thead align="left"><tr id="row1212190113511"><th class="cellrowborder" valign="top" width="28.000000000000004%" id="mcps1.2.3.1.1"><p id="p62126013351"><a name="p62126013351"></a><a name="p62126013351"></a>Parameter</p>
    </th>
    <th class="cellrowborder" valign="top" width="72%" id="mcps1.2.3.1.2"><p id="p521215083520"><a name="p521215083520"></a><a name="p521215083520"></a>Description</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row182122006353"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p1321219018350"><a name="p1321219018350"></a><a name="p1321219018350"></a>NAME</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p172121408352"><a name="p172121408352"></a><a name="p172121408352"></a>VolumeModifyClaim resource name.</p>
    </td>
    </tr>
    <tr id="row621260203510"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p102121105357"><a name="p102121105357"></a><a name="p102121105357"></a>STATUS</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p1121211063514"><a name="p1121211063514"></a><a name="p1121211063514"></a>VolumeModifyClaim resource status. The value can be:</p>
    <a name="ul1132773514478"></a><a name="ul1132773514478"></a><ul id="ul1132773514478"><li><strong id="b2201164825911"><a name="b2201164825911"></a><a name="b2201164825911"></a>Pending</strong>: initial status.</li><li><strong id="b1544124201"><a name="b1544124201"></a><a name="b1544124201"></a>Creating</strong>: The VolumeModifyClaim has completed basic verification and the server has received the change task, but the task has not been completed.</li><li><strong id="b1512131014020"><a name="b1512131014020"></a><a name="b1512131014020"></a>Completed</strong>: All associated PVCs are changed.</li><li><strong id="b19436191416019"><a name="b19436191416019"></a><a name="b19436191416019"></a>Rollback</strong>: When associated PVCs are partially changed, a user deletes PVCs.</li><li><strong id="b1076514581002"><a name="b1076514581002"></a><a name="b1076514581002"></a>Deleting</strong>: When all associated PVCs are changed, a user deletes PVCs.</li></ul>
    </td>
    </tr>
    <tr id="row2212101353"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p8212409353"><a name="p8212409353"></a><a name="p8212409353"></a>READY</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p1221220193511"><a name="p1221220193511"></a><a name="p1221220193511"></a>Ratio of the number of changed PVCs to the total number of PVCs that need to be changed.</p>
    </td>
    </tr>
    <tr id="row1421300183510"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p16213190103516"><a name="p16213190103516"></a><a name="p16213190103516"></a>SOURCEKIND</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p52136013518"><a name="p52136013518"></a><a name="p52136013518"></a>Data source type, for example, StorageClass.</p>
    </td>
    </tr>
    <tr id="row20585173813548"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p65857385540"><a name="p65857385540"></a><a name="p65857385540"></a>SOURCENAME</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p11585123815543"><a name="p11585123815543"></a><a name="p11585123815543"></a>Data source name, for example, StorageClass name.</p>
    </td>
    </tr>
    <tr id="row5936134120543"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p4936941165417"><a name="p4936941165417"></a><a name="p4936941165417"></a>STARTEDAT</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p1493624120545"><a name="p1493624120545"></a><a name="p1493624120545"></a>Change start time, that is, the timestamp when the server receives the task and starts to process the task.</p>
    </td>
    </tr>
    <tr id="row1410514475419"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p9106944135414"><a name="p9106944135414"></a><a name="p9106944135414"></a>COMPLETEDAT</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p910664414546"><a name="p910664414546"></a><a name="p910664414546"></a>Change completion time, that is, the timestamp when the changes of all associated PVCs are complete. This parameter exists only when <strong id="b3791144292114"><a name="b3791144292114"></a><a name="b3791144292114"></a>STATUS</strong> is <strong id="b1467015433212"><a name="b1467015433212"></a><a name="b1467015433212"></a>Completed</strong>.</p>
    </td>
    </tr>
    <tr id="row203380055616"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p8797114560"><a name="p8797114560"></a><a name="p8797114560"></a>AGE</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p1033919020567"><a name="p1033919020567"></a><a name="p1033919020567"></a>Lifetime of a VolumeModifyClaim from the time when it is created to the current time.</p>
    </td>
    </tr>
    </tbody>
    </table>

>![](/public_sys-resources/en/icon-note.gif)
>You can use kubectl to view the  **Events**  information of a VolumeModifyClaim. If a VolumeModifyClaim cannot meet the creation requirements or an error occurs during the creation, the server will record the  **Events**  information. The following command is used as an example:
>```
>kubectl describe volumemodifyclaims local-to-hypermetro 
>```

## Querying a VolumeModifyContent{#section215854219281}

A VolumeModifyContent is created using a VolumeModifyClaim and records the change details of a single PVC. To query a VolumeModifyContent using kubectl, perform the following steps:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to query a PVC change. In the command,  _myvmc-uid_  indicates the VolumeModifyContent resource name.

    ```
    kubectl get volumemodifycontents myvmc-uid  -owide
    ```

    The following is an example of the command output.

    ```
    NAME         STATUS      MODIFYCLAIMNAME     SOURCEVOLUME   STARTEDAT              COMPLETEDAT            AGE
    myvmc-uid    Completed   myvmc               default/mypvc  2024-06-06T03:19:07Z   2024-06-06T03:19:09Z   36m
    ```

    **Table  2**  Command output description

    <a name="table410118315599"></a>
    <table><thead align="left"><tr id="row2010116313592"><th class="cellrowborder" valign="top" width="28.000000000000004%" id="mcps1.2.3.1.1"><p id="p8102153145912"><a name="p8102153145912"></a><a name="p8102153145912"></a>Parameter</p>
    </th>
    <th class="cellrowborder" valign="top" width="72%" id="mcps1.2.3.1.2"><p id="p111026317599"><a name="p111026317599"></a><a name="p111026317599"></a>Description</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row4102203155914"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p151022315915"><a name="p151022315915"></a><a name="p151022315915"></a>NAME</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p1910216317597"><a name="p1910216317597"></a><a name="p1910216317597"></a>VolumeModifyContent resource name. The format is <em id="i18320184202510"><a name="i18320184202510"></a><a name="i18320184202510"></a>VolumeModifyClaim name</em><strong id="b10329115642415"><a name="b10329115642415"></a><a name="b10329115642415"></a>-</strong><em id="i1086101511252"><a name="i1086101511252"></a><a name="i1086101511252"></a>UID of the associated PVC</em>.</p>
    </td>
    </tr>
    <tr id="row5102133165919"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p1710233175911"><a name="p1710233175911"></a><a name="p1710233175911"></a>STATUS</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p610220365916"><a name="p610220365916"></a><a name="p610220365916"></a>VolumeModifyContent resource status. The value can be:</p>
    <a name="ul710223125912"></a><a name="ul710223125912"></a><ul id="ul710223125912"><li><strong id="b2022454925910"><a name="b2022454925910"></a><a name="b2022454925910"></a>Pending</strong>: initial status.</li><li><strong id="b32082421417"><a name="b32082421417"></a><a name="b32082421417"></a>Creating</strong>: The VolumeModifyContent has completed basic verification and the server has received the change task, but the task has not been completed.</li><li><strong id="b17820134716115"><a name="b17820134716115"></a><a name="b17820134716115"></a>Completed</strong>: The associated PVC is changed.</li><li><strong id="b07511112220"><a name="b07511112220"></a><a name="b07511112220"></a>Rollback</strong>: The PVC change is being rolled back.</li></ul>
    </td>
    </tr>
    <tr id="row6102193175915"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p1610212345919"><a name="p1610212345919"></a><a name="p1610212345919"></a>MODIFYCLAIMNAME</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p910219314597"><a name="p910219314597"></a><a name="p910219314597"></a>Name of the associated VolumeModifyClaim.</p>
    </td>
    </tr>
    <tr id="row1810220311598"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p410217312596"><a name="p410217312596"></a><a name="p410217312596"></a>SOURCEVOLUME</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p61021731593"><a name="p61021731593"></a><a name="p61021731593"></a>Information about the associated PVC. The format is <em id="i1236212515218"><a name="i1236212515218"></a><a name="i1236212515218"></a>Namespace name</em><strong id="b91641331424"><a name="b91641331424"></a><a name="b91641331424"></a>/</strong><em id="i10301328322"><a name="i10301328322"></a><a name="i10301328322"></a>PVC name</em>.</p>
    </td>
    </tr>
    <tr id="row101021033597"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p1110214314598"><a name="p1110214314598"></a><a name="p1110214314598"></a>STARTEDAT</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p61023395918"><a name="p61023395918"></a><a name="p61023395918"></a>PVC change start time, that is, the timestamp when the server receives the task and starts to process the task.</p>
    </td>
    </tr>
    <tr id="row1310214345917"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p81021319598"><a name="p81021319598"></a><a name="p81021319598"></a>COMPLETEDAT</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p16102193165912"><a name="p16102193165912"></a><a name="p16102193165912"></a>PVC change completion time, that is, the timestamp when the changes of all associated PVCs are complete. This parameter exists only when <strong id="b154417813264"><a name="b154417813264"></a><a name="b154417813264"></a>STATUS</strong> is <strong id="b74429815263"><a name="b74429815263"></a><a name="b74429815263"></a>Completed</strong>.</p>
    </td>
    </tr>
    <tr id="row10102193195915"><td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.3.1.1 "><p id="p010212395912"><a name="p010212395912"></a><a name="p010212395912"></a>AGE</p>
    </td>
    <td class="cellrowborder" valign="top" width="72%" headers="mcps1.2.3.1.2 "><p id="p1810211375912"><a name="p1810211375912"></a><a name="p1810211375912"></a>Lifetime of a VolumeModifyContent from the time when it is created to the current time.</p>
    </td>
    </tr>
    </tbody>
    </table>

>![](/public_sys-resources/en/icon-note.gif)
>You can use kubectl to view the  **Events**  information of a VolumeModifyContent. If a VolumeModifyContent cannot meet the creation requirements or an error occurs during the PVC change, the server will record the  **Events**  information. The following command is used as an example:
>```
>kubectl describe volumemodifycontents myvmc-uid
>```

