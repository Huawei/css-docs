---
title: "配置存储拓扑感知"
linkTitle: "配置存储拓扑感知"
description: 
weight: 2
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

    **表 1**  参数说明

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


