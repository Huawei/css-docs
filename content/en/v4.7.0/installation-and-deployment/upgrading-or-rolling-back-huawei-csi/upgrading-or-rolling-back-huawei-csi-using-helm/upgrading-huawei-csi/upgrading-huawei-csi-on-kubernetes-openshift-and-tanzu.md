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

7.  Run the  **vi update-values.yaml**  command to open the file obtained in  [6](#li1037712113474), modify the  **images**  configuration items, and update the image to the latest version. For details about the parameters to be modified, see  [Table 1](#table1554616217465).

    **Table  1**  images configuration items

    <a name="table1554616217465"></a>
    <table><thead align="left"><tr id="row5547102174612"><th class="cellrowborder" valign="top" width="24.242424242424242%" id="mcps1.2.5.1.1"><p id="en-us_topic_0214996140_p166064474810"><a name="en-us_topic_0214996140_p166064474810"></a><a name="en-us_topic_0214996140_p166064474810"></a>Container Name</p>
    </th>
    <th class="cellrowborder" valign="top" width="28.282828282828287%" id="mcps1.2.5.1.2"><p id="p1340513569100"><a name="p1340513569100"></a><a name="p1340513569100"></a>Description</p>
    </th>
    <th class="cellrowborder" valign="top" width="22.222222222222225%" id="mcps1.2.5.1.3"><p id="p917411101195"><a name="p917411101195"></a><a name="p917411101195"></a>K8s Version Requirements</p>
    </th>
    <th class="cellrowborder" valign="top" width="25.252525252525253%" id="mcps1.2.5.1.4"><p id="en-us_topic_0214996140_p26601644124817"><a name="en-us_topic_0214996140_p26601644124817"></a><a name="en-us_topic_0214996140_p26601644124817"></a>New Value</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row193537226910"><td class="cellrowborder" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="p101561535494"><a name="p101561535494"></a><a name="p101561535494"></a>storage-backend-controller</p>
    </td>
    <td class="cellrowborder" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p14405356131013"><a name="p14405356131013"></a><a name="p14405356131013"></a>huawei-csi image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p1015617351799"><a name="p1015617351799"></a><a name="p1015617351799"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="p0156183516920"><a name="p0156183516920"></a><a name="p0156183516920"></a>storage-backend-controller:<span id="ph131571335991"><a name="ph131571335991"></a><a name="ph131571335991"></a>4.7.0</span></p>
    </td>
    </tr>
    <tr id="row137401924896"><td class="cellrowborder" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="p81571358910"><a name="p81571358910"></a><a name="p81571358910"></a>storage-backend-sidecar</p>
    </td>
    <td class="cellrowborder" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p74055565107"><a name="p74055565107"></a><a name="p74055565107"></a>Image used by Huawei backends to manage storageBackendContent resources.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p18157173510920"><a name="p18157173510920"></a><a name="p18157173510920"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="p415783518912"><a name="p415783518912"></a><a name="p415783518912"></a>storage-backend-sidecar:<span id="ph61574352914"><a name="ph61574352914"></a><a name="ph61574352914"></a>4.7.0</span></p>
    </td>
    </tr>
    <tr id="row11864142612910"><td class="cellrowborder" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="p615719351098"><a name="p615719351098"></a><a name="p615719351098"></a>huawei-csi-driver</p>
    </td>
    <td class="cellrowborder" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p740515611016"><a name="p740515611016"></a><a name="p740515611016"></a>Image used by Huawei backends to manage storageBackendClaim resources.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p11157435196"><a name="p11157435196"></a><a name="p11157435196"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="p1015714351890"><a name="p1015714351890"></a><a name="p1015714351890"></a>huawei-csi:<span id="ph14157935896"><a name="ph14157935896"></a><a name="ph14157935896"></a>4.7.0</span></p>
    </td>
    </tr>
    <tr id="row1035818295911"><td class="cellrowborder" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="p5157935795"><a name="p5157935795"></a><a name="p5157935795"></a>huawei-csi-extender</p>
    </td>
    <td class="cellrowborder" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p1040555619107"><a name="p1040555619107"></a><a name="p1040555619107"></a>huawei-csi-extender image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p415710351892"><a name="p415710351892"></a><a name="p415710351892"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="p51571935491"><a name="p51571935491"></a><a name="p51571935491"></a>huawei-csi-extender:<span id="ph1515716351795"><a name="ph1515716351795"></a><a name="ph1515716351795"></a>4.7.0</span></p>
    </td>
    </tr>
    <tr id="row9547192114619"><td class="cellrowborder" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0214996140_p86601044154812"><a name="en-us_topic_0214996140_p86601044154812"></a><a name="en-us_topic_0214996140_p86601044154812"></a>images.sidecar.livenessProbe</p>
    </td>
    <td class="cellrowborder" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p22105111109"><a name="p22105111109"></a><a name="p22105111109"></a><a href="https://kubernetes-csi.github.io/docs/livenessprobe.html" target="_blank" rel="noopener noreferrer">livenessprobe</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p1517410101399"><a name="p1517410101399"></a><a name="p1517410101399"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0214996140_p166034494817"><a name="en-us_topic_0214996140_p166034494817"></a><a name="en-us_topic_0214996140_p166034494817"></a><span id="text1328521101017"><a name="text1328521101017"></a><a name="text1328521101017"></a>registry.k8s.io/sig-storage/livenessprobe:v2.12.0</span></p>
    </td>
    </tr>
    <tr id="row3136101118366"><td class="cellrowborder" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0214996140_p11661204454815"><a name="en-us_topic_0214996140_p11661204454815"></a><a name="en-us_topic_0214996140_p11661204454815"></a>images.sidecar.resizer</p>
    </td>
    <td class="cellrowborder" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p82155161016"><a name="p82155161016"></a><a name="p82155161016"></a><a href="https://kubernetes-csi.github.io/docs/external-resizer.html" target="_blank" rel="noopener noreferrer">csi-resizer</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p017491015911"><a name="p017491015911"></a><a name="p017491015911"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0214996140_p18661134413484"><a name="en-us_topic_0214996140_p18661134413484"></a><a name="en-us_topic_0214996140_p18661134413484"></a><span id="text3532628181013"><a name="text3532628181013"></a><a name="text3532628181013"></a>registry.k8s.io/sig-storage/csi-resizer:v1.9.0</span></p>
    </td>
    </tr>
    <tr id="row020073517369"><td class="cellrowborder" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0214996140_p866114415480"><a name="en-us_topic_0214996140_p866114415480"></a><a name="en-us_topic_0214996140_p866114415480"></a>images.sidecar.registrar</p>
    </td>
    <td class="cellrowborder" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p721051121011"><a name="p721051121011"></a><a name="p721051121011"></a><a href="https://kubernetes-csi.github.io/docs/node-driver-registrar.html" target="_blank" rel="noopener noreferrer">csi-node-driver-registrar</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p1417416101295"><a name="p1417416101295"></a><a name="p1417416101295"></a>v1.16+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="en-us_topic_0214996140_p1866215446487"><a name="en-us_topic_0214996140_p1866215446487"></a><a name="en-us_topic_0214996140_p1866215446487"></a><span id="text16984124141019"><a name="text16984124141019"></a><a name="text16984124141019"></a>registry.k8s.io/sig-storage/csi-node-driver-registrar:v2.9.0</span></p>
    </td>
    </tr>
    <tr id="row324775233618"><td class="cellrowborder" rowspan="2" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0214996140_p766184474818"><a name="en-us_topic_0214996140_p766184474818"></a><a name="en-us_topic_0214996140_p766184474818"></a>images.sidecar.snapshotter</p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p116916597115"><a name="p116916597115"></a><a name="p116916597115"></a><a href="https://kubernetes-csi.github.io/docs/external-snapshotter.html" target="_blank" rel="noopener noreferrer">csi-snapshotter</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p01741110595"><a name="p01741110595"></a><a name="p01741110595"></a>v1.20+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="p18449610144812"><a name="p18449610144812"></a><a name="p18449610144812"></a><span id="text11716195016102"><a name="text11716195016102"></a><a name="text11716195016102"></a>registry.k8s.io/sig-storage/csi-snapshotter:v6.3.0</span></p>
    </td>
    </tr>
    <tr id="row1854381033716"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p141741410499"><a name="p141741410499"></a><a name="p141741410499"></a>v1.17-v1.19</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p202545710478"><a name="p202545710478"></a><a name="p202545710478"></a>registry.k8s.io/sig-storage/csi-snapshotter:v4.2.1</p>
    </td>
    </tr>
    <tr id="row7643145710372"><td class="cellrowborder" rowspan="2" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0214996140_p12661144444812"><a name="en-us_topic_0214996140_p12661144444812"></a><a name="en-us_topic_0214996140_p12661144444812"></a>images.sidecar.snapshotController</p>
    <p id="p82014388380"><a name="p82014388380"></a><a name="p82014388380"></a></p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p698812417123"><a name="p698812417123"></a><a name="p698812417123"></a><a href="https://kubernetes-csi.github.io/docs/snapshot-controller.html" target="_blank" rel="noopener noreferrer">snapshot-controller</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p41741010492"><a name="p41741010492"></a><a name="p41741010492"></a>v1.20+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="p12512182574812"><a name="p12512182574812"></a><a name="p12512182574812"></a><span id="text255013593103"><a name="text255013593103"></a><a name="text255013593103"></a>registry.k8s.io/sig-storage/snapshot-controller:v6.3.0</span></p>
    </td>
    </tr>
    <tr id="row192011038193813"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p31741108918"><a name="p31741108918"></a><a name="p31741108918"></a>v1.17-v1.19</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1196613398484"><a name="p1196613398484"></a><a name="p1196613398484"></a>registry.k8s.io/sig-storage/snapshot-controller:v4.2.1</p>
    </td>
    </tr>
    <tr id="row175917813402"><td class="cellrowborder" rowspan="3" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="p97594894014"><a name="p97594894014"></a><a name="p97594894014"></a>images.sidecar.provisioner</p>
    <p id="p18457125104116"><a name="p18457125104116"></a><a name="p18457125104116"></a></p>
    </td>
    <td class="cellrowborder" rowspan="3" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p111331238191113"><a name="p111331238191113"></a><a name="p111331238191113"></a><a href="https://kubernetes-csi.github.io/docs/external-provisioner.html" target="_blank" rel="noopener noreferrer">csi-provisioner</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p7174101012917"><a name="p7174101012917"></a><a name="p7174101012917"></a>v1.20+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="p127598810403"><a name="p127598810403"></a><a name="p127598810403"></a><span id="text173371111171115"><a name="text173371111171115"></a><a name="text173371111171115"></a>registry.k8s.io/sig-storage/csi-provisioner:v3.6.0</span></p>
    </td>
    </tr>
    <tr id="row13547021134610"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p151745101197"><a name="p151745101197"></a><a name="p151745101197"></a>v1.17-v1.19</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="en-us_topic_0214996140_p866017444487"><a name="en-us_topic_0214996140_p866017444487"></a><a name="en-us_topic_0214996140_p866017444487"></a>registry.k8s.io/sig-storage/csi-provisioner:v3.0.0</p>
    </td>
    </tr>
    <tr id="row1745712516419"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p71742101912"><a name="p71742101912"></a><a name="p71742101912"></a>v1.16.x</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p845762517411"><a name="p845762517411"></a><a name="p845762517411"></a>quay.io/k8scsi/csi-provisioner:v1.4.0</p>
    </td>
    </tr>
    <tr id="row13547122114466"><td class="cellrowborder" rowspan="2" valign="top" width="24.242424242424242%" headers="mcps1.2.5.1.1 "><p id="en-us_topic_0214996140_p76611044114813"><a name="en-us_topic_0214996140_p76611044114813"></a><a name="en-us_topic_0214996140_p76611044114813"></a>images.sidecar.attacher</p>
    <p id="p19287224398"><a name="p19287224398"></a><a name="p19287224398"></a></p>
    </td>
    <td class="cellrowborder" rowspan="2" valign="top" width="28.282828282828287%" headers="mcps1.2.5.1.2 "><p id="p127791244101110"><a name="p127791244101110"></a><a name="p127791244101110"></a><a href="https://kubernetes-csi.github.io/docs/external-attacher.html" target="_blank" rel="noopener noreferrer">csi-attacher</a> sidecar image.</p>
    </td>
    <td class="cellrowborder" valign="top" width="22.222222222222225%" headers="mcps1.2.5.1.3 "><p id="p617410101295"><a name="p617410101295"></a><a name="p617410101295"></a>v1.17+</p>
    </td>
    <td class="cellrowborder" valign="top" width="25.252525252525253%" headers="mcps1.2.5.1.4 "><p id="p10146135017914"><a name="p10146135017914"></a><a name="p10146135017914"></a><span id="text10459171819114"><a name="text10459171819114"></a><a name="text10459171819114"></a>registry.k8s.io/sig-storage/csi-attacher:v4.4.0</span></p>
    </td>
    </tr>
    <tr id="row32879215395"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p817413101195"><a name="p817413101195"></a><a name="p817413101195"></a>v.1.16.x</p>
    </td>
    <td class="cellrowborder" valign="top" headers="mcps1.2.5.1.2 "><p id="p1328711216396"><a name="p1328711216396"></a><a name="p1328711216396"></a>quay.io/k8scsi/csi-attacher:v1.2.1</p>
    </td>
    </tr>
    </tbody>
    </table>

8.  \(Optional\) If you need to update configuration items or add configuration information during the upgrade, modify the configuration information in the  **update-values.yaml**  file by referring to  [Parameters in the values.yaml File of Helm](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/parameters-in-the-values-yaml-file-of-helm).

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
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

