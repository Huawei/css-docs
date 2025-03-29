---
title: "Installing Huawei CSI on the CCE or CCE Agile Platform"
linkTitle: "Installing Huawei CSI on the CCE or CCE Agile Platform"
description: 
weight: 2
---

This section describes how to install Huawei CSI on the CCE or CCE Agile platform.

## Creating a Helm Installation Package{#section2032812215509}

The CCE or CCE Agile platform cannot directly install Huawei CSI using Helm. You need to manually create a Helm installation package and upload it to the chart list on the platform for installation.

1.  Use a remote access tool, such as PuTTY, to log in to any node where Helm is deployed through the management IP address.
2.  Copy the  **helm**  directory in the Huawei CSI component package to any directory on the node. For details about the Helm tool path, see  [Table 1](/docs/installation-and-deployment/installation-preparations/downloading-the-huawei-csi-software-package#en-us_topic_0150885197_table17200162435412).
3.  Go to the  **helm**  working directory.

    ```
    cd helm/
    ```

4.  Modify the  **kubeletConfigDir**  and  **csiDriver.driverName**  parameters in the  **helm/esdk/values.yaml**  file.

    ```
    vi ./esdk/values.yaml
    ```

    Modify the following parameters:

    ```yaml
    # Specify kubelet config dir path.
    # kubernetes and openshift is usually /var/lib/kubelet
    # Tanzu is usually /var/vcap/data/kubelet
    # CCE is usually /mnt/paas/kubernetes/kubelet
    kubeletConfigDir: /mnt/paas/kubernetes/kubelet
    
    # The CSI driver parameter configuration
    csiDriver:
      # Driver name, it is strongly recommended not to modify this parameter
      # The CCE platform needs to modify this parameter, e.g. csi.oceanstor.com
      driverName: csi.oceanstor.com
    ```

5.  Run the following command to create a Helm installation package. This command will generate the installation package to the current path.

    ```
    helm package ./esdk/ -d ./
    ```

## Installing Huawei CSI{#section3411185295111}

1.  Use a remote access tool, such as PuTTY, to log in to any master node where the CCE Agile platform is deployed through the management IP address.
2.  Run the following command to create a namespace for deploying Huawei CSI.  _huawei-csi_  indicates the custom namespace.

    ```
    kubectl create namespace huawei-csi
    ```

3.  Export the Helm installation package. For details, see  [Creating a Helm Installation Package](#section2032812215509).
4.  On the home page, choose  **Charts**  \>  **My Charts**  \>  **Upload Chart**. The  **Upload Chart**  dialog box is displayed. Import the exported Helm installation package to the CCE Agile platform.

    ![](/css-docs/figures/上传模板-ch.png)

5.  After the installation package is uploaded, choose  **Charts**  \>  **My Charts**. On the  **My Charts**  page that is displayed, choose  **Install**  \>  **Submit**. The chart release name can be customized.

    ![](/css-docs/figures/安装csi中文.png)

6.  On the home page, choose  **Charts**  \>  **Releases**  and select the project specified during installation \(for example,  **default**  in the following figure\). After the installation is successful,  **Installed**  is displayed in the  **Status**  column.

    ![](/css-docs/figures/安装结果-ch.png)

