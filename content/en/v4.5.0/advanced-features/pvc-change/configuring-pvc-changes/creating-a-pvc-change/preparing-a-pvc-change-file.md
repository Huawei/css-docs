---
title: "Preparing a PVC Change File"
linkTitle: "Preparing a PVC Change File"
description: 
weight: 1
---

## PVC Change File Description{#section45675517546}

The sample template of the PVC change file is  **/examples/volumemodifyclaim.yaml**. The following table lists the configuration items.

**Table  1**  Parameter description

<a name="table882408155517"></a>
<table><thead align="left"><tr id="row1882418105518"><th class="cellrowborder" valign="top" width="16%" id="mcps1.2.6.1.1"><p id="p282412815559"><a name="p282412815559"></a><a name="p282412815559"></a>Parameter</p>
</th>
<th class="cellrowborder" valign="top" width="23%" id="mcps1.2.6.1.2"><p id="p1682410825515"><a name="p1682410825515"></a><a name="p1682410825515"></a>Description</p>
</th>
<th class="cellrowborder" valign="top" width="16%" id="mcps1.2.6.1.3"><p id="p17824188185518"><a name="p17824188185518"></a><a name="p17824188185518"></a>Mandatory</p>
</th>
<th class="cellrowborder" valign="top" width="17%" id="mcps1.2.6.1.4"><p id="p16824148195513"><a name="p16824148195513"></a><a name="p16824148195513"></a>Default Value</p>
</th>
<th class="cellrowborder" valign="top" width="28.000000000000004%" id="mcps1.2.6.1.5"><p id="p98241783553"><a name="p98241783553"></a><a name="p98241783553"></a>Remarks</p>
</th>
</tr>
</thead>
<tbody><tr id="row282438175514"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p38247819556"><a name="p38247819556"></a><a name="p38247819556"></a>apiVersion</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.6.1.2 "><p id="en-us_topic_0000001541071762_p0896194484915"><a name="en-us_topic_0000001541071762_p0896194484915"></a><a name="en-us_topic_0000001541071762_p0896194484915"></a>API group, which is of the string type.</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.3 "><p id="p8824178125515"><a name="p8824178125515"></a><a name="p8824178125515"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.6.1.4 "><p id="p138247865515"><a name="p138247865515"></a><a name="p138247865515"></a>xuanwu.huawei.io/v1</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p982408115517"><a name="p982408115517"></a><a name="p982408115517"></a>The value is fixed at <strong id="b4705121514462"><a name="b4705121514462"></a><a name="b4705121514462"></a>xuanwu.huawei.io/v1</strong>.</p>
</td>
</tr>
<tr id="row158241788556"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p1382416825518"><a name="p1382416825518"></a><a name="p1382416825518"></a>kind</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.6.1.2 "><p id="p782438195513"><a name="p782438195513"></a><a name="p782438195513"></a>Resource type, which is of the string type.</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.3 "><p id="p88244814556"><a name="p88244814556"></a><a name="p88244814556"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.6.1.4 "><p id="p1782413819554"><a name="p1782413819554"></a><a name="p1782413819554"></a>VolumeModifyClaim</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p12824198115512"><a name="p12824198115512"></a><a name="p12824198115512"></a>The value is fixed at <strong id="b17554182420471"><a name="b17554182420471"></a><a name="b17554182420471"></a>VolumeModifyClaim</strong>.</p>
</td>
</tr>
<tr id="row7824198185511"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p1182488115510"><a name="p1182488115510"></a><a name="p1182488115510"></a>metadata.name</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.6.1.2 "><p id="p188241387558"><a name="p188241387558"></a><a name="p188241387558"></a>Name of a cluster resource object, which is of the string type.</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.3 "><p id="p5824684559"><a name="p5824684559"></a><a name="p5824684559"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.6.1.4 "><p id="p1782413895514"><a name="p1782413895514"></a><a name="p1782413895514"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1482417805520"><a name="p1482417805520"></a><a name="p1482417805520"></a>The name must comply with the naming rules of a <a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#dns-subdomain-names" target="_blank" rel="noopener noreferrer">DNS subdomain name</a>. The value can contain a maximum of 63 characters, including digits, lowercase letters, hyphens (-), and periods (.). It must start and end with a lowercase letter or digit.</p>
</td>
</tr>
<tr id="row1482498135514"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p18241589552"><a name="p18241589552"></a><a name="p18241589552"></a>spec.source.kind</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.6.1.2 "><p id="p13824158195519"><a name="p13824158195519"></a><a name="p13824158195519"></a>Data source type, which is of the string type.</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.3 "><p id="p1082428125517"><a name="p1082428125517"></a><a name="p1082428125517"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.6.1.4 "><p id="p982420825510"><a name="p982420825510"></a><a name="p982420825510"></a>StorageClass</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p138240835517"><a name="p138240835517"></a><a name="p138240835517"></a>This parameter can only be set to <strong id="b435383819547"><a name="b435383819547"></a><a name="b435383819547"></a>StorageClass</strong>.</p>
</td>
</tr>
<tr id="row1580118248311"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p48021124438"><a name="p48021124438"></a><a name="p48021124438"></a>spec.source.name</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.6.1.2 "><p id="p68021524930"><a name="p68021524930"></a><a name="p68021524930"></a>Data source name, which is of the string type.</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.3 "><p id="p480210241835"><a name="p480210241835"></a><a name="p480210241835"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.6.1.4 "><p id="p980213243314"><a name="p980213243314"></a><a name="p980213243314"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1380282420314"><a name="p1380282420314"></a><a name="p1380282420314"></a>Only a StorageClass name can be configured.</p>
</td>
</tr>
<tr id="row19555112614317"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p0555826131"><a name="p0555826131"></a><a name="p0555826131"></a>spec.parameters.hyperMetro</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.6.1.2 "><p id="p145556261430"><a name="p145556261430"></a><a name="p145556261430"></a>Whether to change a common volume to a HyperMetro volume. Currently, the value can only be <strong id="b8301192215559"><a name="b8301192215559"></a><a name="b8301192215559"></a>"true"</strong>.</p>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.3 "><p id="p205555261534"><a name="p205555261534"></a><a name="p205555261534"></a>Yes</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.6.1.4 "><p id="p1555926531"><a name="p1555926531"></a><a name="p1555926531"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p465413911106"><a name="p465413911106"></a><a name="p465413911106"></a>Only common storage volumes at the primary site can be changed to HyperMetro storage volumes.</p>
</td>
</tr>
<tr id="row141343508506"><td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.1 "><p id="p13134125010508"><a name="p13134125010508"></a><a name="p13134125010508"></a>spec.parameters.metroPairSyncSpeed</p>
</td>
<td class="cellrowborder" valign="top" width="23%" headers="mcps1.2.6.1.2 "><p id="p11242177125214"><a name="p11242177125214"></a><a name="p11242177125214"></a>Data synchronization speed of a HyperMetro pair. The value ranges from 1 to 4.</p>
<p id="p1924214720529"><a name="p1924214720529"></a><a name="p1924214720529"></a>The value can be:</p>
<a name="ul4215172125219"></a><a name="ul4215172125219"></a><ul id="ul4215172125219"><li><strong id="b1497122032817"><a name="b1497122032817"></a><a name="b1497122032817"></a>1</strong>: low</li><li><strong id="b1655321192810"><a name="b1655321192810"></a><a name="b1655321192810"></a>2</strong>: medium</li><li><strong id="b109641321152814"><a name="b109641321152814"></a><a name="b109641321152814"></a>3</strong>: high</li><li><strong id="b1081622222816"><a name="b1081622222816"></a><a name="b1081622222816"></a>4</strong>: highest</li></ul>
</td>
<td class="cellrowborder" valign="top" width="16%" headers="mcps1.2.6.1.3 "><p id="p1413415016505"><a name="p1413415016505"></a><a name="p1413415016505"></a>No</p>
</td>
<td class="cellrowborder" valign="top" width="17%" headers="mcps1.2.6.1.4 "><p id="p113425015509"><a name="p113425015509"></a><a name="p113425015509"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.6.1.5 "><p id="p1813405016505"><a name="p1813405016505"></a><a name="p1813405016505"></a>This parameter is available only when <strong id="b1250143842810"><a name="b1250143842810"></a><a name="b1250143842810"></a>spec.parameters.hyperMetro</strong> is set to <strong id="b383674313287"><a name="b383674313287"></a><a name="b383674313287"></a>"true"</strong>.</p>
<p id="p688744685818"><a name="p688744685818"></a><a name="p688744685818"></a>Note:</p>
<a name="ul35821048175812"></a><a name="ul35821048175812"></a><ul id="ul35821048175812"><li>If this parameter is not configured, the storage speed of the HyperMetro pair is determined by the storage device.</li><li>The highest synchronization speed may increase the host latency.</li></ul>
</td>
</tr>
</tbody>
</table>

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   The  **spec.source.kind**  and  **spec.source.name**  parameters are used to specify the volume change scope. For example, if they are set to a StorageClass and the corresponding name respectively, all PVCs in the  **Bound**  state provisioned using the target StorageClass will be changed.
>-   After all associated PVCs are changed, Huawei CSI will replace the original StorageClass and add the  **spec.parameters**  parameter of the VolumeModifyClaim so that the PVCs meet the StorageClass definition.

For details about the configuration in typical scenarios, see the following example:

## Changing a Common Volume to a HyperMetro Volume{#section637055131612}

The following is an example of changing a common volume to a HyperMetro volume:

```yaml
apiVersion: xuanwu.huawei.io/v1
kind: VolumeModifyClaim
metadata:
  name: myvmc
spec:
  source:
    kind: StorageClass
    name: mysc
  parameters:
    hyperMetro: "true"
```

