---
title: "Configuring PVC Changes"
linkTitle: "Configuring PVC Changes"
description: 
weight: 2
---

The PVC change feature is implemented using CRD. Related resources are described as follows.

**Table  1**  Resource description

<a name="table196975418221"></a>
<table><thead align="left"><tr id="row1769854112216"><th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.1"><p id="p116915422214"><a name="p116915422214"></a><a name="p116915422214"></a>NAME</p>
</th>
<th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.2"><p id="p1569254192210"><a name="p1569254192210"></a><a name="p1569254192210"></a>APIVERSION</p>
</th>
<th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.3"><p id="p96915547229"><a name="p96915547229"></a><a name="p96915547229"></a>NAMESPACED</p>
</th>
<th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.4"><p id="p369195482215"><a name="p369195482215"></a><a name="p369195482215"></a>KIND</p>
</th>
</tr>
</thead>
<tbody><tr id="row186965482219"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p16691054172211"><a name="p16691054172211"></a><a name="p16691054172211"></a>volumemodifyclaims</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.2 "><p id="p1869554182214"><a name="p1869554182214"></a><a name="p1869554182214"></a>xuanwu.huawei.io/v1</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.3 "><p id="p469454102215"><a name="p469454102215"></a><a name="p469454102215"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p26975442218"><a name="p26975442218"></a><a name="p26975442218"></a>VolumeModifyClaim</p>
</td>
</tr>
<tr id="row17691754122214"><td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.1 "><p id="p166925411229"><a name="p166925411229"></a><a name="p166925411229"></a>volumemodifycontents</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.2 "><p id="p499610812418"><a name="p499610812418"></a><a name="p499610812418"></a>xuanwu.huawei.io/v1</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.3 "><p id="p7996148132410"><a name="p7996148132410"></a><a name="p7996148132410"></a>false</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p969145482214"><a name="p969145482214"></a><a name="p969145482214"></a>VolumeModifyContent</p>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   VolumeModifyClaim resources can be created, deleted, and queried, but cannot be updated.
>-   VolumeModifyContent resources can only be queried and are used to display the change details of a single PVC. Do not manually create, delete, or modify the resources.
>-   VolumeModifyContent resources are managed by VolumeModifyClaim. Do not manually manage VolumeModifyContent resources.




