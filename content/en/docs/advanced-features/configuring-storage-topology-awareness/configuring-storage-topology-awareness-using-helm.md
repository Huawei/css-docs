---
title: "Configuring Storage Topology Awareness Using Helm"
linkTitle: "Configuring Storage Topology Awareness Using Helm"
description: 
weight: 1
---

## Procedure{#en-us_topic_0000001352573769_section748483471312}

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Go to the directory where the Helm project is located. If the previous Helm project cannot be found, copy the  **helm**  directory in the component package to any directory on the master node. For details about the component package path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).
3.  Go to the backend service configuration directory  **/examples/backend/**  and back up the  **backend.yaml**  file.

    ```
    cp backend.yaml backend.yaml.bak
    ```

4.  Run the  **vi **_backend.yaml_  command to open the file and configure topology awareness as required. The following is an example. After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

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

7.  Run the  **vi StorageClass.yaml**  command to modify the .yaml file. Press  **I**  or  **Insert**  to enter the insert mode and add related parameters in the .yaml file. For details about the parameters, see  [Table 1](#en-us_topic_0000001352573769_table118458471087). After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

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

    **Table  1**  Parameter description

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
    <p id="en-us_topic_0000001352573769_p142147540815"><a name="en-us_topic_0000001352573769_p142147540815"></a><a name="en-us_topic_0000001352573769_p142147540815"></a>Both <span class="parmname" id="en-us_topic_0000001352573769_parmname1861343213319"><a name="en-us_topic_0000001352573769_parmname1861343213319"></a><a name="en-us_topic_0000001352573769_parmname1861343213319"></a><b>key</b></span> and <span class="parmname" id="en-us_topic_0000001352573769_parmname1161312324312"><a name="en-us_topic_0000001352573769_parmname1161312324312"></a><a name="en-us_topic_0000001352573769_parmname1161312324312"></a><b>value</b></span> must be configured in a fixed format.</p>
    </td>
    <td class="cellrowborder" valign="top" width="54.205420542054206%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001352573769_p182141254384"><a name="en-us_topic_0000001352573769_p182141254384"></a><a name="en-us_topic_0000001352573769_p182141254384"></a><span class="parmname" id="en-us_topic_0000001352573769_parmname390803812312"><a name="en-us_topic_0000001352573769_parmname390803812312"></a><a name="en-us_topic_0000001352573769_parmname390803812312"></a><b>key</b></span>: This parameter can be set to <span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue1990933813119"><a name="en-us_topic_0000001352573769_parmvalue1990933813119"></a><a name="en-us_topic_0000001352573769_parmvalue1990933813119"></a><b>topology.kubernetes.io/zone</b></span> or <span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue190973817313"><a name="en-us_topic_0000001352573769_parmvalue190973817313"></a><a name="en-us_topic_0000001352573769_parmvalue190973817313"></a><b>topology.kubernetes.io/region</b></span>.</p>
    <p id="en-us_topic_0000001352573769_p321410548819"><a name="en-us_topic_0000001352573769_p321410548819"></a><a name="en-us_topic_0000001352573769_p321410548819"></a><strong id="en-us_topic_0000001352573769_b8422184383119"><a name="en-us_topic_0000001352573769_b8422184383119"></a><a name="en-us_topic_0000001352573769_b8422184383119"></a>topology.kubernetes.io/protocol.</strong><em id="en-us_topic_0000001352573769_i19423104393112"><a name="en-us_topic_0000001352573769_i19423104393112"></a><a name="en-us_topic_0000001352573769_i19423104393112"></a>&lt;protocol&gt;</em>: <em id="en-us_topic_0000001352573769_i144232043193116"><a name="en-us_topic_0000001352573769_i144232043193116"></a><a name="en-us_topic_0000001352573769_i144232043193116"></a>&lt;protocol&gt;</em> indicates the protocol type and can be <strong id="en-us_topic_0000001352573769_b12423114383113"><a name="en-us_topic_0000001352573769_b12423114383113"></a><a name="en-us_topic_0000001352573769_b12423114383113"></a>iscsi</strong>, <strong id="en-us_topic_0000001352573769_b12424543153113"><a name="en-us_topic_0000001352573769_b12424543153113"></a><a name="en-us_topic_0000001352573769_b12424543153113"></a>fc</strong>, or <strong id="en-us_topic_0000001352573769_b1142410439318"><a name="en-us_topic_0000001352573769_b1142410439318"></a><a name="en-us_topic_0000001352573769_b1142410439318"></a>nfs</strong>.</p>
    </td>
    </tr>
    <tr id="en-us_topic_0000001352573769_row85481628121017"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001352573769_p1209324123216"><a name="en-us_topic_0000001352573769_p1209324123216"></a><a name="en-us_topic_0000001352573769_p1209324123216"></a><span class="parmname" id="en-us_topic_0000001352573769_parmname1166435611312"><a name="en-us_topic_0000001352573769_parmname1166435611312"></a><a name="en-us_topic_0000001352573769_parmname1166435611312"></a><b>value</b></span>:</p>
    <p id="en-us_topic_0000001352573769_p1024122115329"><a name="en-us_topic_0000001352573769_p1024122115329"></a><a name="en-us_topic_0000001352573769_p1024122115329"></a>If <span class="parmname" id="parmname6687855171313"><a name="parmname6687855171313"></a><a name="parmname6687855171313"></a><b>key</b></span> is <span class="parmvalue" id="parmvalue4687135517137"><a name="parmvalue4687135517137"></a><a name="parmvalue4687135517137"></a><b>topology.kubernetes.io/zone</b></span> or <span class="parmvalue" id="parmvalue19687165512136"><a name="parmvalue19687165512136"></a><a name="parmvalue19687165512136"></a><b>topology.kubernetes.io/region</b></span>, <span class="parmname" id="parmname1168755519130"><a name="parmname1168755519130"></a><a name="parmname1168755519130"></a><b>value</b></span> must be the same as the <a href="configuring-storage-topology-awareness.md#en-us_topic_0000001200451233_section12171124814413">topology label set in the prerequisites</a>.</p>
    <p id="en-us_topic_0000001352573769_p195481328151018"><a name="en-us_topic_0000001352573769_p195481328151018"></a><a name="en-us_topic_0000001352573769_p195481328151018"></a>If <span class="parmname" id="en-us_topic_0000001352573769_parmname13144742173219"><a name="en-us_topic_0000001352573769_parmname13144742173219"></a><a name="en-us_topic_0000001352573769_parmname13144742173219"></a><b>key</b></span> is <strong id="en-us_topic_0000001352573769_b1914414427326"><a name="en-us_topic_0000001352573769_b1914414427326"></a><a name="en-us_topic_0000001352573769_b1914414427326"></a>topology.kubernetes.io/protocol.</strong><em id="en-us_topic_0000001352573769_i14145194283217"><a name="en-us_topic_0000001352573769_i14145194283217"></a><a name="en-us_topic_0000001352573769_i14145194283217"></a>&lt;protocol&gt;</em>, <span class="parmname" id="en-us_topic_0000001352573769_parmname1114654215323"><a name="en-us_topic_0000001352573769_parmname1114654215323"></a><a name="en-us_topic_0000001352573769_parmname1114654215323"></a><b>value</b></span> is fixed at <span class="parmvalue" id="en-us_topic_0000001352573769_parmvalue9146174218322"><a name="en-us_topic_0000001352573769_parmvalue9146174218322"></a><a name="en-us_topic_0000001352573769_parmvalue9146174218322"></a><b>csi.huawei.com</b></span>.</p>
    </td>
    </tr>
    </tbody>
    </table>

8.  Run the following command to create a StorageClass based on the .yaml file.

    ```
    kubectl create -f StorgeClass.yaml
    ```

9.  Use the StorageClass to create a PVC with the topology capability. For details, see  [PVC Parameters for Dynamic Volume Provisioning](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning).

