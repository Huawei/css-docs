---
title: "Configuring ALUA Parameters for a Huawei Enterprise Storage Backend"
linkTitle: "Configuring ALUA Parameters for a Huawei Enterprise Storage Backend"
description: 
weight: 1
---

For details about how to configure ALUA for Huawei enterprise storage, see the host connectivity guide of the corresponding product.

The ALUA configuration may vary according to the OS. Visit  [Huawei Technical Support](https://support.huawei.com/enterprise/en/index.html), enter  **Host Connectivity Guide**  in the search box, and click the search button. In the search result, select the host connectivity guide for the desired OS. Configure ALUA according to the actual situation and the description in the guide. Huawei CSI will apply the configuration items you set to the initiator of the host on Huawei storage.

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>A node with a Pod provisioned does not proactively change ALUA information. The host ALUA configuration changes only after a Pod is provisioned again to the node.

## ALUA Parameters for OceanStor V5 and OceanStor Dorado V3 Series{#section16218353201717}

[Table 1](#en-us_topic_0000001299863718_en-us_topic_0000001199142540_table106361351202112)  lists the ALUA parameters supported by Huawei CSI for OceanStor V5 and OceanStor Dorado V3 series.

**Table  1**  ALUA parameters supported by Huawei CSI for OceanStor V5 and OceanStor Dorado V3 series

<a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_table106361351202112"></a>
<table><thead align="left"><tr id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_row12636135142110"><th class="cellrowborder" valign="top" width="20.77%" id="mcps1.2.4.1.1"><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p7636151112111"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p7636151112111"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p7636151112111"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="29.799999999999997%" id="mcps1.2.4.1.2"><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p0636195114217"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p0636195114217"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p0636195114217"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="49.43%" id="mcps1.2.4.1.3"><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p18636851162116"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p18636851162116"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p18636851162116"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_row5636145182110"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p12636151172115"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p12636151172115"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p12636151172115"></a>HostName</p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p119151501311"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p119151501311"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p119151501311"></a>Host name rule. This parameter is mandatory. You can use a regular expression.</p>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p46368510213"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p46368510213"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p46368510213"></a>The host name can be obtained by running the <strong id="b89999442473"><a name="b89999442473"></a><a name="b89999442473"></a>cat /etc/hostname</strong> command. It can be matched by using regular expressions. When <strong id="b16125153017486"><a name="b16125153017486"></a><a name="b16125153017486"></a>HostName</strong> is set to <strong id="b14113133920489"><a name="b14113133920489"></a><a name="b14113133920489"></a>*</strong>, the configuration takes effect on hosts with any name. For details, see <a href="https://en.wikipedia.org/wiki/Regular_expression" target="_blank" rel="noopener noreferrer">Regular expression</a>.</p>
<p id="p9139142313544"><a name="p9139142313544"></a><a name="p9139142313544"></a>If the host name of a compute node matches multiple ALUA configuration options, they will be sorted based on the matching accuracy and the first ALUA configuration option will be used. For details about the sorting rules, see <a href="#section81474196587">Rules for Matching ALUA Configuration Items with Host Names</a>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_row763665116210"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p26363512213"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p26363512213"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p26363512213"></a>MULTIPATHTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p863615122117"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p863615122117"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p863615122117"></a>Multipathing type. This parameter is mandatory. The value can be:</p>
<a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul2074595619259"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul2074595619259"></a><ul id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul2074595619259"><li><strong id="b167415472515"><a name="b167415472515"></a><a name="b167415472515"></a>0</strong>: Third-party multipathing is not used.</li><li><strong id="b1781448185211"><a name="b1781448185211"></a><a name="b1781448185211"></a>1</strong>: Third-party multipathing is used.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p5636175119215"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p5636175119215"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p5636175119215"></a>--</p>
</td>
</tr>
<tr id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_row116368518214"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1563655132116"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1563655132116"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1563655132116"></a>FAILOVERMODE</p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1636205142120"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1636205142120"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1636205142120"></a>Initiator switchover mode. This parameter is conditionally mandatory. The value can be:</p>
<a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul1713695915256"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul1713695915256"></a><ul id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul1713695915256"><li><strong id="en-us_topic_0000001299863718_b86664716916"><a name="en-us_topic_0000001299863718_b86664716916"></a><a name="en-us_topic_0000001299863718_b86664716916"></a>0</strong>: early-version ALUA</li><li><strong id="en-us_topic_0000001299863718_b810225318917"><a name="en-us_topic_0000001299863718_b810225318917"></a><a name="en-us_topic_0000001299863718_b810225318917"></a>1</strong>: common ALUA</li><li><strong id="en-us_topic_0000001299863718_b1679519568912"><a name="en-us_topic_0000001299863718_b1679519568912"></a><a name="en-us_topic_0000001299863718_b1679519568912"></a>2</strong>: ALUA not used</li><li><strong id="en-us_topic_0000001299863718_b1296619041010"><a name="en-us_topic_0000001299863718_b1296619041010"></a><a name="en-us_topic_0000001299863718_b1296619041010"></a>3</strong>: special ALUA</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1563712516214"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1563712516214"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1563712516214"></a>This parameter needs to be specified only when third-party multipathing is used. Configure the initiator switchover mode by referring to the connectivity guide.</p>
</td>
</tr>
<tr id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_row1963745142116"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1663785112216"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1663785112216"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1663785112216"></a>SPECIALMODETYPE</p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p16379513219"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p16379513219"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p16379513219"></a>Special mode type of the initiator. This parameter is conditionally mandatory. The value can be:</p>
<a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul177131712192612"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul177131712192612"></a><ul id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul177131712192612"><li><strong id="en-us_topic_0000001299863718_b669217105"><a name="en-us_topic_0000001299863718_b669217105"></a><a name="en-us_topic_0000001299863718_b669217105"></a>0</strong>: special mode 0</li><li><strong id="en-us_topic_0000001299863718_b81814253102"><a name="en-us_topic_0000001299863718_b81814253102"></a><a name="en-us_topic_0000001299863718_b81814253102"></a>1</strong>: special mode 1</li><li><strong id="en-us_topic_0000001299863718_b64821628171017"><a name="en-us_topic_0000001299863718_b64821628171017"></a><a name="en-us_topic_0000001299863718_b64821628171017"></a>2</strong>: special mode 2</li><li><strong id="en-us_topic_0000001299863718_b92216330102"><a name="en-us_topic_0000001299863718_b92216330102"></a><a name="en-us_topic_0000001299863718_b92216330102"></a>3</strong>: special mode 3</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p6637251142114"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p6637251142114"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p6637251142114"></a>This parameter needs to be specified only when the initiator switchover mode is special ALUA. Configure the special mode type of the initiator by referring to the connectivity guide.</p>
</td>
</tr>
<tr id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_row15637155122111"><td class="cellrowborder" valign="top" width="20.77%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p17637951132119"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p17637951132119"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p17637951132119"></a>PATHTYPE</p>
</td>
<td class="cellrowborder" valign="top" width="29.799999999999997%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p18637135117217"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p18637135117217"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p18637135117217"></a>Initiator path type. This parameter is conditionally mandatory. The value can be:</p>
<a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul143311772617"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul143311772617"></a><ul id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_ul143311772617"><li><strong id="en-us_topic_0000001299863718_b1982517526105"><a name="en-us_topic_0000001299863718_b1982517526105"></a><a name="en-us_topic_0000001299863718_b1982517526105"></a>0</strong>: preferred path</li><li><strong id="en-us_topic_0000001299863718_b54861956131012"><a name="en-us_topic_0000001299863718_b54861956131012"></a><a name="en-us_topic_0000001299863718_b54861956131012"></a>1</strong>: non-preferred path</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.43%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1863795162113"><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1863795162113"></a><a name="en-us_topic_0000001299863718_en-us_topic_0000001199142540_p1863795162113"></a>This parameter needs to be specified only when third-party multipathing is used. Configure the initiator path type by referring to the connectivity guide.</p>
</td>
</tr>
</tbody>
</table>

The following uses OceanStor 18500 V5 as an example to describe how to connect to Red Hat. For details about the host connectivity guide, see  _[Huawei SAN Storage Host Connectivity Guide for Red Hat](https://support.huawei.com/enterprise/en/doc/EDOC1000150157)_.

The following ALUA configuration example is recommended in the OceanStor 18500 V5 host connectivity guide for Red Hat in non-HyperMetro storage scenarios. In this example, the OS on compute node  **myhost01**  in the Kubernetes cluster is RHEL 5._x_, and that on other compute nodes is RHEL 7._x_. According to the recommendation, the switchover mode of RHEL 5._x_  should be "ALUA not used", and that of RHEL 7._x_  should be "common ALUA".

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

## ALUA Parameters for OceanStor and OceanStor Dorado Series{#section1629834120204}

[Table 2](#en-us_topic_0000001352783505_en-us_topic_0000001198982584_table7143850202411)  lists the ALUA parameters supported by Huawei CSI for OceanStor and OceanStor Dorado series.

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>By default, the initiator host access mode of OceanStor and OceanStor Dorado series storage is "balanced mode". Therefore, you are advised not to configure ALUA parameters for OceanStor and OceanStor Dorado series storage.

**Table  2**  ALUA parameters for OceanStor and OceanStor Dorado series

<a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_table7143850202411"></a>
<table><thead align="left"><tr id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_row4144125052413"><th class="cellrowborder" valign="top" width="24.33%" id="mcps1.2.4.1.1"><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p3144650112410"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p3144650112410"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p3144650112410"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="26.279999999999998%" id="mcps1.2.4.1.2"><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1514445018249"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1514445018249"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1514445018249"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="49.39%" id="mcps1.2.4.1.3"><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p14144165042418"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p14144165042418"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p14144165042418"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_row0144115012242"><td class="cellrowborder" valign="top" width="24.33%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p10144250172412"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p10144250172412"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p10144250172412"></a>HostName</p>
</td>
<td class="cellrowborder" valign="top" width="26.279999999999998%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p119151501311"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p119151501311"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p119151501311"></a>Host name rule. This parameter is mandatory. You can use a regular expression.</p>
</td>
<td class="cellrowborder" valign="top" width="49.39%" headers="mcps1.2.4.1.3 "><p id="p11531172082216"><a name="p11531172082216"></a><a name="p11531172082216"></a>The host name can be obtained by running the <strong id="b1077420125618"><a name="b1077420125618"></a><a name="b1077420125618"></a>cat /etc/hostname</strong> command. It can be matched by using regular expressions. When <strong id="b011071416612"><a name="b011071416612"></a><a name="b011071416612"></a>HostName</strong> is set to <strong id="b17115614663"><a name="b17115614663"></a><a name="b17115614663"></a>*</strong>, the configuration takes effect on hosts with any name. For details, see <a href="https://en.wikipedia.org/wiki/Regular_expression" target="_blank" rel="noopener noreferrer">Regular expression</a>.</p>
<p id="p2531172016224"><a name="p2531172016224"></a><a name="p2531172016224"></a>If the host name of a compute node matches multiple ALUA configuration options, they will be sorted based on the matching accuracy and the first ALUA configuration option will be used. For details about the sorting rules, see <a href="#section81474196587">Rules for Matching ALUA Configuration Items with Host Names</a>.</p>
</td>
</tr>
<tr id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_row19144195011244"><td class="cellrowborder" valign="top" width="24.33%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1514485010246"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1514485010246"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1514485010246"></a>accessMode</p>
</td>
<td class="cellrowborder" valign="top" width="26.279999999999998%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p17144750112419"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p17144750112419"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p17144750112419"></a>Host access mode. This parameter is mandatory. The value can be:</p>
<a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_ul1877452310265"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_ul1877452310265"></a><ul id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_ul1877452310265"><li><strong id="b84741933863"><a name="b84741933863"></a><a name="b84741933863"></a>0</strong>: balanced mode</li><li><strong id="b518112383611"><a name="b518112383611"></a><a name="b518112383611"></a>1</strong>: asymmetric mode</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.39%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1540212533612"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1540212533612"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1540212533612"></a>The balanced mode is recommended in non-HyperMetro scenarios. Currently, Huawei CSI does not support SAN HyperMetro scenarios. Exercise caution when using the asymmetric mode.</p>
</td>
</tr>
<tr id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_row15144550162416"><td class="cellrowborder" valign="top" width="24.33%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p714455012410"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p714455012410"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p714455012410"></a>hyperMetroPathOptimized</p>
</td>
<td class="cellrowborder" valign="top" width="26.279999999999998%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1414435082414"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1414435082414"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p1414435082414"></a>Whether the path of the host on the current storage array is preferred in HyperMetro scenarios. The value can be:</p>
<a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_ul11690126102616"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_ul11690126102616"></a><ul id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_ul11690126102616"><li><strong id="b3557233277"><a name="b3557233277"></a><a name="b3557233277"></a>1</strong>: yes</li><li><strong id="b20190153618711"><a name="b20190153618711"></a><a name="b20190153618711"></a>0</strong>: no</li></ul>
</td>
<td class="cellrowborder" valign="top" width="49.39%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p11144105010245"><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p11144105010245"></a><a name="en-us_topic_0000001352783505_en-us_topic_0000001198982584_p11144105010245"></a>This parameter needs to be specified only when the host access mode is set to asymmetric.</p>
<p id="p3136547173316"><a name="p3136547173316"></a><a name="p3136547173316"></a>Currently, Huawei CSI does not support SAN HyperMetro scenarios. Exercise caution when using the asymmetric mode.</p>
</td>
</tr>
</tbody>
</table>

The following uses OceanStor Dorado 18000 as an example to describe how to connect to Red Hat. For details about the host connectivity guide, see  _[OceanStor Dorado and OceanStor Host Connectivity Guide for Red Hat](https://support.huawei.com/enterprise/en/doc/EDOC1100113070/1b4ad686)_.

The following ALUA configuration example is recommended in the OceanStor Dorado 18000 host connectivity guide for Red Hat in non-HyperMetro storage scenarios.

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

## Rules for Matching ALUA Configuration Items with Host Names{#section81474196587}

-   If the configured host name rule exactly matches the host name of the service node, the ALUA configuration item corresponding to the host name rule is used.

    For example, the host name rule in configuration item 1 is  **\***  and that in configuration item 2 is  **^myhost01$**. If the host name of a compute node is  **myhost01**, it exactly matches configuration item 2. In this case, Huawei CSI will apply the configuration information in configuration item 2 to the storage side.

-   If the configured host name rule does not exactly match the host name of the service node, the first ALUA configuration item matched by regular expressions is used.

    For example, the host name rule in configuration item 1 is  **myhost0\[0-9\]**  and that in configuration item 2 is  **myhost0\[5-9\]**. In this case, configuration item 1 has a higher priority than configuration item 2. If the host name of a compute node is  **myhost06**, both configuration items can be matched. In this case, Huawei CSI will apply the configuration information in configuration item 1 to the storage side.

