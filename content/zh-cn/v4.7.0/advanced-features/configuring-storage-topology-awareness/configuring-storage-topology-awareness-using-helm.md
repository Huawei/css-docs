---
title: "通过Helm配置存储拓扑感知"
linkTitle: "通过Helm配置存储拓扑感知"
description: 
weight: 1
---

## 操作步骤{#zh-cn_topic_0000001352573769_section748483471312}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  进入Helm工程的目录下，如果无法找到之前的Helm工程，则将组件包中的helm目录拷贝到master节点的任意目录下，组件包路径请参考[表1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。
3.  进入后端服务配置目录/examples/backend/下，备份backend.yaml文件

    ```
    cp backend.yaml backend.yaml.bak
    ```

4.  执行  **vi backend.yaml**  命令打开文件，按需求配置拓扑感知，示例如下所示。修改完成后，按  **Esc**  并输入  **:wq!**  ，保存修改。

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

5.  执行以下命令删除待修改存储后端，其中“dorado-iscsi-155”为存储后端名称。

    ```
    oceanctl delete backend dorado-iscsi-155 -n huawei-csi
    ```

6.  执行以下命令创建存储后端。

    ```
    oceanctl create backend -f ../examples/backend/backend.yaml -i yaml
    ```

    根据命令提示输入存储用户名和密码。

    ```
    Please enter this backend user name:admin
    Please enter this backend password:
    ```

7.  执行** vi StorageClass.yaml**  命令，修改yaml文件。按  **I**  或  **Insert**  进入编辑状态，在yaml文件下增加相关参数，详细参数说明请参见[表1](#zh-cn_topic_0000001352573769_table118458471087)。修改完成后，按  **Esc**  并输入  **:wq!**  ，保存修改。

    在StorageClass.yaml文件中添加以下配置项。

    -   示例1： 在StorageClass中配置zone和region信息

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

    -   示例2： 在StorageClass中配置协议信息

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

    **表 1**  参数说明

    <a name="zh-cn_topic_0000001352573769_table118458471087"></a>
    <table><thead align="left"><tr id="zh-cn_topic_0000001352573769_row138455475813"><th class="cellrowborder" valign="top" width="21.04210421042104%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0000001352573769_p6214454784"><a name="zh-cn_topic_0000001352573769_p6214454784"></a><a name="zh-cn_topic_0000001352573769_p6214454784"></a>参数名</p>
    </th>
    <th class="cellrowborder" valign="top" width="24.752475247524753%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0000001352573769_p1821455414813"><a name="zh-cn_topic_0000001352573769_p1821455414813"></a><a name="zh-cn_topic_0000001352573769_p1821455414813"></a>参数描述</p>
    </th>
    <th class="cellrowborder" valign="top" width="54.205420542054206%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0000001352573769_p12214105415811"><a name="zh-cn_topic_0000001352573769_p12214105415811"></a><a name="zh-cn_topic_0000001352573769_p12214105415811"></a>备注</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="zh-cn_topic_0000001352573769_row168451947281"><td class="cellrowborder" valign="top" width="21.04210421042104%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001352573769_p192141054287"><a name="zh-cn_topic_0000001352573769_p192141054287"></a><a name="zh-cn_topic_0000001352573769_p192141054287"></a><strong id="zh-cn_topic_0000001352573769_b14214754184"><a name="zh-cn_topic_0000001352573769_b14214754184"></a><a name="zh-cn_topic_0000001352573769_b14214754184"></a>volumeBindingMode</strong></p>
    </td>
    <td class="cellrowborder" valign="top" width="24.752475247524753%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001352573769_p1421413541688"><a name="zh-cn_topic_0000001352573769_p1421413541688"></a><a name="zh-cn_topic_0000001352573769_p1421413541688"></a>PersistentVolume绑定方式，用于控制何时进行PersistentVolume动态资源调配和绑定。</p>
    </td>
    <td class="cellrowborder" valign="top" width="54.205420542054206%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001352573769_p921485415817"><a name="zh-cn_topic_0000001352573769_p921485415817"></a><a name="zh-cn_topic_0000001352573769_p921485415817"></a>可配置<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue16216751161712"><a name="zh-cn_topic_0000001352573769_parmvalue16216751161712"></a><a name="zh-cn_topic_0000001352573769_parmvalue16216751161712"></a>“WaitForFirstConsumer”</span>或<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue128755213217"><a name="zh-cn_topic_0000001352573769_parmvalue128755213217"></a><a name="zh-cn_topic_0000001352573769_parmvalue128755213217"></a>“Immediate”</span></p>
    <p id="zh-cn_topic_0000001352573769_p1021416541812"><a name="zh-cn_topic_0000001352573769_p1021416541812"></a><a name="zh-cn_topic_0000001352573769_p1021416541812"></a><span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue18708754151711"><a name="zh-cn_topic_0000001352573769_parmvalue18708754151711"></a><a name="zh-cn_topic_0000001352573769_parmvalue18708754151711"></a>“WaitForFirstConsumer”</span>：表示延迟PersistentVolume的绑定和调配，直到创建使用PVC的Pod。</p>
    <p id="zh-cn_topic_0000001352573769_p204525554212"><a name="zh-cn_topic_0000001352573769_p204525554212"></a><a name="zh-cn_topic_0000001352573769_p204525554212"></a><span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue12363342216"><a name="zh-cn_topic_0000001352573769_parmvalue12363342216"></a><a name="zh-cn_topic_0000001352573769_parmvalue12363342216"></a>“Immediate”</span>：表示创建PVC后，立即发生PersistentVolume绑定和调配。</p>
    </td>
    </tr>
    <tr id="zh-cn_topic_0000001352573769_row78451447983"><td class="cellrowborder" rowspan="2" valign="top" width="21.04210421042104%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001352573769_p821410541784"><a name="zh-cn_topic_0000001352573769_p821410541784"></a><a name="zh-cn_topic_0000001352573769_p821410541784"></a><strong id="zh-cn_topic_0000001352573769_b1421417545816"><a name="zh-cn_topic_0000001352573769_b1421417545816"></a><a name="zh-cn_topic_0000001352573769_b1421417545816"></a>allowedTopologies.matchLabelExpressions</strong></p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="24.752475247524753%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001352573769_p52141154281"><a name="zh-cn_topic_0000001352573769_p52141154281"></a><a name="zh-cn_topic_0000001352573769_p52141154281"></a>拓扑信息标签，用于过滤CSI后端和Kubernetes节点。如果匹配失败，会导致PVC或Pod无法创建。</p>
    <p id="zh-cn_topic_0000001352573769_p142147540815"><a name="zh-cn_topic_0000001352573769_p142147540815"></a><a name="zh-cn_topic_0000001352573769_p142147540815"></a>配置时需要同时按照固定格式配置<span class="parmname" id="zh-cn_topic_0000001352573769_parmname6787043181318"><a name="zh-cn_topic_0000001352573769_parmname6787043181318"></a><a name="zh-cn_topic_0000001352573769_parmname6787043181318"></a>“key”</span>和<span class="parmname" id="zh-cn_topic_0000001352573769_parmname4528250171314"><a name="zh-cn_topic_0000001352573769_parmname4528250171314"></a><a name="zh-cn_topic_0000001352573769_parmname4528250171314"></a>“value”</span>.</p>
    </td>
    <td class="cellrowborder" valign="top" width="54.205420542054206%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001352573769_p182141254384"><a name="zh-cn_topic_0000001352573769_p182141254384"></a><a name="zh-cn_topic_0000001352573769_p182141254384"></a><span class="parmname" id="zh-cn_topic_0000001352573769_parmname765115614133"><a name="zh-cn_topic_0000001352573769_parmname765115614133"></a><a name="zh-cn_topic_0000001352573769_parmname765115614133"></a>“key”</span>：可支持配置<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue62862891416"><a name="zh-cn_topic_0000001352573769_parmvalue62862891416"></a><a name="zh-cn_topic_0000001352573769_parmvalue62862891416"></a>“topology.kubernetes.io/zone”</span>，<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue23850201141"><a name="zh-cn_topic_0000001352573769_parmvalue23850201141"></a><a name="zh-cn_topic_0000001352573769_parmvalue23850201141"></a>“topology.kubernetes.io/region”</span>，</p>
    <p id="zh-cn_topic_0000001352573769_p321410548819"><a name="zh-cn_topic_0000001352573769_p321410548819"></a><a name="zh-cn_topic_0000001352573769_p321410548819"></a>topology.kubernetes.io/protocol.<em id="zh-cn_topic_0000001352573769_i9501249175712"><a name="zh-cn_topic_0000001352573769_i9501249175712"></a><a name="zh-cn_topic_0000001352573769_i9501249175712"></a>&lt;protocol&gt;</em>， 其中<em id="zh-cn_topic_0000001352573769_i4683111395712"><a name="zh-cn_topic_0000001352573769_i4683111395712"></a><a name="zh-cn_topic_0000001352573769_i4683111395712"></a>&lt;protocol&gt;</em>为协议类型， 例如：iscsi, fc, nfs等。</p>
    </td>
    </tr>
    <tr id="zh-cn_topic_0000001352573769_row85481628121017"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001352573769_p1209324123216"><a name="zh-cn_topic_0000001352573769_p1209324123216"></a><a name="zh-cn_topic_0000001352573769_p1209324123216"></a><span class="parmname" id="zh-cn_topic_0000001352573769_parmname152098242326"><a name="zh-cn_topic_0000001352573769_parmname152098242326"></a><a name="zh-cn_topic_0000001352573769_parmname152098242326"></a>“value”</span>：</p>
    <p id="zh-cn_topic_0000001352573769_p1024122115329"><a name="zh-cn_topic_0000001352573769_p1024122115329"></a><a name="zh-cn_topic_0000001352573769_p1024122115329"></a><span class="parmname" id="zh-cn_topic_0000001352573769_parmname10241152116324"><a name="zh-cn_topic_0000001352573769_parmname10241152116324"></a><a name="zh-cn_topic_0000001352573769_parmname10241152116324"></a>“key”</span>如果是<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue6241721103216"><a name="zh-cn_topic_0000001352573769_parmvalue6241721103216"></a><a name="zh-cn_topic_0000001352573769_parmvalue6241721103216"></a>“topology.kubernetes.io/zone”</span>，<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue224172120321"><a name="zh-cn_topic_0000001352573769_parmvalue224172120321"></a><a name="zh-cn_topic_0000001352573769_parmvalue224172120321"></a>“topology.kubernetes.io/region”</span>，<span class="parmname" id="zh-cn_topic_0000001352573769_parmname20241182153212"><a name="zh-cn_topic_0000001352573769_parmname20241182153212"></a><a name="zh-cn_topic_0000001352573769_parmname20241182153212"></a>“value”</span>值需要和<a href="/css-docs/docs/advanced-features/configuring-storage-topology-awareness#zh-cn_topic_0000001200451233_section12171124814413">前提条件中设置的拓扑标签</a>保持一致。</p>
    <p id="zh-cn_topic_0000001352573769_p195481328151018"><a name="zh-cn_topic_0000001352573769_p195481328151018"></a><a name="zh-cn_topic_0000001352573769_p195481328151018"></a><span class="parmname" id="zh-cn_topic_0000001352573769_parmname376144514158"><a name="zh-cn_topic_0000001352573769_parmname376144514158"></a><a name="zh-cn_topic_0000001352573769_parmname376144514158"></a>“key”</span>如果是topology.kubernetes.io/protocol.<em id="zh-cn_topic_0000001352573769_i1114976185818"><a name="zh-cn_topic_0000001352573769_i1114976185818"></a><a name="zh-cn_topic_0000001352573769_i1114976185818"></a>&lt;protocol&gt;</em>， <span class="parmname" id="zh-cn_topic_0000001352573769_parmname1982313019164"><a name="zh-cn_topic_0000001352573769_parmname1982313019164"></a><a name="zh-cn_topic_0000001352573769_parmname1982313019164"></a>“value”</span>值固定为<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue1591701620167"><a name="zh-cn_topic_0000001352573769_parmvalue1591701620167"></a><a name="zh-cn_topic_0000001352573769_parmvalue1591701620167"></a>“csi.huawei.com”</span></p>
    </td>
    </tr>
    </tbody>
    </table>

8.  执行以下命令，基于该yaml文件创建StorageClass。

    ```
    kubectl create -f StorgeClass.yaml
    ```

9.  使用该StorageClass创建具有拓扑能力的PVC，详细操作请参考[动态卷供应PVC参数说明](/docs/using-huawei-csi/managing-a-pvc/creating-a-pvc/dynamic-volume-provisioning/pvc-parameters-for-dynamic-volume-provisioning)。

