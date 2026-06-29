---
title: "Installing Helm 3"
linkTitle: "Installing Helm 3"
description: 
weight: 1
---

This section describes how to install Helm 3.

For details, see  [https://helm.sh/docs/intro/install/](https://helm.sh/docs/intro/install/).

## Prerequisites{#en-us_topic_0000001274250896_section19453102010152}

Ensure that the master node in the Kubernetes cluster can access the Internet.

## Procedure{#section164291640172317}

1.  Run the following command to download the Helm 3 installation script.

    ```
    curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
    ```

2.  Run the following command to modify the permission on the Helm 3 installation script.

    ```
    chmod 700 get_helm.sh
    ```

3.  Determine the Helm version to be installed based on the version mapping between Helm and Kubernetes. For details about the version mapping, see  [Helm Version Support Policy](https://helm.sh/docs/topics/version_skew/#supported-version-skew). Then run the following command to change the  **DESIRED\_VERSION**  environment variable to the Helm version to be installed and run the installation command.

    ```
    DESIRED_VERSION=v3.9.0 ./get_helm.sh
    ```

4.  Run the following command to check whether Helm 3 of the specified version is successfully installed.

    ```
    helm version
    ```

    If the following information is displayed, the installation is successful.

    ```
    version.BuildInfo{Version:"v3.9.0", GitCommit:"7ceeda6c585217a19a1131663d8cd1f7d641b2a7", GitTreeState:"clean", GoVersion:"go1.17.5"}
    ```

