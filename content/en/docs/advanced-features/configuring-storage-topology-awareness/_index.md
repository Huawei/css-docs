---
title: "Configuring Storage Topology Awareness"
linkTitle: "Configuring Storage Topology Awareness"
description: 
weight: 2
---

In the Kubernetes cluster, resources can be scheduled and provisioned based on the topology labels of nodes and the topology capabilities supported by storage backends.

## Prerequisites{#en-us_topic_0000001200451233_section12171124814413}

You need to configure topology labels on worker nodes in the cluster. The method is as follows:

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Run the following command to view information about worker nodes in the current cluster.

    ```
    kubectl get node
    ```

    The following is an example of the command output.

    ```
    NAME     STATUS   ROLES                      AGE   VERSION
    node01   Ready    controlplane,etcd,worker   42d   v1.22.3
    node02   Ready    worker                     42d   v1.22.3
    node03   Ready    worker                     42d   v1.22.3
    ```

3.  Run the following command to configure a topology label for a worker node. In the preceding command,  _nodename_  indicates the name of a worker node. For details about the  **key**  and  **value**  parameters, see  [Table 1](#en-us_topic_0000001200451233_table1261817418166).

    ```
    kubectl label node <nodename> <key>=<value>
    ```

    **Table  1**  Parameter description

    <a name="en-us_topic_0000001200451233_table1261817418166"></a>
    <table><thead align="left"><tr id="en-us_topic_0000001200451233_row1361864114165"><th class="cellrowborder" valign="top" width="16.5016501650165%" id="mcps1.2.4.1.1"><p id="en-us_topic_0000001200451233_p0862145011168"><a name="en-us_topic_0000001200451233_p0862145011168"></a><a name="en-us_topic_0000001200451233_p0862145011168"></a>Parameter</p>
    </th>
    <th class="cellrowborder" valign="top" width="30.673067306730672%" id="mcps1.2.4.1.2"><p id="en-us_topic_0000001200451233_p8862175081616"><a name="en-us_topic_0000001200451233_p8862175081616"></a><a name="en-us_topic_0000001200451233_p8862175081616"></a>Description</p>
    </th>
    <th class="cellrowborder" valign="top" width="52.82528252825283%" id="mcps1.2.4.1.3"><p id="en-us_topic_0000001200451233_p6862350191614"><a name="en-us_topic_0000001200451233_p6862350191614"></a><a name="en-us_topic_0000001200451233_p6862350191614"></a>Remarks</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="en-us_topic_0000001200451233_row1061815413161"><td class="cellrowborder" valign="top" width="16.5016501650165%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001200451233_p171281559121615"><a name="en-us_topic_0000001200451233_p171281559121615"></a><a name="en-us_topic_0000001200451233_p171281559121615"></a>&lt;key&gt;</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.673067306730672%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001200451233_p13618144119164"><a name="en-us_topic_0000001200451233_p13618144119164"></a><a name="en-us_topic_0000001200451233_p13618144119164"></a>Unique identifier of a topology label.</p>
    </td>
    <td class="cellrowborder" valign="top" width="52.82528252825283%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001200451233_p993021810189"><a name="en-us_topic_0000001200451233_p993021810189"></a><a name="en-us_topic_0000001200451233_p993021810189"></a>The value can be <strong id="en-us_topic_0000001200451233_b2052813519618"><a name="en-us_topic_0000001200451233_b2052813519618"></a><a name="en-us_topic_0000001200451233_b2052813519618"></a>zone</strong>, <strong id="en-us_topic_0000001200451233_b231419532615"><a name="en-us_topic_0000001200451233_b231419532615"></a><a name="en-us_topic_0000001200451233_b231419532615"></a>region</strong>, or <strong id="en-us_topic_0000001200451233_b283555405316"><a name="en-us_topic_0000001200451233_b283555405316"></a><a name="en-us_topic_0000001200451233_b283555405316"></a>protocol.</strong><em id="en-us_topic_0000001200451233_i1141625719538"><a name="en-us_topic_0000001200451233_i1141625719538"></a><a name="en-us_topic_0000001200451233_i1141625719538"></a>&lt;protocol&gt;</em>.</p>
    <p id="en-us_topic_0000001200451233_p20771183412190"><a name="en-us_topic_0000001200451233_p20771183412190"></a><a name="en-us_topic_0000001200451233_p20771183412190"></a><em id="en-us_topic_0000001200451233_i9771143416191"><a name="en-us_topic_0000001200451233_i9771143416191"></a><a name="en-us_topic_0000001200451233_i9771143416191"></a>&lt;protocol&gt;</em> can be set to <strong id="en-us_topic_0000001200451233_b1096018264714"><a name="en-us_topic_0000001200451233_b1096018264714"></a><a name="en-us_topic_0000001200451233_b1096018264714"></a>iscsi</strong>, <strong id="en-us_topic_0000001200451233_b7530122818712"><a name="en-us_topic_0000001200451233_b7530122818712"></a><a name="en-us_topic_0000001200451233_b7530122818712"></a>nfs</strong>, <strong id="en-us_topic_0000001200451233_b46971529678"><a name="en-us_topic_0000001200451233_b46971529678"></a><a name="en-us_topic_0000001200451233_b46971529678"></a>fc</strong>, or <strong id="en-us_topic_0000001200451233_b14113103116719"><a name="en-us_topic_0000001200451233_b14113103116719"></a><a name="en-us_topic_0000001200451233_b14113103116719"></a>roce</strong>.</p>
    </td>
    </tr>
    <tr id="en-us_topic_0000001200451233_row3618164119162"><td class="cellrowborder" valign="top" width="16.5016501650165%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001200451233_p15618164181619"><a name="en-us_topic_0000001200451233_p15618164181619"></a><a name="en-us_topic_0000001200451233_p15618164181619"></a>&lt;value&gt;</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.673067306730672%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001200451233_p1961804121614"><a name="en-us_topic_0000001200451233_p1961804121614"></a><a name="en-us_topic_0000001200451233_p1961804121614"></a>Value of a topology label.</p>
    </td>
    <td class="cellrowborder" valign="top" width="52.82528252825283%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001200451233_p89541533122011"><a name="en-us_topic_0000001200451233_p89541533122011"></a><a name="en-us_topic_0000001200451233_p89541533122011"></a>If <span class="parmname" id="en-us_topic_0000001200451233_parmname2954633172020"><a name="en-us_topic_0000001200451233_parmname2954633172020"></a><a name="en-us_topic_0000001200451233_parmname2954633172020"></a><b>key</b></span> is set to <span class="parmvalue" id="en-us_topic_0000001200451233_parmvalue11954123318209"><a name="en-us_topic_0000001200451233_parmvalue11954123318209"></a><a name="en-us_topic_0000001200451233_parmvalue11954123318209"></a><b>zone</b></span> or <span class="parmvalue" id="en-us_topic_0000001200451233_parmvalue2095415339208"><a name="en-us_topic_0000001200451233_parmvalue2095415339208"></a><a name="en-us_topic_0000001200451233_parmvalue2095415339208"></a><b>region</b></span>, <span class="parmname" id="en-us_topic_0000001200451233_parmname1954193352013"><a name="en-us_topic_0000001200451233_parmname1954193352013"></a><a name="en-us_topic_0000001200451233_parmname1954193352013"></a><b>value</b></span> is a user-defined parameter.</p>
    <p id="en-us_topic_0000001200451233_p44843300202"><a name="en-us_topic_0000001200451233_p44843300202"></a><a name="en-us_topic_0000001200451233_p44843300202"></a>If <span class="parmname" id="en-us_topic_0000001200451233_parmname2048443072017"><a name="en-us_topic_0000001200451233_parmname2048443072017"></a><a name="en-us_topic_0000001200451233_parmname2048443072017"></a><b>key</b></span> is set to <strong id="en-us_topic_0000001200451233_b1943715189548"><a name="en-us_topic_0000001200451233_b1943715189548"></a><a name="en-us_topic_0000001200451233_b1943715189548"></a>protocol.</strong><em id="en-us_topic_0000001200451233_i17437218165414"><a name="en-us_topic_0000001200451233_i17437218165414"></a><a name="en-us_topic_0000001200451233_i17437218165414"></a>&lt;protocol&gt;</em>, <span class="parmname" id="en-us_topic_0000001200451233_parmname19484143018201"><a name="en-us_topic_0000001200451233_parmname19484143018201"></a><a name="en-us_topic_0000001200451233_parmname19484143018201"></a><b>value</b></span> is fixed at <span class="parmvalue" id="en-us_topic_0000001200451233_parmvalue5484133020209"><a name="en-us_topic_0000001200451233_parmvalue5484133020209"></a><a name="en-us_topic_0000001200451233_parmvalue5484133020209"></a><b>csi.huawei.com</b></span>.</p>
    </td>
    </tr>
    </tbody>
    </table>

    >![](/css-docs/public_sys-resources/en/icon-note.gif)
    >-   A topology label must start with  **topology.kubernetes.io**. Topology label examples:
    >    -   Example 1:  **topology.kubernetes.io/region=China-west**
    >    -   Example 2:  **topology.kubernetes.io/zone=ChengDu**
    >    -   Example 3:  **topology.kubernetes.io/protocol.iscsi=csi.huawei.com**
    >    -   Example 4:  **topology.kubernetes.io/protocol.fc=csi.huawei.com**
    >-   A key in a topology label on a node can have only one value.
    >-   If multiple protocols are configured in a topology label on a node, when you configure a StorageClass, the StorageClass needs to meet only one of the protocols.
    >-   If both the region and the zone are configured in a topology label on a node, when you configure a StorageClass, the StorageClass must meet all filter criteria.

4.  Run the following command to view the label information about all worker nodes in the current cluster.

    ```
    kubectl get nodes -o=jsonpath='{range .items[*]}[{.metadata.name}, {.metadata.labels}]{"\n"}{end}' | grep --color "topology.kubernetes.io"
    ```

    The following is an example of the command output.

    ```
    [node01,"beta.kubernetes.io/arch":"amd64","beta.kubernetes.io/os":"linux","kubernetes.io/arch":"amd64","kubernetes.io/hostname":"node01","kubernetes.io/os":"linux","node-role.kubernetes.io/controlplane":"true","node-role.kubernetes.io/etcd":"true","node-role.kubernetes.io/worker":"true","topology.kubernetes.io/zone":"ChengDu"}]
    ```


