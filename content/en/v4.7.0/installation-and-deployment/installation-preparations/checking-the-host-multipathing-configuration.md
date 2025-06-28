---
title: "Checking the Host Multipathing Configuration"
linkTitle: "Checking the Host Multipathing Configuration"
description: 
weight: 5
---

If you plan to use the FC/iSCSI/NVMe over RoCE/NVMe over FC protocol to access Huawei storage in a container environment, you are advised to use host multipathing software to enhance the link redundancy and performance of the host and storage. If you do not want to use the software, skip this section.

For details about the OSs and multipathing software supported by Huawei CSI, see  [Table 2](/docs/compatibility-and-features/kubernetes-and-os-compatibility#table133422378818).

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>-   If you want to use the FC/iSCSI protocol to connect to Huawei storage, you are advised to use native DM-Multipath provided by the OS.
>-   If you want to use the NVMe over RoCE/NVMe over FC protocol to connect to Huawei storage, you are advised to use Huawei-developed UltraPath-NVMe.
>-   If you want to use the SCSI protocol to connect to Huawei storage, disable DM-Multipath provided by the OS.

## Prerequisites{#section43820464358}

Multipathing software has been correctly installed on a host.

-   If you use native DM-Multipath provided by the OS, contact your host or OS provider to obtain the documents and software packages required for the installation.
-   If you use Huawei-developed UltraPath or UltraPath-NVMe, contact Huawei engineers to obtain the UltraPath or UltraPath-NVMe documents and software packages. For details about the software package versions, see  [Table 2](/docs/compatibility-and-features/kubernetes-and-os-compatibility#table133422378818).

## Procedure{#section14674125816351}

1.  If you use the iSCSI/FC protocol to connect to Huawei enterprise storage, configure and check host multipathing by referring to  _[OceanStor Dorado and OceanStor Host Connectivity Guide for Red Hat](https://support.huawei.com/enterprise/en/doc/EDOC1100113070/1b4ad686/os-native-multipathing-software)_.
2.  If you use the NVMe over RoCE/NVMe over FC protocol to connect to Huawei enterprise storage, configure and check host multipathing by referring to  _[OceanStor Dorado and OceanStor Host Connectivity Guide for Red Hat](https://support.huawei.com/enterprise/en/doc/EDOC1100113070/5f5e5688/ultrapath)_.
3.  If you use iSCSI to connect to Huawei distributed storage, configure and check host multipathing by referring to  [Configuring Multipathing for an Application Server](https://support.huawei.com/enterprise/en/doc/EDOC1100115354/59dfdd73)  in  _[FusionStorage 8.0.1 Block Storage Basic Service Configuration Guide](https://support.huawei.com/enterprise/en/doc/EDOC1100115354)_.
4.  If you use the native multipathing software provided by the OS, check whether the  **/etc/multipath.conf**  file contains the following configuration item.

    ```
    defaults {
            user_friendly_names yes
            find_multipaths no
    }
    ```

    If the configuration item does not exist, add it to the beginning of the  **/etc/multipath.conf**  file.

    >![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
    >For details about the functions of the  **user\_friendly\_names**  and  **find\_multipaths**  parameters, see  [dm\_multipath/config\_file\_defaults](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/dm_multipath/config_file_defaults).

