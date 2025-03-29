---
title: "Uploading a Huawei CSI Image"
linkTitle: "Uploading a Huawei CSI Image"
description: 
weight: 2
---

Huawei provides the  **huawei-csi**  image for users. For details about how to obtain the image file, see  [Downloading the Huawei CSI Software Package](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package).

To use the CSI image on the container management platform, you need to import the CSI image to the cluster in advance using either of the following methods:

-   \(Recommended\) Use Docker to upload the CSI image to the image repository.
-   Manually import the CSI image to all nodes where Huawei CSI needs to be deployed.

## Uploading an Image to the Image Repository{#section93821739143119}

The installation of Huawei CSI depends on the following image files provided by Huawei. Import and upload the image files in sequence. For details about how to obtain the image files, see  [Downloading the Huawei CSI Software Package](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package).

-   huawei-csi-v4.7.0-arch.tar
-   storage-backend-controller-v4.7.0-_arch_.tar
-   storage-backend-sidecar-v4.7.0-_arch_.tar
-   huawei-csi-extender-v4.7.0-arch.tar

**Prerequisites**

A Linux host with Docker installed is available, and the host can access the image repository.

**Procedure**

1.  Run the following command to import the CSI image to the current node. The value of  _arch_  can be  **X86**,  **ARM**, or  **PPC64LE**.

    ```
    docker load -i huawei-csi-v4.7.0-<arch>.tar 
    ```

2.  Run the following command to add the image repository address to the image tag.  **repo.huawei.com**  indicates the image repository address.

    ```
    docker tag huawei-csi:4.7.0 <repo.huawei.com>/huawei-csi:4.7.0
    ```

3.  Run the following command to upload the CSI image to the image repository.  **repo.huawei.com**  indicates the image repository address.

    ```
    docker push <repo.huawei.com>/huawei-csi:4.7.0
    ```

>![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
>-   You can also use containerd to import and upload the images.
>-   For details about how to import and upload images to the CCE or CCE Agile platform, see the user manual of the platform.

## Uploading an Image to a Local Node{#section15439218133113}

If the image has been uploaded to the image repository, skip this section.

**Prerequisites**

-   The node has the corresponding Huawei CSI image file. For details about how to obtain the image file, see  [Downloading the Huawei CSI Software Package](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package).
-   Docker or another container engine has been installed on the node.

**Procedure**

1.  Use a remote access tool, such as PuTTY, to log in to the node where the image is to be imported through the management IP address.
2.  Copy the  **image**  directory in the Kubernetes CSI component package to any directory on the current node.
3.  Run the  **cd image**  command to go to the  **image**  working directory. For details about the tool path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).
4.  Run the following commands in sequence to import all Huawei CSI images in the  **image**  directory to the local node. In the commands,  _name_  indicates the name of a .tar image package.

    Run the following command using the Docker container engine:

    ```
    docker load -i <name>.tar
    ```

    Run the following command using the containerd container engine:

    ```
    ctr -n k8s.io image import <name>.tar
    ```

    Run the following command using the Podman container engine:

    ```
    podman load -i <name>.tar
    ```

    >![](/css-docs/public_sys-resources/en-us/icon-notice.gif)  
    >If another container engine is installed on the node, use the image import command for the corresponding container engine.

