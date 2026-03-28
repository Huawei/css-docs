---
title: "配置存储拓扑感知"
linkTitle: "配置存储拓扑感知"
description: 
weight: 9
---

在Kubernetes集群中，可以根据节点的拓扑标签以及存储后端支持的拓扑能力调度和发放资源。

## 前提条件{#zh-cn_topic_0000001200451233_section12171124814413}

需要在集群中的worker节点完成拓扑的标签配置，标签配置方法如下：

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  执行以下命令，查看当前集群中的worker节点信息。

    ```
    kubectl get node
    ```

    命令结果示例如下：

    ```
    NAME     STATUS   ROLES                      AGE   VERSION
    node01   Ready    controlplane,etcd,worker   42d   v1.22.3
    node02   Ready    worker                     42d   v1.22.3
    node03   Ready    worker                     42d   v1.22.3
    ```

3.  执行以下命令，给worker节点配置拓扑标签。其中_ nodename _为worker节点名称, key 和 value 参数说明请参考[表1](#zh-cn_topic_0000001200451233_table1261817418166)。

    ```
    kubectl label node <nodename> <key>=<value>
    ```

    **表 1**  拓扑标签参数说明

    <a name="zh-cn_topic_0000001200451233_table1261817418166"></a>
    <table><thead align="left"><tr id="zh-cn_topic_0000001200451233_row1361864114165"><th class="cellrowborder" valign="top" width="16.5016501650165%" id="mcps1.2.4.1.1"><p id="zh-cn_topic_0000001200451233_p0862145011168"><a name="zh-cn_topic_0000001200451233_p0862145011168"></a><a name="zh-cn_topic_0000001200451233_p0862145011168"></a>参数名</p>
    </th>
    <th class="cellrowborder" valign="top" width="30.673067306730672%" id="mcps1.2.4.1.2"><p id="zh-cn_topic_0000001200451233_p8862175081616"><a name="zh-cn_topic_0000001200451233_p8862175081616"></a><a name="zh-cn_topic_0000001200451233_p8862175081616"></a>参数描述</p>
    </th>
    <th class="cellrowborder" valign="top" width="52.82528252825283%" id="mcps1.2.4.1.3"><p id="zh-cn_topic_0000001200451233_p6862350191614"><a name="zh-cn_topic_0000001200451233_p6862350191614"></a><a name="zh-cn_topic_0000001200451233_p6862350191614"></a>备注</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="zh-cn_topic_0000001200451233_row1061815413161"><td class="cellrowborder" valign="top" width="16.5016501650165%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001200451233_p171281559121615"><a name="zh-cn_topic_0000001200451233_p171281559121615"></a><a name="zh-cn_topic_0000001200451233_p171281559121615"></a>&lt;key&gt;</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.673067306730672%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001200451233_p13618144119164"><a name="zh-cn_topic_0000001200451233_p13618144119164"></a><a name="zh-cn_topic_0000001200451233_p13618144119164"></a>拓扑标签的唯一标识。</p>
    </td>
    <td class="cellrowborder" valign="top" width="52.82528252825283%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001200451233_p993021810189"><a name="zh-cn_topic_0000001200451233_p993021810189"></a><a name="zh-cn_topic_0000001200451233_p993021810189"></a>可支持配置：zone，region，protocol.<em id="zh-cn_topic_0000001200451233_i460232951814"><a name="zh-cn_topic_0000001200451233_i460232951814"></a><a name="zh-cn_topic_0000001200451233_i460232951814"></a>&lt;protocol&gt;</em></p>
    <p id="zh-cn_topic_0000001200451233_p20771183412190"><a name="zh-cn_topic_0000001200451233_p20771183412190"></a><a name="zh-cn_topic_0000001200451233_p20771183412190"></a>其中<em id="zh-cn_topic_0000001200451233_i9771143416191"><a name="zh-cn_topic_0000001200451233_i9771143416191"></a><a name="zh-cn_topic_0000001200451233_i9771143416191"></a>&lt;protocol&gt;</em>可支持配置iscsi, nfs, fc, roce。</p>
    </td>
    </tr>
    <tr id="zh-cn_topic_0000001200451233_row3618164119162"><td class="cellrowborder" valign="top" width="16.5016501650165%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001200451233_p15618164181619"><a name="zh-cn_topic_0000001200451233_p15618164181619"></a><a name="zh-cn_topic_0000001200451233_p15618164181619"></a>&lt;value&gt;</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.673067306730672%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001200451233_p1961804121614"><a name="zh-cn_topic_0000001200451233_p1961804121614"></a><a name="zh-cn_topic_0000001200451233_p1961804121614"></a>拓扑标签的参数值。</p>
    </td>
    <td class="cellrowborder" valign="top" width="52.82528252825283%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001200451233_p89541533122011"><a name="zh-cn_topic_0000001200451233_p89541533122011"></a><a name="zh-cn_topic_0000001200451233_p89541533122011"></a><span class="parmname" id="zh-cn_topic_0000001200451233_parmname2954633172020"><a name="zh-cn_topic_0000001200451233_parmname2954633172020"></a><a name="zh-cn_topic_0000001200451233_parmname2954633172020"></a>“key”</span>如果是<span class="parmvalue" id="zh-cn_topic_0000001200451233_parmvalue11954123318209"><a name="zh-cn_topic_0000001200451233_parmvalue11954123318209"></a><a name="zh-cn_topic_0000001200451233_parmvalue11954123318209"></a>“zone”</span>，<span class="parmvalue" id="zh-cn_topic_0000001200451233_parmvalue2095415339208"><a name="zh-cn_topic_0000001200451233_parmvalue2095415339208"></a><a name="zh-cn_topic_0000001200451233_parmvalue2095415339208"></a>“region”</span>，<span class="parmname" id="zh-cn_topic_0000001200451233_parmname1954193352013"><a name="zh-cn_topic_0000001200451233_parmname1954193352013"></a><a name="zh-cn_topic_0000001200451233_parmname1954193352013"></a>“value”</span>值为自定义参数。</p>
    <p id="zh-cn_topic_0000001200451233_p44843300202"><a name="zh-cn_topic_0000001200451233_p44843300202"></a><a name="zh-cn_topic_0000001200451233_p44843300202"></a><span class="parmname" id="zh-cn_topic_0000001200451233_parmname2048443072017"><a name="zh-cn_topic_0000001200451233_parmname2048443072017"></a><a name="zh-cn_topic_0000001200451233_parmname2048443072017"></a>“key”</span>如果是protocol.<em id="zh-cn_topic_0000001200451233_i1815844555617"><a name="zh-cn_topic_0000001200451233_i1815844555617"></a><a name="zh-cn_topic_0000001200451233_i1815844555617"></a>&lt;protocol&gt;</em>， <span class="parmname" id="zh-cn_topic_0000001200451233_parmname19484143018201"><a name="zh-cn_topic_0000001200451233_parmname19484143018201"></a><a name="zh-cn_topic_0000001200451233_parmname19484143018201"></a>“value”</span>值固定为<span class="parmvalue" id="zh-cn_topic_0000001200451233_parmvalue5484133020209"><a name="zh-cn_topic_0000001200451233_parmvalue5484133020209"></a><a name="zh-cn_topic_0000001200451233_parmvalue5484133020209"></a>“csi.huawei.com”</span>。</p>
    </td>
    </tr>
    </tbody>
    </table>

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >-   拓扑标签必须以topology.kubernetes.io开头。拓扑标签示例：
    >    -   示例1：topology.kubernetes.io/region=China-west
    >    -   示例2：topology.kubernetes.io/zone=ChengDu
    >    -   示例3：topology.kubernetes.io/protocol.iscsi=csi.huawei.com
    >    -   示例4：topology.kubernetes.io/protocol.fc=csi.huawei.com
    >-   同一节点上拓扑标签中同一个key只能支持一个value值。
    >-   如果同一节点上拓扑标签中同时配置多个protocol，配置StorageClass时，StorageClass只需要满足其中一个protocol即可。
    >-   如果同一节点上拓扑标签中同时配置region和zone，配置StorageClass时，StorageClass需要满足全部筛选条件。

4.  执行命令， 查看当前集群中所有worker节点的标签信息。

    ```
    kubectl get nodes -o=jsonpath='{range .items[*]}[{.metadata.name}, {.metadata.labels}]{"\n"}{end}' | grep --color "topology.kubernetes.io"
    ```

    命令结果示例如下：

    ```
    [node01,"beta.kubernetes.io/arch":"amd64","beta.kubernetes.io/os":"linux","kubernetes.io/arch":"amd64","kubernetes.io/hostname":"node01","kubernetes.io/os":"linux","node-role.kubernetes.io/controlplane":"true","node-role.kubernetes.io/etcd":"true","node-role.kubernetes.io/worker":"true","topology.kubernetes.io/zone":"ChengDu"}]
    ```

## 操作步骤{#section2619114191417}

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  进入Helm工程的目录下，如果无法找到之前的Helm工程，则将组件包中的helm目录拷贝到master节点的任意目录下，组件包路径请参考[表1](/docs/installation-and-deployment/csi/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。
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

7.  执行** vi StorageClass.yaml**  命令，修改yaml文件。按  **I**  或  **Insert**  进入编辑状态，在yaml文件下增加相关参数，详细参数说明请参见[表2](#zh-cn_topic_0000001352573769_table118458471087)。修改完成后，按  **Esc**  并输入  **:wq!**  ，保存修改。

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

    **表 2**  StorageClass参数说明

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
    <p id="zh-cn_topic_0000001352573769_p142147540815"><a name="zh-cn_topic_0000001352573769_p142147540815"></a><a name="zh-cn_topic_0000001352573769_p142147540815"></a>配置时需要同时按照固定格式配置<span class="parmname" id="zh-cn_topic_0000001352573769_parmname6787043181318"><a name="zh-cn_topic_0000001352573769_parmname6787043181318"></a><a name="zh-cn_topic_0000001352573769_parmname6787043181318"></a>“key”</span>和<span class="parmname" id="zh-cn_topic_0000001352573769_parmname4528250171314"><a name="zh-cn_topic_0000001352573769_parmname4528250171314"></a><a name="zh-cn_topic_0000001352573769_parmname4528250171314"></a>“values”</span>.</p>
    </td>
    <td class="cellrowborder" valign="top" width="54.205420542054206%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001352573769_p182141254384"><a name="zh-cn_topic_0000001352573769_p182141254384"></a><a name="zh-cn_topic_0000001352573769_p182141254384"></a><span class="parmname" id="zh-cn_topic_0000001352573769_parmname765115614133"><a name="zh-cn_topic_0000001352573769_parmname765115614133"></a><a name="zh-cn_topic_0000001352573769_parmname765115614133"></a>“key”</span>：可支持配置<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue62862891416"><a name="zh-cn_topic_0000001352573769_parmvalue62862891416"></a><a name="zh-cn_topic_0000001352573769_parmvalue62862891416"></a>“topology.kubernetes.io/zone”</span>，<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue23850201141"><a name="zh-cn_topic_0000001352573769_parmvalue23850201141"></a><a name="zh-cn_topic_0000001352573769_parmvalue23850201141"></a>“topology.kubernetes.io/region”</span>，</p>
    <p id="zh-cn_topic_0000001352573769_p321410548819"><a name="zh-cn_topic_0000001352573769_p321410548819"></a><a name="zh-cn_topic_0000001352573769_p321410548819"></a>topology.kubernetes.io/protocol.<em id="zh-cn_topic_0000001352573769_i9501249175712"><a name="zh-cn_topic_0000001352573769_i9501249175712"></a><a name="zh-cn_topic_0000001352573769_i9501249175712"></a>&lt;protocol&gt;</em>， 其中<em id="zh-cn_topic_0000001352573769_i4683111395712"><a name="zh-cn_topic_0000001352573769_i4683111395712"></a><a name="zh-cn_topic_0000001352573769_i4683111395712"></a>&lt;protocol&gt;</em>为协议类型， 例如：iscsi, fc, nfs等。</p>
    </td>
    </tr>
    <tr id="zh-cn_topic_0000001352573769_row85481628121017"><td class="cellrowborder" valign="top" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001352573769_p1209324123216"><a name="zh-cn_topic_0000001352573769_p1209324123216"></a><a name="zh-cn_topic_0000001352573769_p1209324123216"></a><span class="parmname" id="zh-cn_topic_0000001352573769_parmname152098242326"><a name="zh-cn_topic_0000001352573769_parmname152098242326"></a><a name="zh-cn_topic_0000001352573769_parmname152098242326"></a>“values”</span>：</p>
    <p id="zh-cn_topic_0000001352573769_p1024122115329"><a name="zh-cn_topic_0000001352573769_p1024122115329"></a><a name="zh-cn_topic_0000001352573769_p1024122115329"></a><span class="parmname" id="zh-cn_topic_0000001352573769_parmname10241152116324"><a name="zh-cn_topic_0000001352573769_parmname10241152116324"></a><a name="zh-cn_topic_0000001352573769_parmname10241152116324"></a>“key”</span>如果是<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue6241721103216"><a name="zh-cn_topic_0000001352573769_parmvalue6241721103216"></a><a name="zh-cn_topic_0000001352573769_parmvalue6241721103216"></a>“topology.kubernetes.io/zone”</span>，<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue224172120321"><a name="zh-cn_topic_0000001352573769_parmvalue224172120321"></a><a name="zh-cn_topic_0000001352573769_parmvalue224172120321"></a>“topology.kubernetes.io/region”</span>，<span class="parmname" id="zh-cn_topic_0000001352573769_parmname20241182153212"><a name="zh-cn_topic_0000001352573769_parmname20241182153212"></a><a name="zh-cn_topic_0000001352573769_parmname20241182153212"></a>“values”</span>值需要和<a href="/css-docs/docs/common-o-m-operations/configuring-storage-topology-awareness#zh-cn_topic_0000001200451233_section12171124814413">前提条件中设置的拓扑标签</a>保持一致。</p>
    <p id="zh-cn_topic_0000001352573769_p195481328151018"><a name="zh-cn_topic_0000001352573769_p195481328151018"></a><a name="zh-cn_topic_0000001352573769_p195481328151018"></a><span class="parmname" id="zh-cn_topic_0000001352573769_parmname376144514158"><a name="zh-cn_topic_0000001352573769_parmname376144514158"></a><a name="zh-cn_topic_0000001352573769_parmname376144514158"></a>“key”</span>如果是topology.kubernetes.io/protocol.<em id="zh-cn_topic_0000001352573769_i1114976185818"><a name="zh-cn_topic_0000001352573769_i1114976185818"></a><a name="zh-cn_topic_0000001352573769_i1114976185818"></a>&lt;protocol&gt;</em>， <span class="parmname" id="zh-cn_topic_0000001352573769_parmname1982313019164"><a name="zh-cn_topic_0000001352573769_parmname1982313019164"></a><a name="zh-cn_topic_0000001352573769_parmname1982313019164"></a>“value”</span>值固定为<span class="parmvalue" id="zh-cn_topic_0000001352573769_parmvalue1591701620167"><a name="zh-cn_topic_0000001352573769_parmvalue1591701620167"></a><a name="zh-cn_topic_0000001352573769_parmvalue1591701620167"></a>“csi.huawei.com”</span></p>
    </td>
    </tr>
    </tbody>
    </table>

8.  执行以下命令，基于该yaml文件创建StorageClass。

    ```
    kubectl create -f StorgeClass.yaml
    ```

9.  使用该StorageClass创建具有拓扑能力的PVC，详细操作请参考[表1](/docs/basic-services/persistent-volume-management/configuring-pvs/configuring-dynamic-pvs#zh-cn_topic_0150885187_table195731435604)。

