---
title: "Downloading the Huawei CSI Software Package"
linkTitle: "Downloading the Huawei CSI Software Package"
description: 
weight: 1
---

This section describes how to download the software package and the component structure of the software package.

1.  Open a browser and enter  [https://github.com/Huawei/eSDK\_K8S\_Plugin/releases](https://github.com/Huawei/eSDK_K8S_Plugin/releases)  in the address box.
2.  Download the software package of the  4.5.0  version based on the CPU architecture.

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >Software package naming rule: Plug-in name \(**eSDK\_Huawei\_Storage\_Kubernetes\_CSI\_Plugin**\) + Version number + CPU architecture

3.  Decompress the downloaded software package. The following table shows the component structure of the software package.

    **Table  1**  Component description

    <a name="en-us_topic_0150885197_table17200162435412"></a>
    <table><thead align="left"><tr id="en-us_topic_0150885197_row6201202412546"><th class="cellrowborder" valign="top" width="37.43%" id="mcps1.2.3.1.1"><p id="en-us_topic_0150885197_p15201324135419"><a name="en-us_topic_0150885197_p15201324135419"></a><a name="en-us_topic_0150885197_p15201324135419"></a>Component</p>
    </th>
    <th class="cellrowborder" valign="top" width="62.57%" id="mcps1.2.3.1.2"><p id="en-us_topic_0150885197_p10201724105411"><a name="en-us_topic_0150885197_p10201724105411"></a><a name="en-us_topic_0150885197_p10201724105411"></a>Description</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row930973118310"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p230912312313"><a name="p230912312313"></a><a name="p230912312313"></a>image/huawei-csi-v<span id="ph1247142163214"><a name="ph1247142163214"></a><a name="ph1247142163214"></a>4.5.0</span>-<em id="i7879115512231"><a name="i7879115512231"></a><a name="i7879115512231"></a>arch</em>.tar</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p131017311931"><a name="p131017311931"></a><a name="p131017311931"></a>huawei-csi-driver image. <em id="i468114311317"><a name="i468114311317"></a><a name="i468114311317"></a>arch</em> is <strong id="b630516121316"><a name="b630516121316"></a><a name="b630516121316"></a>X86</strong> or <strong id="b59447711133"><a name="b59447711133"></a><a name="b59447711133"></a>ARM</strong>.</p>
    </td>
    </tr>
    <tr id="row1636415012105"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p236425091017"><a name="p236425091017"></a><a name="p236425091017"></a>image/storage-backend-controller-v<span id="ph16563185044814"><a name="ph16563185044814"></a><a name="ph16563185044814"></a>4.5.0</span>-<em id="i1580012569101"><a name="i1580012569101"></a><a name="i1580012569101"></a>arch</em>.tar</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p0364350161018"><a name="p0364350161018"></a><a name="p0364350161018"></a>Back-end management controller image. <em id="i5481153614711"><a name="i5481153614711"></a><a name="i5481153614711"></a>arch</em> is <strong id="b1481143624716"><a name="b1481143624716"></a><a name="b1481143624716"></a>X86</strong> or <strong id="b248110368473"><a name="b248110368473"></a><a name="b248110368473"></a>ARM</strong>.</p>
    </td>
    </tr>
    <tr id="row20811154791011"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p9811154713107"><a name="p9811154713107"></a><a name="p9811154713107"></a>image/storage-backend-sidecar-v<span id="ph0931352104814"><a name="ph0931352104814"></a><a name="ph0931352104814"></a>4.5.0</span>-<em id="i17458825101116"><a name="i17458825101116"></a><a name="i17458825101116"></a>arch</em>.tar</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p7811174751010"><a name="p7811174751010"></a><a name="p7811174751010"></a>Back-end management sidecar image. <em id="i113682409477"><a name="i113682409477"></a><a name="i113682409477"></a>arch</em> is <strong id="b1536814012479"><a name="b1536814012479"></a><a name="b1536814012479"></a>X86</strong> or <strong id="b9368164014718"><a name="b9368164014718"></a><a name="b9368164014718"></a>ARM</strong>.</p>
    </td>
    </tr>
    <tr id="row925351132220"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p32505182215"><a name="p32505182215"></a><a name="p32505182215"></a>image/huawei-csi-extender-v<span id="ph486705310481"><a name="ph486705310481"></a><a name="ph486705310481"></a>4.5.0</span>-<em id="i12719141202718"><a name="i12719141202718"></a><a name="i12719141202718"></a>arch</em>.tar</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p182585182214"><a name="p182585182214"></a><a name="p182585182214"></a>huawei-csi-extender image. <em id="i861363955118"><a name="i861363955118"></a><a name="i861363955118"></a>arch</em> is <strong id="b1961373914518"><a name="b1961373914518"></a><a name="b1961373914518"></a>X86</strong> or <strong id="b1961353913514"><a name="b1961353913514"></a><a name="b1961353913514"></a>ARM</strong>.</p>
    </td>
    </tr>
    <tr id="en-us_topic_0150885197_row132011024185415"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="en-us_topic_0150885197_p320102410540"><a name="en-us_topic_0150885197_p320102410540"></a><a name="en-us_topic_0150885197_p320102410540"></a>bin/</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="en-us_topic_0150885197_p720172417549"><a name="en-us_topic_0150885197_p720172417549"></a><a name="en-us_topic_0150885197_p720172417549"></a>Binary file used by an image provided by Huawei.</p>
    </td>
    </tr>
    <tr id="row1266918385217"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p566919345210"><a name="p566919345210"></a><a name="p566919345210"></a>bin/oceanctl</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p1966993195218"><a name="p1966993195218"></a><a name="p1966993195218"></a>Command line tool provided by Huawei, which can be used to manage storage backends.</p>
    </td>
    </tr>
    <tr id="en-us_topic_0150885197_row1745645113715"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="en-us_topic_0150885197_p164570514374"><a name="en-us_topic_0150885197_p164570514374"></a><a name="en-us_topic_0150885197_p164570514374"></a>helm/</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="en-us_topic_0150885197_p445715115370"><a name="en-us_topic_0150885197_p445715115370"></a><a name="en-us_topic_0150885197_p445715115370"></a>Helm project used to deploy Huawei CSI.</p>
    </td>
    </tr>
    <tr id="row1466517173816"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p104671317163816"><a name="p104671317163816"></a><a name="p104671317163816"></a>manual/</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p154672177382"><a name="p154672177382"></a><a name="p154672177382"></a>Used to manually install and deploy Huawei CSI.</p>
    </td>
    </tr>
    <tr id="en-us_topic_0150885197_row132192110373"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="en-us_topic_0150885197_p18220111117379"><a name="en-us_topic_0150885197_p18220111117379"></a><a name="en-us_topic_0150885197_p18220111117379"></a>examples/</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="en-us_topic_0150885197_p622091193716"><a name="en-us_topic_0150885197_p622091193716"></a><a name="en-us_topic_0150885197_p622091193716"></a>.yaml sample file used during CSI use.</p>
    </td>
    </tr>
    <tr id="row49534515549"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p14954195135418"><a name="p14954195135418"></a><a name="p14954195135418"></a>examples/backend</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p695405175411"><a name="p695405175411"></a><a name="p695405175411"></a>.yaml sample file used to create a storage backend.</p>
    </td>
    </tr>
    </tbody>
    </table>

