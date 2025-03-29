---
title: "Kubernetes、OpenShift、Tanzu升级华为CSI"
linkTitle: "Kubernetes、OpenShift、Tanzu升级华为CSI"
description: 
weight: 2
---

## 前提条件{#section12493103133711}

-   旧版本华为CSI使用Helm安装。
-   新版本华为CSI镜像已制作完成，并且按照[上传华为CSI镜像](/docs/installation-and-deployment/installation-preparations/uploading-a-huawei-csi-image)章节说明，上传到镜像仓库或者导入到所有节点。

## 升级华为CSI{#section6841317173013}

如果您旧版本CSI使用Helm部署，请按照以下操作步骤升级华为CSI。

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  将目标版本CSI组件包拷贝到master节点的任意目录下。
3.  进入到helm/esdk的工作目录下，目录路径请参见[表1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。

    ```
    cd helm/esdk
    ```

4.  执行**kubectl apply -f**  ./crds/backend/命令，更新存储后端CRD

    ```
    kubectl apply -f ./crds/backend/
    ```

5.  **（可选）**  请务必按照[检查卷快照依赖组件](/docs/installation-and-deployment/installation-preparations/checking-volume-snapshot-dependent-components)章节检查快照依赖组件，确认无误后执行执行**kubectl apply -f**  ./crds/snapshot-crds/  **--validate=false**命令更新快照CRD，如果controller.snapshot.enabled参数设置为false或Kubernetes版本低于v1.17，可跳过本步骤，详情请参考[表2](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table813124411459)。

    ```
    kubectl apply -f ./crds/snapshot-crds/ --validate=false
    ```

6.  <a name="li1037712113474"></a>执行以下命令，获取原有服务配置文件。其中helm-huawei-csi为旧版本安装时指定的Helm Chart名称，huawei-csi为旧版本安装时指定的Helm Chart命名空间。

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

7.  执行**vi update-values.yaml**命令打开[6](#li1037712113474)中获取的文件，修改images配置项，更新镜像至最新版本。需要修改的参数请参考[表1](#table1554616217465)。

    **表 1**  images配置项

    <a name="table1554616217465"></a>
    <table><thead align="left"><tr id="row5547102174612"><th class="cellrowborder" valign="top" width="27.597240275972407%" id="mcps1.2.5.1.1"><p id="zh-cn_topic_0214996140_p166064474810"><a name="zh-cn_topic_0214996140_p166064474810"></a><a name="zh-cn_topic_0214996140_p166064474810"></a>容器名称</p>
    </th>
    <th class="cellrowborder" valign="top" width="24.80751924807519%" id="mcps1.2.5.1.2"><p id="p1340513569100"><a name="p1340513569100"></a><a name="p1340513569100"></a>描述</p>
    </th>
    <th class="cellrowborder" valign="top" width="13.668633136686331%" id="mcps1.2.5.1.3"><p id="p917411101195"><a name="p917411101195"></a><a name="p917411101195"></a>K8s版本要求</p>
    </th>
    <th class="cellrowborder" valign="top" width="33.92660733926608%" id="mcps1.2.5.1.4"><p id="zh-cn_topic_0214996140_p26601644124817"><a name="zh-cn_topic_0214996140_p26601644124817"></a><a name="zh-cn_topic_0214996140_p26601644124817"></a>修改为</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row193537226910"><td class="cellrowborder" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="p101561535494"><a name="p101561535494"></a><a name="p101561535494"></a>storage-backend-controller</p>
    </td>
    <td class="cellrowborder" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p14405356131013"><a name="p14405356131013"></a><a name="p14405356131013"></a>huawei-csi镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p1015617351799"><a name="p1015617351799"></a><a name="p1015617351799"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="p0156183516920"><a name="p0156183516920"></a><a name="p0156183516920"></a>storage-backend-controller:<span id="ph131571335991"><a name="ph131571335991"></a><a name="ph131571335991"></a>4.6.0</span></p>
    </td>
    </tr>
    <tr id="row137401924896"><td class="cellrowborder" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="p81571358910"><a name="p81571358910"></a><a name="p81571358910"></a>storage-backend-sidecar</p>
    </td>
    <td class="cellrowborder" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p74055565107"><a name="p74055565107"></a><a name="p74055565107"></a>华为后端管理storageBackendContent资源的镜像</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p18157173510920"><a name="p18157173510920"></a><a name="p18157173510920"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="p415783518912"><a name="p415783518912"></a><a name="p415783518912"></a>storage-backend-sidecar:<span id="ph61574352914"><a name="ph61574352914"></a><a name="ph61574352914"></a>4.6.0</span></p>
    </td>
    </tr>
    <tr id="row11864142612910"><td class="cellrowborder" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="p615719351098"><a name="p615719351098"></a><a name="p615719351098"></a>huawei-csi-driver</p>
    </td>
    <td class="cellrowborder" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p740515611016"><a name="p740515611016"></a><a name="p740515611016"></a>华为后端管理storageBackendClaim资源的镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p11157435196"><a name="p11157435196"></a><a name="p11157435196"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="p1015714351890"><a name="p1015714351890"></a><a name="p1015714351890"></a>huawei-csi:<span id="ph14157935896"><a name="ph14157935896"></a><a name="ph14157935896"></a>4.6.0</span></p>
    </td>
    </tr>
    <tr id="row1035818295911"><td class="cellrowborder" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="p5157935795"><a name="p5157935795"></a><a name="p5157935795"></a>huawei-csi-extender</p>
    </td>
    <td class="cellrowborder" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p1040555619107"><a name="p1040555619107"></a><a name="p1040555619107"></a>huawei-csi-extender镜像</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p415710351892"><a name="p415710351892"></a><a name="p415710351892"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="p51571935491"><a name="p51571935491"></a><a name="p51571935491"></a>huawei-csi-extender:<span id="ph1515716351795"><a name="ph1515716351795"></a><a name="ph1515716351795"></a>4.6.0</span></p>
    </td>
    </tr>
    <tr id="row9547192114619"><td class="cellrowborder" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p86601044154812"><a name="zh-cn_topic_0214996140_p86601044154812"></a><a name="zh-cn_topic_0214996140_p86601044154812"></a>images.sidecar.livenessProbe</p>
    </td>
    <td class="cellrowborder" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p22105111109"><a name="p22105111109"></a><a name="p22105111109"></a><a href="https://kubernetes-csi.github.io/docs/livenessprobe.html" target="_blank" rel="noopener noreferrer">livenessprobe</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p1517410101399"><a name="p1517410101399"></a><a name="p1517410101399"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p166034494817"><a name="zh-cn_topic_0214996140_p166034494817"></a><a name="zh-cn_topic_0214996140_p166034494817"></a>registry.k8s.io/sig-storage/livenessprobe:v2.12.0</p>
    </td>
    </tr>
    <tr id="row3136101118366"><td class="cellrowborder" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p11661204454815"><a name="zh-cn_topic_0214996140_p11661204454815"></a><a name="zh-cn_topic_0214996140_p11661204454815"></a>images.sidecar.resizer</p>
    </td>
    <td class="cellrowborder" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p82155161016"><a name="p82155161016"></a><a name="p82155161016"></a><a href="https://kubernetes-csi.github.io/docs/external-resizer.html" target="_blank" rel="noopener noreferrer">csi-resizer</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p017491015911"><a name="p017491015911"></a><a name="p017491015911"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p18661134413484"><a name="zh-cn_topic_0214996140_p18661134413484"></a><a name="zh-cn_topic_0214996140_p18661134413484"></a>registry.k8s.io/sig-storage/csi-resizer:v1.9.0</p>
    </td>
    </tr>
    <tr id="row020073517369"><td class="cellrowborder" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p866114415480"><a name="zh-cn_topic_0214996140_p866114415480"></a><a name="zh-cn_topic_0214996140_p866114415480"></a>images.sidecar.registrar</p>
    </td>
    <td class="cellrowborder" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p721051121011"><a name="p721051121011"></a><a name="p721051121011"></a><a href="https://kubernetes-csi.github.io/docs/node-driver-registrar.html" target="_blank" rel="noopener noreferrer">csi-node-driver-registrar</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p1417416101295"><a name="p1417416101295"></a><a name="p1417416101295"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="zh-cn_topic_0214996140_p1866215446487"><a name="zh-cn_topic_0214996140_p1866215446487"></a><a name="zh-cn_topic_0214996140_p1866215446487"></a>registry.k8s.io/sig-storage/csi-node-driver-registrar:v2.9.0</p>
    </td>
    </tr>
    <tr id="row324775233618"><td class="cellrowborder" rowspan="2" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p766184474818"><a name="zh-cn_topic_0214996140_p766184474818"></a><a name="zh-cn_topic_0214996140_p766184474818"></a>images.sidecar.snapshotter</p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p116916597115"><a name="p116916597115"></a><a name="p116916597115"></a><a href="https://kubernetes-csi.github.io/docs/external-snapshotter.html" target="_blank" rel="noopener noreferrer">csi-snapshotter</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p01741110595"><a name="p01741110595"></a><a name="p01741110595"></a>v1.20+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="p18449610144812"><a name="p18449610144812"></a><a name="p18449610144812"></a>registry.k8s.io/sig-storage/csi-snapshotter:v6.3.0</p>
    </td>
    </tr>
    <tr id="row1854381033716"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p141741410499"><a name="p141741410499"></a><a name="p141741410499"></a>v1.17-v1.19</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p202545710478"><a name="p202545710478"></a><a name="p202545710478"></a>registry.k8s.io/sig-storage/csi-snapshotter:v4.2.1</p>
    </td>
    </tr>
    <tr id="row7643145710372"><td class="cellrowborder" rowspan="2" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p12661144444812"><a name="zh-cn_topic_0214996140_p12661144444812"></a><a name="zh-cn_topic_0214996140_p12661144444812"></a>images.sidecar.snapshotController</p>
    <p id="p82014388380"><a name="p82014388380"></a><a name="p82014388380"></a></p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p698812417123"><a name="p698812417123"></a><a name="p698812417123"></a><a href="https://kubernetes-csi.github.io/docs/snapshot-controller.html" target="_blank" rel="noopener noreferrer">snapshot-controller</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p41741010492"><a name="p41741010492"></a><a name="p41741010492"></a>v1.20+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="p12512182574812"><a name="p12512182574812"></a><a name="p12512182574812"></a>registry.k8s.io/sig-storage/snapshot-controller:v6.3.0</p>
    </td>
    </tr>
    <tr id="row192011038193813"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p31741108918"><a name="p31741108918"></a><a name="p31741108918"></a>v1.17-v1.19</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1196613398484"><a name="p1196613398484"></a><a name="p1196613398484"></a>registry.k8s.io/sig-storage/snapshot-controller:v4.2.1</p>
    </td>
    </tr>
    <tr id="row175917813402"><td class="cellrowborder" rowspan="3" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="p97594894014"><a name="p97594894014"></a><a name="p97594894014"></a>images.sidecar.provisioner</p>
    <p id="p18457125104116"><a name="p18457125104116"></a><a name="p18457125104116"></a></p>
    </td>
    <td class="cellrowborder" rowspan="3" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p111331238191113"><a name="p111331238191113"></a><a name="p111331238191113"></a><a href="https://kubernetes-csi.github.io/docs/external-provisioner.html" target="_blank" rel="noopener noreferrer">csi-provisioner</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p7174101012917"><a name="p7174101012917"></a><a name="p7174101012917"></a>v1.20+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="p127598810403"><a name="p127598810403"></a><a name="p127598810403"></a>registry.k8s.io/sig-storage/csi-provisioner:v3.6.0</p>
    </td>
    </tr>
    <tr id="row13547021134610"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p151745101197"><a name="p151745101197"></a><a name="p151745101197"></a>v1.17-v1.19</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="zh-cn_topic_0214996140_p866017444487"><a name="zh-cn_topic_0214996140_p866017444487"></a><a name="zh-cn_topic_0214996140_p866017444487"></a>registry.k8s.io/sig-storage/csi-provisioner:v3.0.0</p>
    </td>
    </tr>
    <tr id="row1745712516419"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p71742101912"><a name="p71742101912"></a><a name="p71742101912"></a>v1.16.x</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p845762517411"><a name="p845762517411"></a><a name="p845762517411"></a>quay.io/k8scsi/csi-provisioner:v1.4.0</p>
    </td>
    </tr>
    <tr id="row13547122114466"><td class="cellrowborder" rowspan="2" valign="top" width="27.597240275972407%" headers="mcps1.2.5.1.1 "><p id="zh-cn_topic_0214996140_p76611044114813"><a name="zh-cn_topic_0214996140_p76611044114813"></a><a name="zh-cn_topic_0214996140_p76611044114813"></a>images.sidecar.attacher</p>
    <p id="p19287224398"><a name="p19287224398"></a><a name="p19287224398"></a></p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="24.80751924807519%" headers="mcps1.2.5.1.2 "><p id="p127791244101110"><a name="p127791244101110"></a><a name="p127791244101110"></a><a href="https://kubernetes-csi.github.io/docs/external-attacher.html" target="_blank" rel="noopener noreferrer">csi-attacher</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="13.668633136686331%" headers="mcps1.2.5.1.3 "><p id="p617410101295"><a name="p617410101295"></a><a name="p617410101295"></a>v1.17+</p>
    </td>
    <td class="cellrowborder" valign="top" width="33.92660733926608%" headers="mcps1.2.5.1.4 "><p id="p10146135017914"><a name="p10146135017914"></a><a name="p10146135017914"></a>registry.k8s.io/sig-storage/csi-attacher:v4.4.0</p>
    </td>
    </tr>
    <tr id="row32879215395"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p817413101195"><a name="p817413101195"></a><a name="p817413101195"></a>v.1.16.x</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1328711216396"><a name="p1328711216396"></a><a name="p1328711216396"></a>quay.io/k8scsi/csi-attacher:v1.2.1</p>
    </td>
    </tr>
    </tbody>
    </table>

8.  （可选）在升级过程中如需自定义更新配置项信息或者需要新增配置信息，可参考[Helm values.yaml参数说明](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm)修改update-values.yaml文件中配置信息。

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >升级时，如果update-values.yaml与values.yaml配置文件中存在相同配置项，update-values.yaml中的配置将会优先生效。

9.  执行以下命令，升级华为CSI。其中helm-huawei-csi为指定的Helm Chart名称，huawei-csi为指定的Helm Chart命名空间，update-values.yaml为步骤[6](#li1037712113474)中获取的文件。

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi -f ./values.yaml -f ./update-values.yaml
    ```

10. 完成huawei-csi服务部署后，执行命令检查服务是否启动。

    ```
    kubectl get pod -n huawei-csi
    ```

    命令结果示例如下，Pod状态为“Running“表明服务启动成功。

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   9/9     Running   0          24m
    huawei-csi-controller-6dfcc4b79f-csphc   9/9     Running   0          24m
    huawei-csi-node-g6f4k                    3/3     Running   0          20m
    huawei-csi-node-tqs87                    3/3     Running   0          20m
    ```

