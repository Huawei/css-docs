---
title: "Configuring ALUA Parameters for a Distributed Storage Backend"
linkTitle: "Configuring ALUA Parameters for a Distributed Storage Backend"
description: 
weight: 2
---

For details about how to configure ALUA for Huawei distributed storage, see the host connectivity guide of the corresponding product.

The ALUA configuration may vary according to the OS. Visit  [Huawei Technical Support](https://support.huawei.com/enterprise/en/index.html), enter  **Host Connectivity Guide**  in the search box, and click the search button. In the search result, select the host connectivity guide for the desired OS. Configure ALUA according to the actual situation and the description in the guide. Huawei CSI will apply the configuration items you set to the initiator of the host on Huawei storage.

>![](/css-docs/public_sys-resources/en/icon-note.gif)
>A node with a Pod provisioned does not proactively change ALUA information. The host ALUA configuration changes only after a Pod is provisioned again to the node.
>In non-HyperMetro scenarios of distributed storage, you are advised to set the switchover mode to "disable ALUA" \(default value\). This is because the storage system is in active/active mode and "enables ALUA" is meaningless. Therefore, you are advised not to configure ALUA parameters for distributed storage.

[Table 1](#table17219165595413)  lists the ALUA parameters supported by Huawei CSI for distributed storage.

**Table  1**  ALUA parameters for distributed storage

<a name="table17219165595413"></a>
<table><thead align="left"><tr id="row122207550541"><th class="cellrowborder" valign="top" width="28.57%" id="mcps1.2.4.1.1"><p id="p192208550546"><a name="p192208550546"></a><a name="p192208550546"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="34.870000000000005%" id="mcps1.2.4.1.2"><p id="p12201855175414"><a name="p12201855175414"></a><a name="p12201855175414"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="36.559999999999995%" id="mcps1.2.4.1.3"><p id="p622075535420"><a name="p622075535420"></a><a name="p622075535420"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row62201655155419"><td class="cellrowborder" valign="top" width="28.57%" headers="mcps1.2.4.1.1 "><p id="p422025511543"><a name="p422025511543"></a><a name="p422025511543"></a>HostName</p>
</td>
<td class="cellrowborder" valign="top" width="34.870000000000005%" headers="mcps1.2.4.1.2 "><p id="p1522045510541"><a name="p1522045510541"></a><a name="p1522045510541"></a>The value of <strong id="b2532152014246"><a name="b2532152014246"></a><a name="b2532152014246"></a>HostName</strong> is the host name of a worker node, for example, <strong id="b145331205242"><a name="b145331205242"></a><a name="b145331205242"></a>HostName1</strong> and <strong id="b19534132032416"><a name="b19534132032416"></a><a name="b19534132032416"></a>HostName2</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="36.559999999999995%" headers="mcps1.2.4.1.3 "><p id="p11531172082216"><a name="p11531172082216"></a><a name="p11531172082216"></a>The host name can be obtained by running the <strong id="b8558527162414"><a name="b8558527162414"></a><a name="b8558527162414"></a>cat /etc/hostname</strong> command. It can be matched by using regular expressions. When <strong id="b16199133032411"><a name="b16199133032411"></a><a name="b16199133032411"></a>HostName</strong> is set to <strong id="b19200630132410"><a name="b19200630132410"></a><a name="b19200630132410"></a>*</strong>, the configuration takes effect on hosts with any name. For details, see <a href="https://en.wikipedia.org/wiki/Regular_expression" target="_blank" rel="noopener noreferrer">Regular expression</a>.</p>
<p id="p2531172016224"><a name="p2531172016224"></a><a name="p2531172016224"></a>If the host name of a compute node matches multiple ALUA configuration options, they will be sorted based on the matching accuracy and the first ALUA configuration option will be used. For details about the sorting rules, see <a href="#section81474196587">Rules for Matching ALUA Configuration Items with Host Names</a>.</p>
</td>
</tr>
<tr id="row1022005517540"><td class="cellrowborder" valign="top" width="28.57%" headers="mcps1.2.4.1.1 "><p id="p142209555544"><a name="p142209555544"></a><a name="p142209555544"></a>switchoverMode</p>
</td>
<td class="cellrowborder" valign="top" width="34.870000000000005%" headers="mcps1.2.4.1.2 "><p id="p422018552546"><a name="p422018552546"></a><a name="p422018552546"></a>Switchover mode. This parameter is mandatory. The value can be:</p>
<a name="ul1422015558541"></a><a name="ul1422015558541"></a><ul id="ul1422015558541"><li><strong id="b35561348122412"><a name="b35561348122412"></a><a name="b35561348122412"></a>Disable_alua</strong>: disables ALUA.</li><li><strong id="b20109453122419"><a name="b20109453122419"></a><a name="b20109453122419"></a>Enable_alua</strong>: enables ALUA.</li></ul>
</td>
<td class="cellrowborder" valign="top" width="36.559999999999995%" headers="mcps1.2.4.1.3 "><p id="p14575336571"><a name="p14575336571"></a><a name="p14575336571"></a>In non-HyperMetro scenario, you are advised to set the switchover mode to "disable ALUA". This is because the storage system is in active/active mode and "enables ALUA" is meaningless. Currently, Huawei CSI does not support SAN HyperMetro scenarios. Exercise caution when enabling ALUA.</p>
</td>
</tr>
<tr id="row0220155515413"><td class="cellrowborder" valign="top" width="28.57%" headers="mcps1.2.4.1.1 "><p id="p02201255125416"><a name="p02201255125416"></a><a name="p02201255125416"></a>pathType</p>
</td>
<td class="cellrowborder" valign="top" width="34.870000000000005%" headers="mcps1.2.4.1.2 "><p id="p2022011558544"><a name="p2022011558544"></a><a name="p2022011558544"></a>Path type. This parameter is conditionally mandatory. The value can be:</p>
<a name="ul142201655195419"></a><a name="ul142201655195419"></a><ul id="ul142201655195419"><li><strong id="b431615302613"><a name="b431615302613"></a><a name="b431615302613"></a>optimal_path</strong>: preferred path</li><li><strong id="b15364472262"><a name="b15364472262"></a><a name="b15364472262"></a>non_optimal_path</strong>: non-preferred path</li></ul>
</td>
<td class="cellrowborder" valign="top" width="36.559999999999995%" headers="mcps1.2.4.1.3 "><p id="p1220455195413"><a name="p1220455195413"></a><a name="p1220455195413"></a>This parameter is mandatory when the switchover mode is set to "enables ALUA".</p>
</td>
</tr>
</tbody>
</table>

## Rules for Matching ALUA Configuration Items with Host Names{#section81474196587}

-   If the configured host name rule exactly matches the host name of the service node, the ALUA configuration item corresponding to the host name rule is used.

    For example, the host name rule in configuration item 1 is  **\***  and that in configuration item 2 is  **^myhost01$**. If the host name of a compute node is  **myhost01**, it exactly matches configuration item 2. In this case, Huawei CSI will apply the configuration information in configuration item 2 to the storage side.

-   If the configured host name rule does not exactly match the host name of the service node, the first ALUA configuration item matched by regular expressions is used.

    For example, the host name rule in configuration item 1 is  **myhost0\[0-9\]**  and that in configuration item 2 is  **myhost0\[5-9\]**. In this case, configuration item 1 has a higher priority than configuration item 2. If the host name of a compute node is  **myhost06**, both configuration items can be matched. In this case, Huawei CSI will apply the configuration information in configuration item 1 to the storage side.

