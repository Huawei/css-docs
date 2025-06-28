---
title: "配置华为企业存储后端的ALUA参数"
linkTitle: "配置华为企业存储后端的ALUA参数"
description: 
weight: 1
---

华为企业存储针对ALUA的配置请参考产品对应的主机连通性指南文档说明。

针对不同的操作系统，ALUA配置可能有所不同。进入[华为技术支持](https://support.huawei.com/enterprise/zh/index.html)，在搜索输入框中输入“主机连通性指南”，单击搜索。在搜索结果中，选择对应操作系统的主机连通性指南。结合实际需要根据指南的说明进行ALUA配置。华为CSI将在华为存储上对该主机的启动器应用您设置的配置项。

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>已经发放的Pod的节点不会主动更改ALUA信息，需要通过在该节点重新发放Pod才会变更主机ALUA配置。

## OceanStor V5系列系列存储后端的ALUA参数{#section16218353201717}

华为CSI支持的OceanStor V5系列存储的ALUA参数见[表1](#zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_table106361351202112)。

**表 1**  华为CSI支持的OceanStor V5系列存储的ALUA参数说明

<a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_table106361351202112"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_row12636135142110"><th class="cellrowborder" valign="top" width="20.77%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p7636151112111"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p7636151112111"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p7636151112111"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="29.799999999999997%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p0636195114217"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p0636195114217"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p0636195114217"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="49.43%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p18636851162116"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p18636851162116"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p18636851162116"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_row5636145182110"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p12636151172115"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p12636151172115"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p12636151172115"></a>HostName</p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p119151501311"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p119151501311"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p119151501311"></a>主机名规则。必填，可使用正则表达式。</p>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p46368510213"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p46368510213"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p46368510213"></a>主机名通常使用 cat /etc/hostname 可获取。支持正则表达式方式匹配，如当HostName=“*”时，该条配置对任意主机名的主机生效。可参考<a href="https://zh.wikipedia.org/wiki/正则表达式" target="_blank" rel="noopener noreferrer">《正则表达式》</a>。</p>
<p id="p9139142313544"><a name="p9139142313544"></a><a name="p9139142313544"></a>当计算节点的主机名可已匹配多条ALUA配置选项，会根据匹配的精确度进行排序，使用第一条ALUA配置选项。排序规则见<a href="#section81474196587">ALUA配置项匹配主机名的规则</a>。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_row763665116210"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p26363512213"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p26363512213"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p26363512213"></a><span>MULTIPATHTYPE</span></p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p863615122117"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p863615122117"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p863615122117"></a>多路径类型。必填，取值为：</p>
<a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul2074595619259"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul2074595619259"></a><ul id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul2074595619259"><li>0：不使用第三方多路径</li><li>1：使用第三方多路径</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p5636175119215"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p5636175119215"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p5636175119215"></a>--</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_row116368518214"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1563655132116"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1563655132116"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1563655132116"></a><span>FAILOVERMODE</span></p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1636205142120"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1636205142120"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1636205142120"></a>启动器的切换模式。条件必选，取值为：</p>
<a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul1713695915256"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul1713695915256"></a><ul id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul1713695915256"><li>0：旧版本ALUA</li><li>1：通用ALUA</li><li>2：不使用ALUA</li><li>3：特殊模式ALUA</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1563712516214"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1563712516214"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1563712516214"></a>当使用第三方多路径时该参数才需要指定。请参考连通性指南的说明，配置启动器的切换模式。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_row1963745142116"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1663785112216"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1663785112216"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1663785112216"></a><span>SPECIALMODETYPE</span></p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p16379513219"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p16379513219"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p16379513219"></a>启动器的特殊模式类型。条件必选，取值为：</p>
<a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul177131712192612"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul177131712192612"></a><ul id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul177131712192612"><li>0：特殊模式0</li><li>1：特殊模式1</li><li>2：特殊模式2</li><li>3：特殊模式3</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p6637251142114"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p6637251142114"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p6637251142114"></a>当启动器的切换模式为“特殊模式ALUA”时该参数才需要指定。请参考连通性指南的说明，配置启动器的特殊模式类型。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_row15637155122111"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p17637951132119"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p17637951132119"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p17637951132119"></a><span>PATHTYPE</span></p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p18637135117217"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p18637135117217"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p18637135117217"></a>启动器的路径类型。条件必选，取值为：</p>
<a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul143311772617"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul143311772617"></a><ul id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_ul143311772617"><li>0：优选路径</li><li>1：非优选路径</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1863795162113"><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1863795162113"></a><a name="zh-cn_topic_0000001299863718_zh-cn_topic_0000001199142540_p1863795162113"></a>当使用第三方多路径时该参数才需要指定。请参考连通性指南的说明，配置启动器的路径类型。</p>
</td>
</tr>
</tbody>
</table>

以OceanStor 18500 V5存储对接Red Hat操作系统为例，主机连通性指南见[《华为SAN存储在Red Hat系统下的主机连通性指南》](https://support.huawei.com/enterprise/zh/doc/EDOC1000150152)。

如下ALUA设置示例，是非双活存储场景下，OceanStor 18500 V5存储的Red Hat操作系统的连通性指南的推荐设置。本例中假设Kubernetes集群中计算节点“myhost01”的操作系统是RHEL 5.x，其他计算节点操作系统均为RHEL 7.x。根据推荐，RHEL 5.x的切换模式应该为“不使用ALUA”，RHEL 7.x的切换模式应该为“通用ALUA”。

```yaml
storage: oceanstor-san
name: oceanstor-iscsi-155
urls:
  - https://192.168.129.155:8088
  - https://192.168.129.156:8088
pools:
  - StoragePool001
parameters:
  protocol: iscsi
  portals:
    - 192.168.128.120
    - 192.168.128.121
  ALUA:
    ^myhost01$:
      MULTIPATHTYPE: 1
      FAILOVERMODE: 2
      PATHTYPE: 0
    "*":
      MULTIPATHTYPE: 1
      FAILOVERMODE: 1
      PATHTYPE: 0
```

## OceanStor和OceanStor Dorado系列存储后端的ALUA参数{#section1629834120204}

华为CSI支持的OceanStor和OceanStor Dorado系列存储的ALUA参数见[表2](#zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_table7143850202411)。

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>OceanStor和OceanStor Dorado系列存储在默认情况下启动器主机访问模式即为“均衡模式”，因此不建议对OceanStor和OceanStor Dorado系列存储配置ALUA参数。

**表 2**  OceanStor和OceanStor Dorado系列存储的ALUA参数说明

<a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_table7143850202411"></a>
<table><thead align="left"><tr id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_row4144125052413"><th class="cellrowborder" valign="top" width="24.33%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p3144650112410"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p3144650112410"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p3144650112410"></a>参数名</p>
</th>
<th class="cellrowborder" valign="top" width="26.279999999999998%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1514445018249"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1514445018249"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1514445018249"></a>参数描述</p>
</th>
<th class="cellrowborder" valign="top" width="49.39%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p14144165042418"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p14144165042418"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p14144165042418"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_row0144115012242"><td class="cellrowborder" valign="top" width="24.33%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p10144250172412"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p10144250172412"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p10144250172412"></a>HostName</p>
</td>
<td class="cellrowborder" valign="top" width="26.279999999999998%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p119151501311"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p119151501311"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p119151501311"></a>主机名规则。必填，可使用正则表达式。</p>
</td>
<td class="cellrowborder" valign="top" width="49.39%" headers="mcps1.2.4.1.3 "><p id="p11531172082216"><a name="p11531172082216"></a><a name="p11531172082216"></a>主机名通常使用 cat /etc/hostname 可获取。支持正则表达式方式匹配，如当HostName=“*”时，该条配置对任意主机名的主机生效。可参考<a href="https://zh.wikipedia.org/wiki/正则表达式" target="_blank" rel="noopener noreferrer">《正则表达式》</a>。</p>
<p id="p2531172016224"><a name="p2531172016224"></a><a name="p2531172016224"></a>当计算节点的主机名可已匹配多条ALUA配置选项，会根据匹配的精确度进行排序，使用第一条ALUA配置选项。排序规则见<a href="#section81474196587">ALUA配置项匹配主机名的规则</a>。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_row19144195011244"><td class="cellrowborder" valign="top" width="24.33%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1514485010246"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1514485010246"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1514485010246"></a>accessMode</p>
</td>
<td class="cellrowborder" valign="top" width="26.279999999999998%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p17144750112419"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p17144750112419"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p17144750112419"></a>主机访问模式。必填，取值为：</p>
<a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_ul1877452310265"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_ul1877452310265"></a><ul id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_ul1877452310265"><li>0：均衡模式</li><li>1：非对称模式</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.39%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1540212533612"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1540212533612"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1540212533612"></a><span>非双活场景下</span>建议使用均衡模式。当前华为CSI未支持SAN双活场景，请谨慎使用非对称模式。</p>
</td>
</tr>
<tr id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_row15144550162416"><td class="cellrowborder" valign="top" width="24.33%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p714455012410"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p714455012410"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p714455012410"></a>hyperMetroPathOptimized</p>
</td>
<td class="cellrowborder" valign="top" width="26.279999999999998%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1414435082414"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1414435082414"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p1414435082414"></a>双活场景下，主机在当前阵列的路径是否优选。取值为：</p>
<a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_ul11690126102616"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_ul11690126102616"></a><ul id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_ul11690126102616"><li>1：是</li><li>0：否</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.39%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p11144105010245"><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p11144105010245"></a><a name="zh-cn_topic_0000001352783505_zh-cn_topic_0000001198982584_p11144105010245"></a>当主机访问模式设置为非对称模式时，才需要配置该参数。</p>
<p id="p3136547173316"><a name="p3136547173316"></a><a name="p3136547173316"></a>当前华为CSI未支持SAN双活场景，请谨慎使用非对称模式。</p>
</td>
</tr>
</tbody>
</table>

以OceanStor Dorado 18500存储对接Red Hat操作系统为例，主机连通性指南见[《OceanStor Dorado & OceanStor在Red Hat下的主机连通性指南》](https://support.huawei.com/enterprise/zh/doc/EDOC1100112792/e369b5d4)。

如下ALUA设置示例，是非双活存储场景下，OceanStor Dorado 18500存储的Red Hat操作系统的连通性指南的推荐设置。

```yaml
storage: "oceanstor-san"
name: "dorado-iscsi-155"
urls:
  - "https://192.168.129.155:8088"
  - "https://192.168.129.156:8088"
pools:
  - "StoragePool001"
parameters:
  protocol: "iscsi"
  portals:
    - "192.168.128.120"
    - "192.168.128.121"
  ALUA:
    "*":
      accessMode: 0
```

## ALUA配置项匹配主机名的规则{#section81474196587}

-   如果设置的主机名规则精确匹配的业务节点主机名，则使用该主机名规则对应的ALUA配置项。

    如配置项1中主机名规则为“\*”，配置项2中的主机名规则为“^myhost01$”。当计算节点的主机名是“myhost01”时，精确匹配配置项2，华为CSI将使用配置项2中的配置应用到存储侧。

-   如果设置的主机名规则无法精确匹配的业务节点主机名，则直接使用正则匹配到的第一条ALUA配置项。

    如配置项1中主机名规则为“myhost0\[0-9\]”，配置项2中的主机名规则为“myhost0\[5-9\]”，配置项1的优先级高于配置项2。当计算节点的主机名是“myhost06”时，两个配置项均可以匹配，此时华为CSI将使用配置项1中的配置应用到存储侧。

