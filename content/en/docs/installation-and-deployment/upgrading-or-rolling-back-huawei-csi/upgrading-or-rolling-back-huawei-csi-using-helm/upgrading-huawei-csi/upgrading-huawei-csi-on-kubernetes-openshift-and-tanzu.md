---
title: "Upgrading Huawei CSI on Kubernetes, OpenShift, and Tanzu"
linkTitle: "Upgrading Huawei CSI on Kubernetes, OpenShift, and Tanzu"
description: 
weight: 2
---

## Prerequisites{#section12493103133711}

-   Huawei CSI of an earlier version is installed using Helm.
-   A Huawei CSI image of a new version has been created and uploaded to the image repository or imported to all nodes by following the instructions provided in  [Uploading a Huawei CSI Image](/docs/installation-and-deployment/installation-preparations/uploading-a-huawei-csi-image).

## Upgrading Huawei CSI{#section6841317173013}

If CSI of an earlier version is deployed using Helm, perform the following steps to upgrade Huawei CSI.

1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
2.  Copy the CSI component package of the target version to any directory on the master node.
3.  Go to the  **helm/esdk**  working directory. For the directory path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).

    ```
    cd helm/esdk
    ```

4.  Run the  **kubectl apply -f** _./crds/backend/_  command to update the storage backend CRD.

    ```
    kubectl apply -f ./crds/backend/
    ```

5.  \(Optional\) Check snapshot-dependent components by following the instructions provided in  [Checking Volume Snapshot-Dependent Components](/docs/installation-and-deployment/installation-preparations/checking-volume-snapshot-dependent-components). After confirming that the components are correct, run the  **kubectl apply -f**  ._/crds/snapshot-crds/_ **--validate=false**  command to update the snapshot CRD. If  **controller.snapshot.enabled**  is set to  **false**  or the Kubernetes version is earlier than v1.17, you can skip this step. For details, see  [Table 2](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm#table813124411459).

    ```
    kubectl apply -f ./crds/snapshot-crds/ --validate=false
    ```

6.  <a name="li1037712113474"></a>Run the following command to obtain the original service configuration file.  **helm-huawei-csi**  indicates the Helm chart name specified during the installation of the earlier version, and  **huawei-csi**  indicates the Helm chart namespace specified during the installation of the earlier version.

    ```
    helm get values helm-huawei-csi -n huawei-csi -a > ./update-values.yaml
    ```

7.  Run the  **vi update-values.yaml**  command to open the file obtained in  [6](#li1037712113474), modify the  **images**  configuration items, and update the image to the latest version. For details about the parameters to be modified, see  [Table 1](#table8452547161918).

    **Table  1**  images configuration items

    <a name="table8452547161918"></a>
    <table><thead align="left"><tr id="row645218479197"><th class="cellrowborder" valign="top" width="26.697330266973307%" id="mcps1.2.4.1.1"><p id="p5269141514410"><a name="p5269141514410"></a><a name="p5269141514410"></a>Parameter</p>
    </th>
    <th class="cellrowborder" valign="top" width="30.736926307369266%" id="mcps1.2.4.1.2"><p id="p026931524418"><a name="p026931524418"></a><a name="p026931524418"></a>Description</p>
    </th>
    <th class="cellrowborder" valign="top" width="42.56574342565744%" id="mcps1.2.4.1.3"><p id="p826915156447"><a name="p826915156447"></a><a name="p826915156447"></a>New Value</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row1156694303912"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001324610777_p15337145719458"><a name="en-us_topic_0000001324610777_p15337145719458"></a><a name="en-us_topic_0000001324610777_p15337145719458"></a>images.huaweiCSIService</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001324610777_p173371357144517"><a name="en-us_topic_0000001324610777_p173371357144517"></a><a name="en-us_topic_0000001324610777_p173371357144517"></a>huawei-csi image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001324610777_p1633715710454"><a name="en-us_topic_0000001324610777_p1633715710454"></a><a name="en-us_topic_0000001324610777_p1633715710454"></a>huawei-csi:<span id="ph09001410174913"><a name="ph09001410174913"></a><a name="ph09001410174913"></a>4.5.0</span></p>
    </td>
    </tr>
    <tr id="row12803747173911"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="p1616415034013"><a name="p1616415034013"></a><a name="p1616415034013"></a>images.storageBackendSidecar</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="p1080311470395"><a name="p1080311470395"></a><a name="p1080311470395"></a>Image used by Huawei backends to manage storageBackendContent resources.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="p1380304783914"><a name="p1380304783914"></a><a name="p1380304783914"></a>storage-backend-sidecar:<span id="ph875612200538"><a name="ph875612200538"></a><a name="ph875612200538"></a>4.5.0</span></p>
    </td>
    </tr>
    <tr id="row1089864973918"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="p46581916408"><a name="p46581916408"></a><a name="p46581916408"></a>images.storageBackendController</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="p6899124910393"><a name="p6899124910393"></a><a name="p6899124910393"></a>Image used by Huawei backends to manage storageBackendClaim resources.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="p2089912497394"><a name="p2089912497394"></a><a name="p2089912497394"></a>storage-backend-controller:<span id="ph132856223538"><a name="ph132856223538"></a><a name="ph132856223538"></a>4.5.0</span></p>
    </td>
    </tr>
    <tr id="row13497161917392"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="p134971419183913"><a name="p134971419183913"></a><a name="p134971419183913"></a>images.huaweiCSIExtender</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="p3498151914398"><a name="p3498151914398"></a><a name="p3498151914398"></a>huawei-csi-extender image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="p34988198393"><a name="p34988198393"></a><a name="p34988198393"></a>huawei-csi-extender:<span id="ph17708152310538"><a name="ph17708152310538"></a><a name="ph17708152310538"></a>4.5.0</span></p>
    </td>
    </tr>
    <tr id="row185030354414"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001324610777_p4337185713453"><a name="en-us_topic_0000001324610777_p4337185713453"></a><a name="en-us_topic_0000001324610777_p4337185713453"></a>images.sidecar.livenessProbe</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001324610777_p9337195764510"><a name="en-us_topic_0000001324610777_p9337195764510"></a><a name="en-us_topic_0000001324610777_p9337195764510"></a><a href="https://kubernetes-csi.github.io/docs/livenessprobe.html" target="_blank" rel="noopener noreferrer">livenessprobe</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001324610777_p1633725724512"><a name="en-us_topic_0000001324610777_p1633725724512"></a><a name="en-us_topic_0000001324610777_p1633725724512"></a>k8s.gcr.io/sig-storage/livenessprobe:v2.5.0</p>
    </td>
    </tr>
    <tr id="row345374716195"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001324610777_p333755715453"><a name="en-us_topic_0000001324610777_p333755715453"></a><a name="en-us_topic_0000001324610777_p333755715453"></a>images.sidecar.provisioner</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001324610777_p183372575454"><a name="en-us_topic_0000001324610777_p183372575454"></a><a name="en-us_topic_0000001324610777_p183372575454"></a><a href="https://kubernetes-csi.github.io/docs/external-provisioner.html" target="_blank" rel="noopener noreferrer">csi-provisioner</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001324610777_p1033711577456"><a name="en-us_topic_0000001324610777_p1033711577456"></a><a name="en-us_topic_0000001324610777_p1033711577456"></a>k8s.gcr.io/sig-storage/csi-provisioner:v3.0.0</p>
    </td>
    </tr>
    <tr id="row145324715192"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001324610777_p19337155744517"><a name="en-us_topic_0000001324610777_p19337155744517"></a><a name="en-us_topic_0000001324610777_p19337155744517"></a>images.sidecar.attacher</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001324610777_p18337145744510"><a name="en-us_topic_0000001324610777_p18337145744510"></a><a name="en-us_topic_0000001324610777_p18337145744510"></a><a href="https://kubernetes-csi.github.io/docs/external-attacher.html" target="_blank" rel="noopener noreferrer">csi-attacher</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001324610777_p18337155714518"><a name="en-us_topic_0000001324610777_p18337155714518"></a><a name="en-us_topic_0000001324610777_p18337155714518"></a>k8s.gcr.io/sig-storage/csi-attacher:v3.4.0</p>
    </td>
    </tr>
    <tr id="row94532047111915"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001324610777_p13337175711459"><a name="en-us_topic_0000001324610777_p13337175711459"></a><a name="en-us_topic_0000001324610777_p13337175711459"></a>images.sidecar.resizer</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001324610777_p53377576452"><a name="en-us_topic_0000001324610777_p53377576452"></a><a name="en-us_topic_0000001324610777_p53377576452"></a><a href="https://kubernetes-csi.github.io/docs/external-resizer.html" target="_blank" rel="noopener noreferrer">csi-resizer</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001324610777_p93375572452"><a name="en-us_topic_0000001324610777_p93375572452"></a><a name="en-us_topic_0000001324610777_p93375572452"></a>k8s.gcr.io/sig-storage/csi-resizer:v1.4.0</p>
    </td>
    </tr>
    <tr id="row9453124771918"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001324610777_p833785764516"><a name="en-us_topic_0000001324610777_p833785764516"></a><a name="en-us_topic_0000001324610777_p833785764516"></a>images.sidecar.snapshotter</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001324610777_p73371257134514"><a name="en-us_topic_0000001324610777_p73371257134514"></a><a name="en-us_topic_0000001324610777_p73371257134514"></a><a href="https://kubernetes-csi.github.io/docs/external-snapshotter.html" target="_blank" rel="noopener noreferrer">csi-snapshotter</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001324610777_p1833765712454"><a name="en-us_topic_0000001324610777_p1833765712454"></a><a name="en-us_topic_0000001324610777_p1833765712454"></a>k8s.gcr.io/sig-storage/csi-snapshotter:v4.2.1</p>
    </td>
    </tr>
    <tr id="row196140122014"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001324610777_p10337557174514"><a name="en-us_topic_0000001324610777_p10337557174514"></a><a name="en-us_topic_0000001324610777_p10337557174514"></a>images.sidecar.snapshotController</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001324610777_p163372057164518"><a name="en-us_topic_0000001324610777_p163372057164518"></a><a name="en-us_topic_0000001324610777_p163372057164518"></a><a href="https://kubernetes-csi.github.io/docs/snapshot-controller.html" target="_blank" rel="noopener noreferrer">snapshot-controller</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001324610777_p10337457134511"><a name="en-us_topic_0000001324610777_p10337457134511"></a><a name="en-us_topic_0000001324610777_p10337457134511"></a>k8s.gcr.io/sig-storage/snapshot-controller:v4.2.1</p>
    </td>
    </tr>
    <tr id="row84580467201"><td class="cellrowborder" valign="top" width="26.697330266973307%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0000001324610777_p10337165714454"><a name="en-us_topic_0000001324610777_p10337165714454"></a><a name="en-us_topic_0000001324610777_p10337165714454"></a>images.sidecar.registrar</p>
    </td>
    <td class="cellrowborder" valign="top" width="30.736926307369266%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0000001324610777_p153371957164512"><a name="en-us_topic_0000001324610777_p153371957164512"></a><a name="en-us_topic_0000001324610777_p153371957164512"></a><a href="https://kubernetes-csi.github.io/docs/node-driver-registrar.html" target="_blank" rel="noopener noreferrer">csi-node-driver-registrar</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="42.56574342565744%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0000001324610777_p83371057164510"><a name="en-us_topic_0000001324610777_p83371057164510"></a><a name="en-us_topic_0000001324610777_p83371057164510"></a>k8s.gcr.io/sig-storage/csi-node-driver-registrar:v2.3.0</p>
    </td>
    </tr>
    </tbody>
    </table>

8.  \(Optional\) If you need to update configuration items or add configuration information during the upgrade, modify the configuration information in the  **update-values.yaml**  file by referring to  [Parameters in the values.yaml File of Helm](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm).

    >![](/public_sys-resources/en/icon-note.gif)
    >During the upgrade, if the  **update-values.yaml**  and  **values.yaml**  configuration files contain the same configuration item, the configuration in the  **update-values.yaml**  file takes effect preferentially.

9.  Run the following command to upgrade Huawei CSI. In the following command,  **helm-huawei-csi**  indicates the specified Helm chart name,  **huawei-csi**  indicates the specified Helm chart namespace, and  **update-values.yaml**  indicates the file obtained in  [6](#li1037712113474).

    ```
    helm upgrade helm-huawei-csi ./ -n huawei-csi -f ./values.yaml -f ./update-values.yaml
    ```

10. After the huawei-csi service is deployed, run the following command to check whether the service is started.

    ```
    kubectl get pod -n huawei-csi
    ```

    The following is an example of the command output. If the Pod status is  **Running**, the service is started successfully.

    ```
    NAME                                     READY   STATUS    RESTARTS   AGE
    huawei-csi-controller-6dfcc4b79f-9vjtq   9/9     Running   0          24m
    huawei-csi-controller-6dfcc4b79f-csphc   9/9     Running   0          24m
    huawei-csi-node-g6f4k                    3/3     Running   0          20m
    huawei-csi-node-tqs87                    3/3     Running   0          20m
    ```

