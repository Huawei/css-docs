---
title: "前言"
linkTitle: "前言"
description:
weight: 1
---

## 读者对象{#zh-cn_topic_0150885097_section1582418311113}

本文档主要适用于以下读者对象：

-   技术支持工程师
-   运维工程师
-   具备存储和Kubernetes基础知识的工程师

## 符号约定{#zh-cn_topic_0150885097_section992586151412}

在本文中可能出现下列标志，它们所代表的含义如下。

<a name="zh-cn_topic_0140239342_table1092583494419"></a>
<table><thead align="left"><tr id="zh-cn_topic_0140239342_row5925534194412"><th class="cellrowborder" valign="top" width="20.580000000000002%" id="mcps1.1.3.1.1"><p id="zh-cn_topic_0140239342_p392513413443"><a name="zh-cn_topic_0140239342_p392513413443"></a><a name="zh-cn_topic_0140239342_p392513413443"></a><strong id="zh-cn_topic_0140239342_b119258344448"><a name="zh-cn_topic_0140239342_b119258344448"></a><a name="zh-cn_topic_0140239342_b119258344448"></a>符号</strong></p>
</th>
<th class="cellrowborder" valign="top" width="79.42%" id="mcps1.1.3.1.2"><p id="zh-cn_topic_0140239342_p18925434144418"><a name="zh-cn_topic_0140239342_p18925434144418"></a><a name="zh-cn_topic_0140239342_p18925434144418"></a><strong id="zh-cn_topic_0140239342_b20925203484412"><a name="zh-cn_topic_0140239342_b20925203484412"></a><a name="zh-cn_topic_0140239342_b20925203484412"></a>说明</strong></p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0140239342_row199251834104413"><td class="cellrowborder" valign="top" width="20.580000000000002%" headers="mcps1.1.3.1.1 "><p id="zh-cn_topic_0140239342_p10925173420449"><a name="zh-cn_topic_0140239342_p10925173420449"></a><a name="zh-cn_topic_0140239342_p10925173420449"></a><a name="zh-cn_topic_0140239342_image19925163414449"></a><a name="zh-cn_topic_0140239342_image19925163414449"></a><span><img class="" id="zh-cn_topic_0140239342_image19925163414449" height="25.270000000000003" width="67.83" src="/css-docs/figures/zh-cn_image_0000002007964873.png"></span></p>
</td>
<td class="cellrowborder" valign="top" width="79.42%" headers="mcps1.1.3.1.2 "><p id="zh-cn_topic_0140239342_p1992520345443"><a name="zh-cn_topic_0140239342_p1992520345443"></a><a name="zh-cn_topic_0140239342_p1992520345443"></a>表示如不避免则将会导致死亡或严重伤害的具有高等级风险的危害。</p>
</td>
</tr>
<tr id="zh-cn_topic_0140239342_row1892553411445"><td class="cellrowborder" valign="top" width="20.580000000000002%" headers="mcps1.1.3.1.1 "><p id="zh-cn_topic_0140239342_p10925173434418"><a name="zh-cn_topic_0140239342_p10925173434418"></a><a name="zh-cn_topic_0140239342_p10925173434418"></a><a name="zh-cn_topic_0140239342_image10925183419447"></a><a name="zh-cn_topic_0140239342_image10925183419447"></a><span><img class="" id="zh-cn_topic_0140239342_image10925183419447" height="25.270000000000003" width="67.83" src="/css-docs/figures/zh-cn_image_0000001971484886.png"></span></p>
</td>
<td class="cellrowborder" valign="top" width="79.42%" headers="mcps1.1.3.1.2 "><p id="zh-cn_topic_0140239342_p09254345448"><a name="zh-cn_topic_0140239342_p09254345448"></a><a name="zh-cn_topic_0140239342_p09254345448"></a>表示如不避免则可能导致死亡或严重伤害的具有中等级风险的危害。</p>
</td>
</tr>
<tr id="zh-cn_topic_0140239342_row17925134134420"><td class="cellrowborder" valign="top" width="20.580000000000002%" headers="mcps1.1.3.1.1 "><p id="zh-cn_topic_0140239342_p209256341443"><a name="zh-cn_topic_0140239342_p209256341443"></a><a name="zh-cn_topic_0140239342_p209256341443"></a><a name="zh-cn_topic_0140239342_image3925834204416"></a><a name="zh-cn_topic_0140239342_image3925834204416"></a><span><img class="" id="zh-cn_topic_0140239342_image3925834204416" height="25.270000000000003" width="67.83" src="/css-docs/figures/zh-cn_image_0000001971325090.png"></span></p>
</td>
<td class="cellrowborder" valign="top" width="79.42%" headers="mcps1.1.3.1.2 "><p id="zh-cn_topic_0140239342_p39258341443"><a name="zh-cn_topic_0140239342_p39258341443"></a><a name="zh-cn_topic_0140239342_p39258341443"></a>表示如不避免则可能导致轻微或中度伤害的具有低等级风险的危害。</p>
</td>
</tr>
<tr id="zh-cn_topic_0140239342_row592583414414"><td class="cellrowborder" valign="top" width="20.580000000000002%" headers="mcps1.1.3.1.1 "><p id="zh-cn_topic_0140239342_p1292583414446"><a name="zh-cn_topic_0140239342_p1292583414446"></a><a name="zh-cn_topic_0140239342_p1292583414446"></a><a name="zh-cn_topic_0140239342_image392511343441"></a><a name="zh-cn_topic_0140239342_image392511343441"></a><span><img class="" id="zh-cn_topic_0140239342_image392511343441" height="25.270000000000003" width="67.83" src="/css-docs/figures/zh-cn_image_0000002007964889.png"></span></p>
</td>
<td class="cellrowborder" valign="top" width="79.42%" headers="mcps1.1.3.1.2 "><p id="zh-cn_topic_0140239342_p169258345447"><a name="zh-cn_topic_0140239342_p169258345447"></a><a name="zh-cn_topic_0140239342_p169258345447"></a>用于传递设备或环境安全警示信息。如不避免则可能会导致设备损坏、数据丢失、设备性能降低或其它不可预知的结果。</p>
<p id="zh-cn_topic_0140239342_p9925193454410"><a name="zh-cn_topic_0140239342_p9925193454410"></a><a name="zh-cn_topic_0140239342_p9925193454410"></a>“须知”不涉及人身伤害。</p>
</td>
</tr>
<tr id="zh-cn_topic_0140239342_row169251342440"><td class="cellrowborder" valign="top" width="20.580000000000002%" headers="mcps1.1.3.1.1 "><p id="zh-cn_topic_0140239342_p1192514346447"><a name="zh-cn_topic_0140239342_p1192514346447"></a><a name="zh-cn_topic_0140239342_p1192514346447"></a><a name="zh-cn_topic_0140239342_image18925234194414"></a><a name="zh-cn_topic_0140239342_image18925234194414"></a><span><img class="" id="zh-cn_topic_0140239342_image18925234194414" height="25.270000000000003" width="67.83" src="/css-docs/figures/zh-cn_image_0000002007845453.png"></span></p>
</td>
<td class="cellrowborder" valign="top" width="79.42%" headers="mcps1.1.3.1.2 "><p id="zh-cn_topic_0140239342_p1992511341444"><a name="zh-cn_topic_0140239342_p1992511341444"></a><a name="zh-cn_topic_0140239342_p1992511341444"></a>对正文中重点信息的补充说明。</p>
<p id="zh-cn_topic_0140239342_p9925434124419"><a name="zh-cn_topic_0140239342_p9925434124419"></a><a name="zh-cn_topic_0140239342_p9925434124419"></a>“说明”不是安全警示信息，不涉及人身、设备及环境伤害信息。</p>
</td>
</tr>
</tbody>
</table>
