---
title: "Kubernetes、OpenShift、Tanzu升级华为CSI"
linkTitle: "Kubernetes、OpenShift、Tanzu升级华为CSI"
description: 
weight: 2
---

## 前提条件{#section12493103133711}

-   旧版本华为CSI使用Helm安装。
-   新版本华为CSI镜像已制作完成，并且按照[上传华为CSI镜像](/v4.5.0/installation-and-deployment/installation-preparations/uploading-a-huawei-csi-image)章节说明，上传到镜像仓库或者导入到所有节点。

## 升级华为CSI{#section6841317173013}

如果您旧版本CSI使用Helm部署，请按照以下操作步骤升级华为CSI。

1.  使用远程访问工具（以PuTTY为例），通过管理IP地址，登录Kubernetes集群的任意master节点。
2.  将目标版本CSI组件包拷贝到master节点的任意目录下。
3.  进入到helm/esdk的工作目录下，目录路径请参见[表1](/v4.5.0/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#zh-cn_topic_0150885197_table17200162435412)。

    ```
    cd helm/esdk
    ```

4.  执行**kubectl apply -f**  ./crds/backend/命令，更新存储后端CRD

    ```
    kubectl apply -f ./crds/backend/
    ```

5.  **（可选）**  请务必按照[检查卷快照依赖组件](/v4.5.0/installation-and-deployment/installation-preparations/checking-volume-snapshot-dependent-components)章节检查快照依赖组件，确认无误后执行执行**kubectl apply -f**  ./crds/snapshot-crds/  **--validate=false**命令更新快照CRD，如果controller.snapshot.enabled参数设置为false或Kubernetes版本低于v1.17，可跳过本步骤，详情请参考[表2](/v4.5.0/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table813124411459)。

    ```
    kubectl apply -f ./crds/snapshot-crds/ --validate=false
    ```

6.  <a name="li1037712113474"></a>执行以下命令，获取原有服务配置文件。其中helm-huawei-csi为旧版本安装时指定的Helm Chart名称，huawei-csi为旧版本安装时指定的Helm Chart命名空间。

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

7.  执行**vi update-values.yaml**命令打开[6](#li1037712113474)中获取的文件，修改images配置项，更新镜像至最新版本。需要修改的参数请参考[表1](#table8452547161918)。

    **表 1**  images配置项

    <a name="table8452547161918"></a>
    <table><thead align="left"><tr id="row645218479197"><th class="cellrowborder" valign="top" width="26.697330266973307%" id="mcps1.2.4.1.1"><p id="p5269141514410"><a name="p5269141514410"></a><a name="p5269141514410"></a>参数</p>
    </th>
    <th class="cellrowborder" valign="top" width="30.736926307369266%" id="mcps1.2.4.1.2"><p id="p026931524418"><a name="p026931524418"></a><a name="p026931524418"></a>描述</p>
    </th>
    <th class="cellrowborder" valign="top" width="42.56574342565744%" id="mcps1.2.4.1.3"><p id="p826915156447"><a name="p826915156447"></a><a name="p826915156447"></a>修改为</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row1156694303912"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001324610777_p15337145719458"><a name="zh-cn_topic_0000001324610777_p15337145719458"></a><a name="zh-cn_topic_0000001324610777_p15337145719458"></a>images.huaweiCSIService</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001324610777_p173371357144517"><a name="zh-cn_topic_0000001324610777_p173371357144517"></a><a name="zh-cn_topic_0000001324610777_p173371357144517"></a>huawei-csi镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001324610777_p1633715710454"><a name="zh-cn_topic_0000001324610777_p1633715710454"></a><a name="zh-cn_topic_0000001324610777_p1633715710454"></a>huawei-csi:<span id="ph09001410174913"><a name="ph09001410174913"></a><a name="ph09001410174913"></a>4.5.0</span></p>
    </td>
    </tr>
    <tr id="row12803747173911"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="p1616415034013"><a name="p1616415034013"></a><a name="p1616415034013"></a>images.storageBackendSidecar</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="p1080311470395"><a name="p1080311470395"></a><a name="p1080311470395"></a>华为后端管理storageBackendContent资源的镜像</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="p1380304783914"><a name="p1380304783914"></a><a name="p1380304783914"></a>storage-backend-sidecar:<span id="ph875612200538"><a name="ph875612200538"></a><a name="ph875612200538"></a>4.5.0</span></p>
    </td>
    </tr>
    <tr id="row1089864973918"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="p46581916408"><a name="p46581916408"></a><a name="p46581916408"></a>images.storageBackendController</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="p6899124910393"><a name="p6899124910393"></a><a name="p6899124910393"></a>华为后端管理storageBackendClaim资源的镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="p2089912497394"><a name="p2089912497394"></a><a name="p2089912497394"></a>storage-backend-controller:<span id="ph132856223538"><a name="ph132856223538"></a><a name="ph132856223538"></a>4.5.0</span></p>
    </td>
    </tr>
    <tr id="row13497161917392"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="p134971419183913"><a name="p134971419183913"></a><a name="p134971419183913"></a>images.huaweiCSIExtender</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="p3498151914398"><a name="p3498151914398"></a><a name="p3498151914398"></a>huawei-csi-extender镜像</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="p34988198393"><a name="p34988198393"></a><a name="p34988198393"></a>huawei-csi-extender:<span id="ph17708152310538"><a name="ph17708152310538"></a><a name="ph17708152310538"></a>4.5.0</span></p>
    </td>
    </tr>
    <tr id="row185030354414"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001324610777_p4337185713453"><a name="zh-cn_topic_0000001324610777_p4337185713453"></a><a name="zh-cn_topic_0000001324610777_p4337185713453"></a>images.sidecar.livenessProbe</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001324610777_p9337195764510"><a name="zh-cn_topic_0000001324610777_p9337195764510"></a><a name="zh-cn_topic_0000001324610777_p9337195764510"></a><a href="https://kubernetes-csi.github.io/docs/livenessprobe.html" target="_blank" rel="noopener noreferrer">livenessprobe</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001324610777_p1633725724512"><a name="zh-cn_topic_0000001324610777_p1633725724512"></a><a name="zh-cn_topic_0000001324610777_p1633725724512"></a>k8s.gcr.io/sig-storage/livenessprobe:v2.5.0</p>
    </td>
    </tr>
    <tr id="row345374716195"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001324610777_p333755715453"><a name="zh-cn_topic_0000001324610777_p333755715453"></a><a name="zh-cn_topic_0000001324610777_p333755715453"></a>images.sidecar.provisioner</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001324610777_p183372575454"><a name="zh-cn_topic_0000001324610777_p183372575454"></a><a name="zh-cn_topic_0000001324610777_p183372575454"></a><a href="https://kubernetes-csi.github.io/docs/external-provisioner.html" target="_blank" rel="noopener noreferrer">csi-provisioner</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001324610777_p1033711577456"><a name="zh-cn_topic_0000001324610777_p1033711577456"></a><a name="zh-cn_topic_0000001324610777_p1033711577456"></a>k8s.gcr.io/sig-storage/csi-provisioner:v3.0.0</p>
    </td>
    </tr>
    <tr id="row145324715192"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001324610777_p19337155744517"><a name="zh-cn_topic_0000001324610777_p19337155744517"></a><a name="zh-cn_topic_0000001324610777_p19337155744517"></a>images.sidecar.attacher</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001324610777_p18337145744510"><a name="zh-cn_topic_0000001324610777_p18337145744510"></a><a name="zh-cn_topic_0000001324610777_p18337145744510"></a><a href="https://kubernetes-csi.github.io/docs/external-attacher.html" target="_blank" rel="noopener noreferrer">csi-attacher</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001324610777_p18337155714518"><a name="zh-cn_topic_0000001324610777_p18337155714518"></a><a name="zh-cn_topic_0000001324610777_p18337155714518"></a>k8s.gcr.io/sig-storage/csi-attacher:v3.4.0</p>
    </td>
    </tr>
    <tr id="row94532047111915"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001324610777_p13337175711459"><a name="zh-cn_topic_0000001324610777_p13337175711459"></a><a name="zh-cn_topic_0000001324610777_p13337175711459"></a>images.sidecar.resizer</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001324610777_p53377576452"><a name="zh-cn_topic_0000001324610777_p53377576452"></a><a name="zh-cn_topic_0000001324610777_p53377576452"></a><a href="https://kubernetes-csi.github.io/docs/external-resizer.html" target="_blank" rel="noopener noreferrer">csi-resizer</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001324610777_p93375572452"><a name="zh-cn_topic_0000001324610777_p93375572452"></a><a name="zh-cn_topic_0000001324610777_p93375572452"></a>k8s.gcr.io/sig-storage/csi-resizer:v1.4.0</p>
    </td>
    </tr>
    <tr id="row9453124771918"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001324610777_p833785764516"><a name="zh-cn_topic_0000001324610777_p833785764516"></a><a name="zh-cn_topic_0000001324610777_p833785764516"></a>images.sidecar.snapshotter</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001324610777_p73371257134514"><a name="zh-cn_topic_0000001324610777_p73371257134514"></a><a name="zh-cn_topic_0000001324610777_p73371257134514"></a><a href="https://kubernetes-csi.github.io/docs/external-snapshotter.html" target="_blank" rel="noopener noreferrer">csi-snapshotter</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001324610777_p1833765712454"><a name="zh-cn_topic_0000001324610777_p1833765712454"></a><a name="zh-cn_topic_0000001324610777_p1833765712454"></a>k8s.gcr.io/sig-storage/csi-snapshotter:v4.2.1</p>
    </td>
    </tr>
    <tr id="row196140122014"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001324610777_p10337557174514"><a name="zh-cn_topic_0000001324610777_p10337557174514"></a><a name="zh-cn_topic_0000001324610777_p10337557174514"></a>images.sidecar.snapshotController</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001324610777_p163372057164518"><a name="zh-cn_topic_0000001324610777_p163372057164518"></a><a name="zh-cn_topic_0000001324610777_p163372057164518"></a><a href="https://kubernetes-csi.github.io/docs/snapshot-controller.html" target="_blank" rel="noopener noreferrer">snapshot-controller</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001324610777_p10337457134511"><a name="zh-cn_topic_0000001324610777_p10337457134511"></a><a name="zh-cn_topic_0000001324610777_p10337457134511"></a>k8s.gcr.io/sig-storage/snapshot-controller:v4.2.1</p>
    </td>
    </tr>
    <tr id="row84580467201"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="zh-cn_topic_0000001324610777_p10337165714454"><a name="zh-cn_topic_0000001324610777_p10337165714454"></a><a name="zh-cn_topic_0000001324610777_p10337165714454"></a>images.sidecar.registrar</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="zh-cn_topic_0000001324610777_p153371957164512"><a name="zh-cn_topic_0000001324610777_p153371957164512"></a><a name="zh-cn_topic_0000001324610777_p153371957164512"></a><a href="https://kubernetes-csi.github.io/docs/node-driver-registrar.html" target="_blank" rel="noopener noreferrer">csi-node-driver-registrar</a> sidecar镜像。</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="zh-cn_topic_0000001324610777_p83371057164510"><a name="zh-cn_topic_0000001324610777_p83371057164510"></a><a name="zh-cn_topic_0000001324610777_p83371057164510"></a>k8s.gcr.io/sig-storage/csi-node-driver-registrar:v2.3.0</p>
    </td>
    </tr>
    </tbody>
    </table>

8.  （可选）在升级过程中如需自定义更新配置项信息或者需要新增配置信息，可参考[Helm values.yaml参数说明](/v4.5.0/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm)修改update-values.yaml文件中配置信息。

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

