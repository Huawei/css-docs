---
title: "Checking User Configurations on Huawei Storage"
linkTitle: "Checking User Configurations on Huawei Storage"
description: 
weight: 3
---

After Huawei storage is connected to the container platform, Huawei CSI needs to manage storage resources on Huawei storage based on service requirements, such as creating and mapping volumes. In this case, Huawei CSI needs to use the users created on Huawei storage to communicate with Huawei storage. The following table lists the user information required for different storage devices.

**Table  1**  User requirements for connecting storage to CSI

<a name="en-us_topic_0214996140_table14321516134313"></a>
<table><thead align="left"><tr id="en-us_topic_0214996140_row5326166437"><th class="cellrowborder" valign="top" width="24.000000000000004%" id="mcps1.2.6.1.1"><p id="en-us_topic_0214996140_p1832131654315"><a name="en-us_topic_0214996140_p1832131654315"></a><a name="en-us_topic_0214996140_p1832131654315"></a>Storage Type</p>
</th>
<th class="cellrowborder" valign="top" width="18.000000000000004%" id="mcps1.2.6.1.2"><p id="en-us_topic_0214996140_p240885914315"><a name="en-us_topic_0214996140_p240885914315"></a><a name="en-us_topic_0214996140_p240885914315"></a>User Type</p>
</th>
<th class="cellrowborder" valign="top" width="25.000000000000007%" id="mcps1.2.6.1.3"><p id="en-us_topic_0214996140_p15321716184318"><a name="en-us_topic_0214996140_p15321716184318"></a><a name="en-us_topic_0214996140_p15321716184318"></a>Role</p>
</th>
<th class="cellrowborder" valign="top" width="18.000000000000004%" id="mcps1.2.6.1.4"><p id="en-us_topic_0214996140_p432316124312"><a name="en-us_topic_0214996140_p432316124312"></a><a name="en-us_topic_0214996140_p432316124312"></a>Level</p>
</th>
<th class="cellrowborder" valign="top" width="15.000000000000002%" id="mcps1.2.6.1.5"><p id="en-us_topic_0214996140_p83251674311"><a name="en-us_topic_0214996140_p83251674311"></a><a name="en-us_topic_0214996140_p83251674311"></a>Type</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0214996140_row132121615432"><td class="cellrowborder" rowspan="2" valign="top" width="24.000000000000004%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0214996140_p1232416104313"><a name="en-us_topic_0214996140_p1232416104313"></a><a name="en-us_topic_0214996140_p1232416104313"></a>OceanStor V5</p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0214996140_p9115125319436"><a name="en-us_topic_0214996140_p9115125319436"></a><a name="en-us_topic_0214996140_p9115125319436"></a>System user</p>
</td>
<td class="cellrowborder" valign="top" width="25.000000000000007%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0214996140_p203211654314"><a name="en-us_topic_0214996140_p203211654314"></a><a name="en-us_topic_0214996140_p203211654314"></a>Administrator</p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0214996140_p1732191664311"><a name="en-us_topic_0214996140_p1732191664311"></a><a name="en-us_topic_0214996140_p1732191664311"></a>Administrator</p>
</td>
<td class="cellrowborder" valign="top" width="15.000000000000002%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0214996140_p1532116144311"><a name="en-us_topic_0214996140_p1532116144311"></a><a name="en-us_topic_0214996140_p1532116144311"></a>Local user/LDAP user<sup id="sup1258215209344"><a name="sup1258215209344"></a><a name="sup1258215209344"></a>2</sup></p>
</td>
</tr>
<tr id="en-us_topic_0214996140_row217510214456"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0214996140_p1517512154515"><a name="en-us_topic_0214996140_p1517512154515"></a><a name="en-us_topic_0214996140_p1517512154515"></a>vStore user</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0214996140_p161761824457"><a name="en-us_topic_0214996140_p161761824457"></a><a name="en-us_topic_0214996140_p161761824457"></a>vStore administrator</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0214996140_p71768264519"><a name="en-us_topic_0214996140_p71768264519"></a><a name="en-us_topic_0214996140_p71768264519"></a>Administrator</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0214996140_p111763294517"><a name="en-us_topic_0214996140_p111763294517"></a><a name="en-us_topic_0214996140_p111763294517"></a>Local user/LDAP user<sup id="sup833010577497"><a name="sup833010577497"></a><a name="sup833010577497"></a>2</sup></p>
</td>
</tr>
<tr id="en-us_topic_0214996140_row163581026142419"><td class="cellrowborder" valign="top" width="24.000000000000004%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0214996140_p335942672413"><a name="en-us_topic_0214996140_p335942672413"></a><a name="en-us_topic_0214996140_p335942672413"></a>OceanStor</p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0214996140_p1129916445242"><a name="en-us_topic_0214996140_p1129916445242"></a><a name="en-us_topic_0214996140_p1129916445242"></a>System user</p>
</td>
<td class="cellrowborder" valign="top" width="25.000000000000007%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0214996140_p12299194414240"><a name="en-us_topic_0214996140_p12299194414240"></a><a name="en-us_topic_0214996140_p12299194414240"></a>Administrator/User-defined role<sup id="sup12377123124512"><a name="sup12377123124512"></a><a name="sup12377123124512"></a>1</sup></p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0214996140_p329910440244"><a name="en-us_topic_0214996140_p329910440244"></a><a name="en-us_topic_0214996140_p329910440244"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.000000000000002%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0214996140_p11299154442413"><a name="en-us_topic_0214996140_p11299154442413"></a><a name="en-us_topic_0214996140_p11299154442413"></a>Local user/LDAP user<sup id="sup183455575498"><a name="sup183455575498"></a><a name="sup183455575498"></a>2</sup></p>
</td>
</tr>
<tr id="en-us_topic_0214996140_row143210168434"><td class="cellrowborder" rowspan="2" valign="top" width="24.000000000000004%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0214996140_p23218164437"><a name="en-us_topic_0214996140_p23218164437"></a><a name="en-us_topic_0214996140_p23218164437"></a>OceanStor Dorado</p>
<p id="p58501367152"><a name="p58501367152"></a><a name="p58501367152"></a></p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0214996140_p13170324518"><a name="en-us_topic_0214996140_p13170324518"></a><a name="en-us_topic_0214996140_p13170324518"></a>System user</p>
</td>
<td class="cellrowborder" valign="top" width="25.000000000000007%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0214996140_p2045125319467"><a name="en-us_topic_0214996140_p2045125319467"></a><a name="en-us_topic_0214996140_p2045125319467"></a>Administrator/User-defined role<sup id="sup143334130"><a name="sup143334130"></a><a name="sup143334130"></a>1</sup></p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0214996140_p845125344614"><a name="en-us_topic_0214996140_p845125344614"></a><a name="en-us_topic_0214996140_p845125344614"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.000000000000002%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0214996140_p124515539466"><a name="en-us_topic_0214996140_p124515539466"></a><a name="en-us_topic_0214996140_p124515539466"></a>Local user/LDAP user<sup id="sup17345195710496"><a name="sup17345195710496"></a><a name="sup17345195710496"></a>2</sup></p>
</td>
</tr>
<tr id="en-us_topic_0214996140_row9761201434620"><td class="cellrowborder" valign="top" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0214996140_p117072165112"><a name="en-us_topic_0214996140_p117072165112"></a><a name="en-us_topic_0214996140_p117072165112"></a>vStore user</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0214996140_p14452053154610"><a name="en-us_topic_0214996140_p14452053154610"></a><a name="en-us_topic_0214996140_p14452053154610"></a>vStore administrator</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0214996140_p15451053204616"><a name="en-us_topic_0214996140_p15451053204616"></a><a name="en-us_topic_0214996140_p15451053204616"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0214996140_p1745125312460"><a name="en-us_topic_0214996140_p1745125312460"></a><a name="en-us_topic_0214996140_p1745125312460"></a>Local user/LDAP user<sup id="sup134665713499"><a name="sup134665713499"></a><a name="sup134665713499"></a>2</sup></p>
</td>
</tr>
<tr id="en-us_topic_0214996140_row85331119464"><td class="cellrowborder" valign="top" width="24.000000000000004%" headers="mcps1.2.6.1.1 "><p id="en-us_topic_0214996140_p10532011104612"><a name="en-us_topic_0214996140_p10532011104612"></a><a name="en-us_topic_0214996140_p10532011104612"></a>OceanStor Pacific series</p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0214996140_p145391184612"><a name="en-us_topic_0214996140_p145391184612"></a><a name="en-us_topic_0214996140_p145391184612"></a>System user</p>
</td>
<td class="cellrowborder" valign="top" width="25.000000000000007%" headers="mcps1.2.6.1.3 "><p id="en-us_topic_0214996140_p1453151116467"><a name="en-us_topic_0214996140_p1453151116467"></a><a name="en-us_topic_0214996140_p1453151116467"></a>Administrator</p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.4 "><p id="en-us_topic_0214996140_p1753131112468"><a name="en-us_topic_0214996140_p1753131112468"></a><a name="en-us_topic_0214996140_p1753131112468"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.000000000000002%" headers="mcps1.2.6.1.5 "><p id="en-us_topic_0214996140_p4533113468"><a name="en-us_topic_0214996140_p4533113468"></a><a name="en-us_topic_0214996140_p4533113468"></a>Local user</p>
</td>
</tr>
<tr id="row27531822552"><td class="cellrowborder" valign="top" width="24.000000000000004%" headers="mcps1.2.6.1.1 "><p id="p1575442105515"><a name="p1575442105515"></a><a name="p1575442105515"></a>OceanDisk</p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.2 "><p id="p77542219556"><a name="p77542219556"></a><a name="p77542219556"></a>System user</p>
</td>
<td class="cellrowborder" valign="top" width="25.000000000000007%" headers="mcps1.2.6.1.3 "><p id="p1175472185518"><a name="p1175472185518"></a><a name="p1175472185518"></a>Administrator</p>
</td>
<td class="cellrowborder" valign="top" width="18.000000000000004%" headers="mcps1.2.6.1.4 "><p id="p375414285512"><a name="p375414285512"></a><a name="p375414285512"></a>N/A</p>
</td>
<td class="cellrowborder" valign="top" width="15.000000000000002%" headers="mcps1.2.6.1.5 "><p id="p19754152135515"><a name="p19754152135515"></a><a name="p19754152135515"></a>Local user</p>
</td>
</tr>
</tbody>
</table>

-   Note 1: If a user-defined role is used, you need to configure permissions for the role. For details about how to configure the minimum permissions, see  [Configuring Custom Permissions](/docs/appendix/configuring-custom-permissions).
-   Note 2: If LDAP authentication is used, you need to configure the  **authenticationMode**  parameter during backend creation. For details, see  [Storage Backend Parameters](/docs/storage-backend-management/managing-storage-backends/creating-a-storage-backend/storage-backend-parameters).

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>You are advised not to use the users of the super administrator role.

