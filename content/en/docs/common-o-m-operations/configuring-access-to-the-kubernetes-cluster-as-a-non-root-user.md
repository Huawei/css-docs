---
title: "Configuring Access to the Kubernetes Cluster as a Non-root User"
linkTitle: "Configuring Access to the Kubernetes Cluster as a Non-root User"
description: 
weight: 7
---

## Procedure{#en-us_topic_0000001283708426_section11147613122310}

1.  Copy the authentication file of the Kubernetes cluster and modify  **/etc/kubernetes/admin.conf**  to be the actual authentication file.

    ```
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    ```

2.  Change the user and user group of the authentication file.

    ```
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
    ```

3.  Configure the  **KUBECONFIG**  environment variable of the current user. The following uses Ubuntu 20.04 as an example.

    ```
    echo "export KUBECONFIG=$HOME/.kube/config" >> ~/.bashrc
    source ~/.bashrc
    ```

