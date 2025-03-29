---
title: "下载华为CSI软件包"
linkTitle: "下载华为CSI软件包"
description: 
weight: 1
---

本章节详细说明了下载方法以及软件包组件结构。

1.  打开浏览器，访问仓库地址：[https://github.com/Huawei/eSDK\_K8S\_Plugin/releases](https://github.com/Huawei/eSDK_K8S_Plugin/releases)。
2.  根据CPU架构，下载对应的4.6.0版本软件包。

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >软件包命名规范：插件名称（eSDK\_Huawei\_Storage\_Kubernetes\_CSI\_Plugin）+版本号+CPU架构。
    >CSI支持的CPU架构包括：X86、ARM和PPC64LE。

3.  将下载的软件包解压。软件包组件结构如下表所示。

    **表 1**  软件包组件描述

    <a name="zh-cn_topic_0150885197_table17200162435412"></a>
    <table><thead align="left"><tr id="zh-cn_topic_0150885197_row6201202412546"><th class="cellrowborder" valign="top" width="37.43%" id="mcps1.2.3.1.1"><p id="zh-cn_topic_0150885197_p15201324135419"><a name="zh-cn_topic_0150885197_p15201324135419"></a><a name="zh-cn_topic_0150885197_p15201324135419"></a>组件</p>
    </th>
    <th class="cellrowborder" valign="top" width="62.57%" id="mcps1.2.3.1.2"><p id="zh-cn_topic_0150885197_p10201724105411"><a name="zh-cn_topic_0150885197_p10201724105411"></a><a name="zh-cn_topic_0150885197_p10201724105411"></a>组件描述</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row930973118310"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p230912312313"><a name="p230912312313"></a><a name="p230912312313"></a>image/huawei-csi-v<span id="ph1247142163214"><a name="ph1247142163214"></a><a name="ph1247142163214"></a>4.6.0</span>-<em id="i7879115512231"><a name="i7879115512231"></a><a name="i7879115512231"></a>arch</em>.tar</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p131017311931"><a name="p131017311931"></a><a name="p131017311931"></a>huawei-csi-driver镜像，"arch"为CPU架构。</p>
    </td>
    </tr>
    <tr id="row1636415012105"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p236425091017"><a name="p236425091017"></a><a name="p236425091017"></a>image/storage-backend-controller-v<span id="ph16563185044814"><a name="ph16563185044814"></a><a name="ph16563185044814"></a>4.6.0</span>-<em id="i1580012569101"><a name="i1580012569101"></a><a name="i1580012569101"></a>arch</em>.tar</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p0364350161018"><a name="p0364350161018"></a><a name="p0364350161018"></a>后端管理控制器镜像，"arch"为CPU架构。</p>
    </td>
    </tr>
    <tr id="row20811154791011"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p9811154713107"><a name="p9811154713107"></a><a name="p9811154713107"></a>image/storage-backend-sidecar-v<span id="ph0931352104814"><a name="ph0931352104814"></a><a name="ph0931352104814"></a>4.6.0</span>-<em id="i17458825101116"><a name="i17458825101116"></a><a name="i17458825101116"></a>arch</em>.tar</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p7811174751010"><a name="p7811174751010"></a><a name="p7811174751010"></a>后端管理sidecar镜像，"arch"为CPU架构。</p>
    </td>
    </tr>
    <tr id="row925351132220"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p32505182215"><a name="p32505182215"></a><a name="p32505182215"></a>image/huawei-csi-extender-v<span id="ph486705310481"><a name="ph486705310481"></a><a name="ph486705310481"></a>4.6.0</span>-<em id="i12719141202718"><a name="i12719141202718"></a><a name="i12719141202718"></a>arch</em>.tar</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p182585182214"><a name="p182585182214"></a><a name="p182585182214"></a>huawei-csi-extender镜像，"arch"为CPU架构。</p>
    </td>
    </tr>
    <tr id="zh-cn_topic_0150885197_row132011024185415"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="zh-cn_topic_0150885197_p320102410540"><a name="zh-cn_topic_0150885197_p320102410540"></a><a name="zh-cn_topic_0150885197_p320102410540"></a>bin/</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="zh-cn_topic_0150885197_p720172417549"><a name="zh-cn_topic_0150885197_p720172417549"></a><a name="zh-cn_topic_0150885197_p720172417549"></a>华为提供的镜像使用的二进制文件。</p>
    </td>
    </tr>
    <tr id="row1266918385217"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p566919345210"><a name="p566919345210"></a><a name="p566919345210"></a>bin/oceanctl</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p1966993195218"><a name="p1966993195218"></a><a name="p1966993195218"></a>华为提供的命令行工具，可用于管理存储后端。</p>
    </td>
    </tr>
    <tr id="zh-cn_topic_0150885197_row1745645113715"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="zh-cn_topic_0150885197_p164570514374"><a name="zh-cn_topic_0150885197_p164570514374"></a><a name="zh-cn_topic_0150885197_p164570514374"></a>helm/</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="zh-cn_topic_0150885197_p445715115370"><a name="zh-cn_topic_0150885197_p445715115370"></a><a name="zh-cn_topic_0150885197_p445715115370"></a>Helm工程，用于部署华为CSI。</p>
    </td>
    </tr>
    <tr id="row1466517173816"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p104671317163816"><a name="p104671317163816"></a><a name="p104671317163816"></a>manual/</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p154672177382"><a name="p154672177382"></a><a name="p154672177382"></a>用于手动安装部署华为CSI。</p>
    </td>
    </tr>
    <tr id="zh-cn_topic_0150885197_row132192110373"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="zh-cn_topic_0150885197_p18220111117379"><a name="zh-cn_topic_0150885197_p18220111117379"></a><a name="zh-cn_topic_0150885197_p18220111117379"></a>examples/</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="zh-cn_topic_0150885197_p622091193716"><a name="zh-cn_topic_0150885197_p622091193716"></a><a name="zh-cn_topic_0150885197_p622091193716"></a>CSI使用过程中的yaml示例文件。</p>
    </td>
    </tr>
    <tr id="row49534515549"><td class="cellrowborder" valign="top" width="37.43%" headers="mcps1.2.3.1.1 "><p id="p14954195135418"><a name="p14954195135418"></a><a name="p14954195135418"></a>examples/backend</p>
    </td>
    <td class="cellrowborder" valign="top" width="62.57%" headers="mcps1.2.3.1.2 "><p id="p695405175411"><a name="p695405175411"></a><a name="p695405175411"></a>创建存储后端的yaml示例文件。</p>
    </td>
    </tr>
    </tbody>
    </table>

