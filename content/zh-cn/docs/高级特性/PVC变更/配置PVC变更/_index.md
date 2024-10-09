---
title: "配置PVC变更"
linkTitle: "配置PVC变更"
description: 
weight: 2
---

PVC变更特性使用CRD实现，当前资源说明如下。

**表 1**  资源说明

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

>![](/public_sys-resources/zh/icon-note.gif) 
>-   VolumeModifyClaim资源支持创建/删除/查询，不支持更新。
>-   VolumeModifyContent资源仅支持查询，用于展示单个PVC变更详情，请勿手动创建/删除/修改。
>-   VolumeModifyContent资源被VolumeModifyClaim管理，请勿手动管理VolumeModifyContent资源。




