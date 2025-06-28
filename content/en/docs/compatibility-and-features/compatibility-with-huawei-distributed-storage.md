---
title: "Compatibility with Huawei Distributed Storage"
linkTitle: "Compatibility with Huawei Distributed Storage"
description: 
weight: 4
---

Huawei CSI plug-in is compatible with Huawei OceanStor series distributed storage systems. The following table lists the supported storage versions.

## Supported Huawei Distributed Storage{#section723118313717}

**Table  1**  Supported Huawei distributed storage

<a name="table13501195552513"></a>
<table><thead align="left"><tr id="row17501175532518"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p5501555152518"><a name="p5501555152518"></a><a name="p5501555152518"></a>Storage Product</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p250185516255"><a name="p250185516255"></a><a name="p250185516255"></a>Version</p>
</th>
</tr>
</thead>
<tbody><tr id="row350255517254"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="en-us_topic_0150885201_p283231353315"><a name="en-us_topic_0150885201_p283231353315"></a><a name="en-us_topic_0150885201_p283231353315"></a>FusionStorage Block</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="en-us_topic_0150885201_p1283201313319"><a name="en-us_topic_0150885201_p1283201313319"></a><a name="en-us_topic_0150885201_p1283201313319"></a>8.0.1</p>
</td>
</tr>
<tr id="row16502155513258"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="en-us_topic_0150885201_p467542723319"><a name="en-us_topic_0150885201_p467542723319"></a><a name="en-us_topic_0150885201_p467542723319"></a>OceanStor Pacific series</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="en-us_topic_0150885201_p146755279338"><a name="en-us_topic_0150885201_p146755279338"></a><a name="en-us_topic_0150885201_p146755279338"></a>8.1.0, 8.1.1, 8.1.2, 8.1.3, 8.1.5, 8.2.0, 8.2.1</p>
</td>
</tr>
<tr id="row443523210491"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p11384959194610"><a name="p11384959194610"></a><a name="p11384959194610"></a>OceanDisk</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p16384759154614"><a name="p16384759154614"></a><a name="p16384759154614"></a>1.5.0</p>
</td>
</tr>
</tbody>
</table>

## Features Supported by Huawei Distributed Storage{#section14115311203711}

Huawei CSI plug-in supports the following features for Huawei distributed storage.

**Table  2**  Features supported by Huawei distributed storage and constraints

<a name="table175022559255"></a>
<table><thead align="left"><tr id="row250245510250"><th class="cellrowborder" valign="top" width="20%" id="mcps1.2.5.1.1"><p id="p10502355102510"><a name="p10502355102510"></a><a name="p10502355102510"></a>Feature</p>
</th>
<th class="cellrowborder" valign="top" width="28.000000000000004%" id="mcps1.2.5.1.2"><p id="p7502455182516"><a name="p7502455182516"></a><a name="p7502455182516"></a>FusionStorage Block</p>
</th>
<th class="cellrowborder" valign="top" width="27%" id="mcps1.2.5.1.3"><p id="p150255532517"><a name="p150255532517"></a><a name="p150255532517"></a>OceanStor Pacific Series</p>
</th>
<th class="cellrowborder" valign="top" width="25%" id="mcps1.2.5.1.4"><p id="p4721836124713"><a name="p4721836124713"></a><a name="p4721836124713"></a>OceanDisk</p>
</th>
</tr>
</thead>
<tbody><tr id="row45029556254"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p1250235572516"><a name="p1250235572516"></a><a name="p1250235572516"></a>Static Provisioning</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p10502055182512"><a name="p10502055182512"></a><a name="p10502055182512"></a>SAN: iSCSI/SCSI</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1550235510250"><a name="p1550235510250"></a><a name="p1550235510250"></a>SAN: iSCSI/SCSI</p>
<p id="p1155184451813"><a name="p1155184451813"></a><a name="p1155184451813"></a>NAS: DPC<sup id="sup03431118543"><a name="sup03431118543"></a><a name="sup03431118543"></a>2</sup>/NFS 3/4.1<sup id="sup592411910418"><a name="sup592411910418"></a><a name="sup592411910418"></a>3</sup></p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p1899101904919"><a name="p1899101904919"></a><a name="p1899101904919"></a>SAN<sup id="sup9603152783919"><a name="sup9603152783919"></a><a name="sup9603152783919"></a>4</sup>: FC/iSCSI/NVMe over RoCE<sup id="sup4943164011220"><a name="sup4943164011220"></a><a name="sup4943164011220"></a>6</sup></p>
</td>
</tr>
<tr id="row16502165517252"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p145026553256"><a name="p145026553256"></a><a name="p145026553256"></a>Dynamic Provisioning</p>
</td>
</tr>
<tr id="row247620119518"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p447601759"><a name="p447601759"></a><a name="p447601759"></a>Manage Provisioning<sup id="sup25964561381"><a name="sup25964561381"></a><a name="sup25964561381"></a>1</sup></p>
</td>
</tr>
<tr id="row1050205518258"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1650211552251"><a name="p1650211552251"></a><a name="p1650211552251"></a>Expand Persistent Volume<sup id="sup99731871303"><a name="sup99731871303"></a><a name="sup99731871303"></a>5</sup></p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p3160102971819"><a name="p3160102971819"></a><a name="p3160102971819"></a>Volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
</tr>
<tr id="row1450218559251"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p150210556258"><a name="p150210556258"></a><a name="p150210556258"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 "><p id="p1799618394459"><a name="p1799618394459"></a><a name="p1799618394459"></a>SAN volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.4 "><p id="p07221736144714"><a name="p07221736144714"></a><a name="p07221736144714"></a>N/A</p>
</td>
</tr>
<tr id="row205026554251"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p150235517255"><a name="p150235517255"></a><a name="p150235517255"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p150235542511"><a name="p150235542511"></a><a name="p150235542511"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1616113011918"><a name="p1616113011918"></a><a name="p1616113011918"></a>Only SAN volume snapshots are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p1472283624715"><a name="p1472283624715"></a><a name="p1472283624715"></a>N/A</p>
</td>
</tr>
<tr id="row050219555257"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p550285513251"><a name="p550285513251"></a><a name="p550285513251"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p450275592511"><a name="p450275592511"></a><a name="p450275592511"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1016012981815"><a name="p1016012981815"></a><a name="p1016012981815"></a>Only SAN volume snapshots are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p1072243604714"><a name="p1072243604714"></a><a name="p1072243604714"></a>N/A</p>
</td>
</tr>
<tr id="row135028553252"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p65021755192513"><a name="p65021755192513"></a><a name="p65021755192513"></a>Clone Persistent Volume</p>
</td>
<td class="cellrowborder" colspan="2" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 "><p id="p114410410618"><a name="p114410410618"></a><a name="p114410410618"></a>SAN volumes created in Dynamic Provisioning or Manage Provisioning mode are supported.</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.2.5.1.4 "><p id="p4722153664718"><a name="p4722153664718"></a><a name="p4722153664718"></a>N/A</p>
</td>
</tr>
<tr id="row9502145510258"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p15022553257"><a name="p15022553257"></a><a name="p15022553257"></a>Raw Block Volume</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p550255512257"><a name="p550255512257"></a><a name="p550255512257"></a>Only SAN volumes are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p15502135513255"><a name="p15502135513255"></a><a name="p15502135513255"></a>Only SAN volumes are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p27222036204714"><a name="p27222036204714"></a><a name="p27222036204714"></a>Only SAN volumes are supported.</p>
</td>
</tr>
<tr id="row17502135542517"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p5502355172519"><a name="p5502355172519"></a><a name="p5502355172519"></a>Topology</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p65038550258"><a name="p65038550258"></a><a name="p65038550258"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p155031155122514"><a name="p155031155122514"></a><a name="p155031155122514"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p177224362474"><a name="p177224362474"></a><a name="p177224362474"></a>Supported</p>
</td>
</tr>
<tr id="row795501615390"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p1250314558253"><a name="p1250314558253"></a><a name="p1250314558253"></a>Generic Ephemeral Inline Volumes</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p1503195532514"><a name="p1503195532514"></a><a name="p1503195532514"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p1503125510250"><a name="p1503125510250"></a><a name="p1503125510250"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p11722123644711"><a name="p11722123644711"></a><a name="p11722123644711"></a>Supported</p>
</td>
</tr>
<tr id="row11503255132515"><td class="cellrowborder" valign="top" headers="mcps1.2.5.1.1 "><p id="p1150335519251"><a name="p1150335519251"></a><a name="p1150335519251"></a><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes" target="_blank" rel="noopener noreferrer">Access Mode</a></p>
</td>
<td class="cellrowborder" colspan="3" valign="top" headers="mcps1.2.5.1.2 mcps1.2.5.1.3 mcps1.2.5.1.4 "><p id="p11965017181111"><a name="p11965017181111"></a><a name="p11965017181111"></a>RWO/ROX/RWOP: supported by all types of volumes. RWOP is supported only by Kubernetes 1.22 and later versions.</p>
<p id="p1241355910226"><a name="p1241355910226"></a><a name="p1241355910226"></a>RWX: supported only by Raw Block volumes and NFS volumes.</p>
</td>
</tr>
<tr id="row550395532512"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p1950375552517"><a name="p1950375552517"></a><a name="p1950375552517"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p350312554251"><a name="p350312554251"></a><a name="p350312554251"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p8503855132516"><a name="p8503855132516"></a><a name="p8503855132516"></a>Supported</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p7722163634713"><a name="p7722163634713"></a><a name="p7722163634713"></a>Supported</p>
</td>
</tr>
<tr id="row950335510253"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p850315518253"><a name="p850315518253"></a><a name="p850315518253"></a>Soft and hard quotas</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p850319558258"><a name="p850319558258"></a><a name="p850319558258"></a>Not supported</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p105891507518"><a name="p105891507518"></a><a name="p105891507518"></a>Only NAS volumes are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p11722173634710"><a name="p11722173634710"></a><a name="p11722173634710"></a>N/A</p>
</td>
</tr>
<tr id="row7503185592511"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.5.1.1 "><p id="p3503185514257"><a name="p3503185514257"></a><a name="p3503185514257"></a>Storage multi-tenant</p>
</td>
<td class="cellrowborder" valign="top" width="28.000000000000004%" headers="mcps1.2.5.1.2 "><p id="p453141013615"><a name="p453141013615"></a><a name="p453141013615"></a>Not supported</p>
</td>
<td class="cellrowborder" valign="top" width="27%" headers="mcps1.2.5.1.3 "><p id="p14871012588"><a name="p14871012588"></a><a name="p14871012588"></a>Only NAS volumes are supported.</p>
</td>
<td class="cellrowborder" valign="top" width="25%" headers="mcps1.2.5.1.4 "><p id="p6722636154710"><a name="p6722636154710"></a><a name="p6722636154710"></a>N/A</p>
</td>
</tr>
</tbody>
</table>

-   Note 1: Manage Provisioning is a volume management feature customized by Huawei CSI. This feature allows existing storage resources to be managed by Kubernetes. You are not allowed to manage a storage resource for multiple times and concurrently delete or create a storage resource.
-   Note 2: Only OceanStor Pacific series 8.1.2 and later versions support DPC. When DPC is used, the OS must meet the requirements for the  [OSs supported by Huawei CSI](/docs/compatibility-and-features/kubernetes-and-os-compatibility#table133422378818)  and the DPC basic connectivity requirements of OceanStor Pacific series.
-   Note 3: Only OceanStor Pacific series 8.1.2 and later versions support NFS 4.1. OceanStor Pacific series 8.2.0 and later versions support NFS over RDMA. When NFS over RDMA is used, only NFS 3 is supported.
-   Note 4 If a container platform is deployed on a virtualization platform, you are advised to use the iSCSI protocol when connecting to SAN storage. If the customer requires the FC, NVMe over FC, or NVMe over RoCE protocol, the virtualization platform needs to be configured. In this case, the customer's virtualization team needs to provide technical support.
-   Note 5: The provisioned PVC whose  **volumeType**  is  **lun**  and  **accessModes**  is  **ReadOnlyMany**  does not support capacity expansion.
-   Note 6: If NVMe over RoCE is used, the version of the nvme-cli tool on worker nodes ranges from 1.9 to 1.16. To query the version, run the  **nvme version**  command.

Huawei CSI plug-in supports the following features for Huawei distributed storage dtrees.

**Table  3**  Features supported by Huawei distributed storage dtrees

<a name="table17535153417812"></a>
<table><thead align="left"><tr id="row753517341082"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p1053517341819"><a name="p1053517341819"></a><a name="p1053517341819"></a>Feature</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p453514341681"><a name="p453514341681"></a><a name="p453514341681"></a>Supported</p>
</th>
</tr>
</thead>
<tbody><tr id="row1541413531981"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p151mcpsimp"><a name="p151mcpsimp"></a><a name="p151mcpsimp"></a>Static Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p154mcpsimp"><a name="p154mcpsimp"></a><a name="p154mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row241417531381"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p157mcpsimp"><a name="p157mcpsimp"></a><a name="p157mcpsimp"></a>Dynamic Provisioning</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p159mcpsimp"><a name="p159mcpsimp"></a><a name="p159mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row341412531489"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p162mcpsimp"><a name="p162mcpsimp"></a><a name="p162mcpsimp"></a>Expand Persistent Volume</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p165mcpsimp"><a name="p165mcpsimp"></a><a name="p165mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row104141753384"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p168mcpsimp"><a name="p168mcpsimp"></a><a name="p168mcpsimp"></a>Access Mode</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p170mcpsimp"><a name="p170mcpsimp"></a><a name="p170mcpsimp"></a>√ (RWX/RWO/ROX/RWOP: Kubernetes 1.22 or later supports RWOP.)</p>
</td>
</tr>
<tr id="row7414145315813"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p174mcpsimp"><a name="p174mcpsimp"></a><a name="p174mcpsimp"></a>Multi-tenant</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p176mcpsimp"><a name="p176mcpsimp"></a><a name="p176mcpsimp"></a>√</p>
</td>
</tr>
<tr id="row1741418531812"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p179mcpsimp"><a name="p179mcpsimp"></a><a name="p179mcpsimp"></a>Create VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p181mcpsimp"><a name="p181mcpsimp"></a><a name="p181mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row124142534814"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p184mcpsimp"><a name="p184mcpsimp"></a><a name="p184mcpsimp"></a>Delete VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p186mcpsimp"><a name="p186mcpsimp"></a><a name="p186mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row194141853587"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p189mcpsimp"><a name="p189mcpsimp"></a><a name="p189mcpsimp"></a>Restore VolumeSnapshot</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p191mcpsimp"><a name="p191mcpsimp"></a><a name="p191mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row2041411533814"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p194mcpsimp"><a name="p194mcpsimp"></a><a name="p194mcpsimp"></a>Clone Persistent Volume</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p197mcpsimp"><a name="p197mcpsimp"></a><a name="p197mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row1441414539814"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p200mcpsimp"><a name="p200mcpsimp"></a><a name="p200mcpsimp"></a>QoS</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p202mcpsimp"><a name="p202mcpsimp"></a><a name="p202mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row04141953984"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p205mcpsimp"><a name="p205mcpsimp"></a><a name="p205mcpsimp"></a>Volume HyperMetro</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p207mcpsimp"><a name="p207mcpsimp"></a><a name="p207mcpsimp"></a>X</p>
</td>
</tr>
<tr id="row84129531881"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p210mcpsimp"><a name="p210mcpsimp"></a><a name="p210mcpsimp"></a>Application type</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p212mcpsimp"><a name="p212mcpsimp"></a><a name="p212mcpsimp"></a>X</p>
</td>
</tr>
</tbody>
</table>

**Table  4**  Huawei storage versions supported by Huawei distributed storage dtrees

<a name="table120mcpsimp"></a>
<table><thead align="left"><tr id="row126mcpsimp"><th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.1"><p id="p128mcpsimp"><a name="p128mcpsimp"></a><a name="p128mcpsimp"></a>Storage Product</p>
</th>
<th class="cellrowborder" valign="top" width="50%" id="mcps1.2.3.1.2"><p id="p130mcpsimp"><a name="p130mcpsimp"></a><a name="p130mcpsimp"></a>Version</p>
</th>
</tr>
</thead>
<tbody><tr id="row132mcpsimp"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.1 "><p id="p19397953184113"><a name="p19397953184113"></a><a name="p19397953184113"></a>OceanStor Pacific series</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.2.3.1.2 "><p id="p6397953124114"><a name="p6397953124114"></a><a name="p6397953124114"></a>8.1.0, 8.1.1, 8.1.2, 8.1.3, 8.1.5, 8.2.0, 8.2.1</p>
</td>
</tr>
</tbody>
</table>

