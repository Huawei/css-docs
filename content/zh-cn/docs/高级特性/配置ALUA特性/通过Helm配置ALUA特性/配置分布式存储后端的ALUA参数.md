---
title: "配置分布式存储后端的ALUA参数"
linkTitle: "配置分布式存储后端的ALUA参数"
description: 
weight: 2
---

华为分布式存储针对ALUA的配置请参考产品对应的主机连通性指南文档说明。

针对不同的操作系统，ALUA配置可能有所不同。进入[华为技术支持](https://support.huawei.com/enterprise/zh/index.html)，在搜索输入框中输入“主机连通性指南”，单击搜索。在搜索结果中，选择对应操作系统的主机连通性指南。结合实际需要根据指南的说明进行ALUA配置。华为CSI将在华为存储上对该主机的启动器应用您设置的配置项。

>![](/public_sys-resources/zh/icon-note.gif) 
>已经发放的Pod的节点不会主动更改ALUA信息，需要通过在该节点重新发放Pod才会变更主机ALUA配置。
>分布式存储非双活场景，存储系统自身为Active/Active模式，选择“启用ALUA”没有实际意义，建议选择存储默认的“禁用ALUA”。因此不建议对分布式存储配置ALUA参数。

华为CSI支持的分布式存储的ALUA参数见[表 分布式存储ALUA参数说明](#table17219165595413)。

**表 1**  分布式存储ALUA参数说明

<a name="table17219165595413"></a>
<table><thead align="left"><tr id="row122207550541"><th class="cellrowborder" valign="top" width="28.57%" id="mcps1.2.4.1.1"><p id="p192208550546"><a name="p192208550546"></a><a name="p192208550546"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="34.870000000000005%" id="mcps1.2.4.1.2"><p id="p12201855175414"><a name="p12201855175414"></a><a name="p12201855175414"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="36.559999999999995%" id="mcps1.2.4.1.3"><p id="p622075535420"><a name="p622075535420"></a><a name="p622075535420"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row62201655155419"><td class="cellrowborder" valign="top" width="28.57%" headers="mcps1.2.4.1.1 "><p id="p422025511543"><a name="p422025511543"></a><a name="p422025511543"></a>HostName</p>
</td>
<td class="cellrowborder" valign="top" width="34.870000000000005%" headers="mcps1.2.4.1.2 "><p id="p1522045510541"><a name="p1522045510541"></a><a name="p1522045510541"></a>HostName的值为worker节点的主机名，如HostName1、HostName2。</p>
</td>
<td class="cellrowborder" valign="top" width="36.559999999999995%" headers="mcps1.2.4.1.3 "><p id="p11531172082216"><a name="p11531172082216"></a><a name="p11531172082216"></a>主机名通常使用 cat /etc/hostname 可获取。支持正则表达式方式匹配，如当HostName=“*”时，该条配置对任意主机名的主机生效。可参考<a href="https://zh.wikipedia.org/wiki/正则表达式" target="_blank" rel="noopener noreferrer">《正则表达式》</a>。</p>
<p id="p2531172016224"><a name="p2531172016224"></a><a name="p2531172016224"></a>当计算节点的主机名可已匹配多条ALUA配置选项，会根据匹配的精确度进行排序，使用第一条ALUA配置选项。排序规则见<a href="#section81474196587">ALUA配置项匹配主机名的规则</a>。</p>
</td>
</tr>
<tr id="row1022005517540"><td class="cellrowborder" valign="top" width="28.57%" headers="mcps1.2.4.1.1 "><p id="p142209555544"><a name="p142209555544"></a><a name="p142209555544"></a>switchoverMode</p>
</td>
<td class="cellrowborder" valign="top" width="34.870000000000005%" headers="mcps1.2.4.1.2 "><p id="p422018552546"><a name="p422018552546"></a><a name="p422018552546"></a>切换模式。必选，取值为：</p>
<a name="ul1422015558541"></a><a name="ul1422015558541"></a><ul id="ul1422015558541"><li>Disable_alua：禁用ALUA</li><li>Enable_alua：启用ALUA</li></ul>
</td>
<td class="cellrowborder" valign="top" width="36.559999999999995%" headers="mcps1.2.4.1.3 "><p id="p14575336571"><a name="p14575336571"></a><a name="p14575336571"></a>非双活场景，存储系统自身为Active/Active模式，选择“启用ALUA”没有实际意义，建议选择“禁用ALUA”。当前华为CSI未支持SAN双活场景，请谨慎启用ALUA。</p>
</td>
</tr>
<tr id="row0220155515413"><td class="cellrowborder" valign="top" width="28.57%" headers="mcps1.2.4.1.1 "><p id="p02201255125416"><a name="p02201255125416"></a><a name="p02201255125416"></a>pathType</p>
</td>
<td class="cellrowborder" valign="top" width="34.870000000000005%" headers="mcps1.2.4.1.2 "><p id="p2022011558544"><a name="p2022011558544"></a><a name="p2022011558544"></a>路径类型。条件必选，取值为：</p>
<a name="ul142201655195419"></a><a name="ul142201655195419"></a><ul id="ul142201655195419"><li>optimal_path：优选路径</li><li>non_optimal_path：非优选路径</li></ul>
</td>
<td class="cellrowborder" valign="top" width="36.559999999999995%" headers="mcps1.2.4.1.3 "><p id="p1220455195413"><a name="p1220455195413"></a><a name="p1220455195413"></a>切换模式为启动ALUA时需要设置该选项。</p>
</td>
</tr>
</tbody>
</table>

## ALUA配置项匹配主机名的规则{#section81474196587}

-   如果设置的主机名规则精确匹配的业务节点主机名，则使用该主机名规则对应的ALUA配置项。

    如配置项1中主机名规则为“\*”，配置项2中的主机名规则为“^myhost01$”。当计算节点的主机名是“myhost01”时，精确匹配配置项2，华为CSI将使用配置项2中的配置应用到存储侧。

-   如果设置的主机名规则无法精确匹配的业务节点主机名，则直接使用正则匹配到的第一条ALUA配置项。

    如配置项1中主机名规则为“myhost0\[0-9\]”，配置项2中的主机名规则为“myhost0\[5-9\]”，配置项1的优先级高于配置项2。当计算节点的主机名是“myhost06”时，两个配置项均可以匹配，此时华为CSI将使用配置项1中的配置应用到存储侧。

