---
title: "Configuring Storage Topology Awareness"
linkTitle: "Configuring Storage Topology Awareness"
description: 
weight: 9
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

    **Table  1**  Description of topology label parameters

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

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
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

## Procedure{#section2619114191417}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Go to the directory where the Helm project is located. If the previous Helm project cannot be found, copy the  **helm**  directory in the component package to any directory on the master node. For details about the component package path, see  [Table 1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).
3.  Go to the backend service configuration directory  **/examples/backend/**  and back up the  **backend.yaml**  file.

    ```
    cp backend.yaml backend.yaml.bak
    ```

4.  Run the  **vi backend.yaml**  command to open the file and configure topology awareness as required. The following is an example. After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

    ```yaml
    storage: "oceanstor-san"
    name: "dorado-iscsi-155"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.155:8088"
    pools:
      - "StoragePool001"
    parameters:
      protocol: "iscsi"
      portals:
        - "10.10.30.20"
        - "10.10.30.21"
    supportedTopologies:
      - { "topology.kubernetes.io/region": "China-west", "topology.kubernetes.io/zone": "ChengDu" }
      - { "topology.kubernetes.io/region": "China-south","topology.kubernetes.io/zone": "ShenZhen" }
    maxClientThreads: "30"
    ```

5.  Run the following command to delete the storage backend to be modified. In the command,  **dorado-iscsi-155**  indicates the storage backend name.

    ```
    oceanctl delete backend dorado-iscsi-155 -n huawei-csi
    ```

6.  Run the following command to create a storage backend.

    ```
    oceanctl create backend -f ../examples/backend/backend.yaml -i yaml
    ```

    Enter the storage user name and password as prompted.

    ```
    Please enter this backend user name:admin
    Please enter this backend password:
    ```

7.  Run the  **vi StorageClass.yaml**  command to modify the .yaml file. Press  **I**  or  **Insert**  to enter the insert mode and add related parameters in the .yaml file. For details about the parameters, see  [Table 2](#en-us_topic_0000001352573769_table118458471087). After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

    Add the following configuration items to the  _StorageClass.yaml_  file.

    -   Example 1: Configure zone and region information in the StorageClass.

        ```yaml
        kind: StorageClass
        apiVersion: storage.k8s.io/v1
        metadata:
          name: example-storageclass
        provisioner: csi.huawei.com
        parameters:
          volumeType: lun
          allocType: thin
        volumeBindingMode: WaitForFirstConsumer
        allowedTopologies:
        - matchLabelExpressions:
          - key: topology.kubernetes.io/zone
            values:
            - ChengDu
          - key: topology.kubernetes.io/region
            values:
            - China-west
        ```

    -   Example 2: Configure protocol information in the StorageClass.

        ```yaml
        kind: StorageClass
        apiVersion: storage.k8s.io/v1
        metadata:
          name: protocol-example-storageclass
        provisioner: csi.huawei.com
        parameters:
          volumeType: lun
          allocType: thin
        volumeBindingMode: WaitForFirstConsumer
        allowedTopologies:
        - matchLabelExpressions:
          - key: topology.kubernetes.io/protocol.iscsi
            values:
            - csi.huawei.com
        ```

    **Table  2**  StorageClass parameter description

    <a name="en-us_topic_0000001352573769_table118458471087"></a>
    <table><thead align="left"><tr id="en-us_topic_0000001352573769_row138455475813"><th class="cellrowborder" valign="top" width="21.04210421042104%" id="mcps1.2.4.1.1"><p id="en-us_topic_0000001352573769_p6214454784"><a name="en-us_topic_0000001352573769_p6214454784"></a><a name="en-us_topic_0000001352573769_p6214454784"></a>Parameter</p>
    </th>
    <th class="cellrowborder" valign="top" width="24.752475247524753%" id="mcps1.2.4.1.2"><p id="en-us_topic_0000001352573769_p1821455414813"><a name="en-us_topic_0000001352573769_p1821455414813"></a><a name="en-us_topic_0000001352573769_p1821455414813"></a>Description</p>
    </th>
    <th class="cellrowborder" valign="top" width="54.205420542054206%" id="mcps1.2.4.1.3"><p id="en-us_topic_0000001352573769_p12214105415811"><a name="en-us_topic_0000001352573769_p12214105415811"></a><a name="en-us_topic_0000001352573769_p12214105415811"></a>Remarks</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="en-us_topic_0000001352573769_row168451947281"><td class="cellrowborder" valign="top" width="21.04210421042104%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001352573769_p192141054287"><a name="en-us_topic_0000001352573769_p192141054287"></a><a name="en-us_topic_0000001352573769_p192141054287"></a><strong id="en-us_topic_0000001352573769_b14214754184"><a name="en-us_topic_0000001352573769_b14214754184"></a><a name="en-us_topic_0000001352573769_b14214754184"></a>volumeBindingMode</strong></p>
    </td>
    <td class="cellrowborder" valign="top" width="24.752475247524753%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001352573769_p1421413541688"><a name="en-us_topic_0000001352573769_p1421413541688"></a><a name="en-us_topic_0000001352573769_p1421413541688"></a>PersistentVolume binding mode, used to control the time when PersistentVolume resources are dynamically allocated and bound.</p>
    </td>
    <td class="cellrowborder" valign="top" width="54.205420542054206%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001352573769_p921485415817"><a name="en-us_topic_0000001352573769_p921485415817"></a><a name="en-us_topic_0000001352573769_p921485415817"></a>You can set this parameter to <span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue154917598306"><a name="en-us_topic_0000001352573769_parmvalue154917598306"></a><a name="en-us_topic_0000001352573769_parmvalue154917598306"></a><b>WaitForFirstConsumer</b></span> or <span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue1549117599305"><a name="en-us_topic_0000001352573769_parmvalue1549117599305"></a><a name="en-us_topic_0000001352573769_parmvalue1549117599305"></a><b>Immediate</b></span>.</p>
    <p id="en-us_topic_0000001352573769_p1021416541812"><a name="en-us_topic_0000001352573769_p1021416541812"></a><a name="en-us_topic_0000001352573769_p1021416541812"></a><span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue10208754317"><a name="en-us_topic_0000001352573769_parmvalue10208754317"></a><a name="en-us_topic_0000001352573769_parmvalue10208754317"></a><b>WaitForFirstConsumer</b></span>: indicates that the binding and allocation of the PersistentVolume are delayed until a Pod that uses the PVC is created.</p>
    <p id="en-us_topic_0000001352573769_p204525554212"><a name="en-us_topic_0000001352573769_p204525554212"></a><a name="en-us_topic_0000001352573769_p204525554212"></a><span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue7611316317"><a name="en-us_topic_0000001352573769_parmvalue7611316317"></a><a name="en-us_topic_0000001352573769_parmvalue7611316317"></a><b>Immediate</b></span>: The PersistentVolume is bound and allocated immediately after a PVC is created.</p>
    </td>
    </tr>
    <tr id="en-us_topic_0000001352573769_row78451447983"><td class="cellrowborder" rowspan="2" valign="top" width="21.04210421042104%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001352573769_p821410541784"><a name="en-us_topic_0000001352573769_p821410541784"></a><a name="en-us_topic_0000001352573769_p821410541784"></a><strong id="en-us_topic_0000001352573769_b1421417545816"><a name="en-us_topic_0000001352573769_b1421417545816"></a><a name="en-us_topic_0000001352573769_b1421417545816"></a>allowedTopologies.matchLabelExpressions</strong></p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="24.752475247524753%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001352573769_p52141154281"><a name="en-us_topic_0000001352573769_p52141154281"></a><a name="en-us_topic_0000001352573769_p52141154281"></a>Topology information label, which is used to filter CSI backends and Kubernetes nodes. If the matching fails, PVCs or Pods cannot be created.</p>
    <p id="en-us_topic_0000001352573769_p142147540815"><a name="en-us_topic_0000001352573769_p142147540815"></a><a name="en-us_topic_0000001352573769_p142147540815"></a>Both <span class="parmname" id="en-us_topic_0000001352573769_parmname1861343213319"><a name="en-us_topic_0000001352573769_parmname1861343213319"></a><a name="en-us_topic_0000001352573769_parmname1861343213319"></a><b>key</b></span> and <span class="parmname" id="en-us_topic_0000001352573769_parmname1161312324312"><a name="en-us_topic_0000001352573769_parmname1161312324312"></a><a name="en-us_topic_0000001352573769_parmname1161312324312"></a><b>values</b></span> must be configured in a fixed format.</p>
    </td>
    <td class="cellrowborder" valign="top" width="54.205420542054206%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001352573769_p182141254384"><a name="en-us_topic_0000001352573769_p182141254384"></a><a name="en-us_topic_0000001352573769_p182141254384"></a><span class="parmname" id="en-us_topic_0000001352573769_parmname390803812312"><a name="en-us_topic_0000001352573769_parmname390803812312"></a><a name="en-us_topic_0000001352573769_parmname390803812312"></a><b>key</b></span>: This parameter can be set to <span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue1990933813119"><a name="en-us_topic_0000001352573769_parmvalue1990933813119"></a><a name="en-us_topic_0000001352573769_parmvalue1990933813119"></a><b>topology.kubernetes.io/zone</b></span> or <span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue190973817313"><a name="en-us_topic_0000001352573769_parmvalue190973817313"></a><a name="en-us_topic_0000001352573769_parmvalue190973817313"></a><b>topology.kubernetes.io/region</b></span>.</p>
    <p id="en-us_topic_0000001352573769_p321410548819"><a name="en-us_topic_0000001352573769_p321410548819"></a><a name="en-us_topic_0000001352573769_p321410548819"></a><strong id="en-us_topic_0000001352573769_b8422184383119"><a name="en-us_topic_0000001352573769_b8422184383119"></a><a name="en-us_topic_0000001352573769_b8422184383119"></a>topology.kubernetes.io/protocol.</strong><em id="en-us_topic_0000001352573769_i19423104393112"><a name="en-us_topic_0000001352573769_i19423104393112"></a><a name="en-us_topic_0000001352573769_i19423104393112"></a>&lt;protocol&gt;</em>: <em id="en-us_topic_0000001352573769_i144232043193116"><a name="en-us_topic_0000001352573769_i144232043193116"></a><a name="en-us_topic_0000001352573769_i144232043193116"></a>&lt;protocol&gt;</em> indicates the protocol type and can be <strong id="en-us_topic_0000001352573769_b12423114383113"><a name="en-us_topic_0000001352573769_b12423114383113"></a><a name="en-us_topic_0000001352573769_b12423114383113"></a>iscsi</strong>, <strong id="en-us_topic_0000001352573769_b12424543153113"><a name="en-us_topic_0000001352573769_b12424543153113"></a><a name="en-us_topic_0000001352573769_b12424543153113"></a>fc</strong>, or <strong id="en-us_topic_0000001352573769_b1142410439318"><a name="en-us_topic_0000001352573769_b1142410439318"></a><a name="en-us_topic_0000001352573769_b1142410439318"></a>nfs</strong>.</p>
    </td>
    </tr>
    <tr id="en-us_topic_0000001352573769_row85481628121017"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001352573769_p1209324123216"><a name="en-us_topic_0000001352573769_p1209324123216"></a><a name="en-us_topic_0000001352573769_p1209324123216"></a><span class="parmname" id="en-us_topic_0000001352573769_parmname152098242326"><a name="en-us_topic_0000001352573769_parmname152098242326"></a><a name="en-us_topic_0000001352573769_parmname152098242326"></a><b>values</b></span>:</p>
    <p id="en-us_topic_0000001352573769_p1024122115329"><a name="en-us_topic_0000001352573769_p1024122115329"></a><a name="en-us_topic_0000001352573769_p1024122115329"></a>If <span class="parmname" id="parmname208347569183"><a name="parmname208347569183"></a><a name="parmname208347569183"></a><b>key</b></span> is <span class="parmvalue" id="parmvalue1783415671817"><a name="parmvalue1783415671817"></a><a name="parmvalue1783415671817"></a><b>topology.kubernetes.io/zone</b></span> or <span class="parmvalue" id="parmvalue1383405681818"><a name="parmvalue1383405681818"></a><a name="parmvalue1383405681818"></a><b>topology.kubernetes.io/region</b></span>, <span class="parmname" id="parmname18834205691818"><a name="parmname18834205691818"></a><a name="parmname18834205691818"></a><b>values</b></span> must be the same as that in <a href="/css-docs/en/docs/common-o-m-operations/configuring-storage-topology-awareness#en-us_topic_0000001200451233_section12171124814413">Prerequisites</a>.</p>
    <p id="en-us_topic_0000001352573769_p195481328151018"><a name="en-us_topic_0000001352573769_p195481328151018"></a><a name="en-us_topic_0000001352573769_p195481328151018"></a>If <span class="parmname" id="en-us_topic_0000001352573769_parmname13144742173219"><a name="en-us_topic_0000001352573769_parmname13144742173219"></a><a name="en-us_topic_0000001352573769_parmname13144742173219"></a><b>key</b></span> is <strong id="en-us_topic_0000001352573769_b1914414427326"><a name="en-us_topic_0000001352573769_b1914414427326"></a><a name="en-us_topic_0000001352573769_b1914414427326"></a>topology.kubernetes.io/protocol.</strong><em id="en-us_topic_0000001352573769_i14145194283217"><a name="en-us_topic_0000001352573769_i14145194283217"></a><a name="en-us_topic_0000001352573769_i14145194283217"></a>&lt;protocol&gt;</em>, <span class="parmname" id="en-us_topic_0000001352573769_parmname1114654215323"><a name="en-us_topic_0000001352573769_parmname1114654215323"></a><a name="en-us_topic_0000001352573769_parmname1114654215323"></a><b>value</b></span> is fixed at <span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue9146174218322"><a name="en-us_topic_0000001352573769_parmvalue9146174218322"></a><a name="en-us_topic_0000001352573769_parmvalue9146174218322"></a><b>csi.huawei.com</b></span>.</p>
    </td>
    </tr>
    </tbody>
    </table>

8.  Run the following command to create a StorageClass based on the .yaml file.

    ```
    kubectl create -f StorgeClass.yaml
    ```

9.  Use the StorageClass to create a PVC with the topology capability. For details, see  [Table 1](/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#en-us_topic_0150885187_table195731435604).

