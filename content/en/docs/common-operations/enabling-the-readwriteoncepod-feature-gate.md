---
title: "Enabling the ReadWriteOncePod Feature Gate"
linkTitle: "Enabling the ReadWriteOncePod Feature Gate"
description: 
weight: 6
---

The ReadWriteOnce access mode is the fourth access mode introduced by Kubernetes v1.22 for PVs and PVCs. If you create a Pod using a PVC in ReadWriteOncePod access mode, Kubernetes ensures that the Pod is the only Pod in the cluster that can read or write the PVC.

The ReadWriteOncePod access mode is an alpha feature in Kubernetes v1.22/1.23/1.24. Therefore, you need to enable the ReadWriteOncePod feature in  **feature-gates**  of kube-apiserver, kube-scheduler, and kubelet before using the access mode.

>![](/public_sys-resources/en/icon-note.gif)
>Currently, the CCE or CCE Agile platform does not support the ReadWriteOncePod feature gate.

## Procedure{#en-us_topic_0000001259843616_section137882216292}

1.  Enable the ReadWriteOncePod feature gate for kube-apiserver.
    1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
    2.  Run the  **vi /etc/kubernetes/manifests/kube-apiserver.yaml**  command, press  **I**  or  **Insert**  to enter the insert mode, and add  **--feature-gates=ReadWriteOncePod=true**  to the kube-apiserver container. After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

        ```
        ...
        spec:
          containers:
          - command:
            - kube-apiserver
            - --feature-gates=ReadWriteOncePod=true
            ...
        ```

        >![](/public_sys-resources/en/icon-note.gif)
        >After the editing is complete, Kubernetes will automatically apply the updates.

2.  Enable the ReadWriteOncePod feature gate for kube-scheduler.
    1.  Use a remote access tool, such as PuTTY, to log in to any master node in the Kubernetes cluster through the management IP address.
    2.  Run the  **vi /etc/kubernetes/manifests/kube-scheduler.yaml**  command, press  **I**  or  **Insert**  to enter the insert mode, and add  **--feature-gates=ReadWriteOncePod=true**  to the kube-scheduler container. After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

        ```
        ...
        spec:
          containers:
          - command:
            - kube-scheduler
            - --feature-gates=ReadWriteOncePod=true
            ...
        ```

        >![](/public_sys-resources/en/icon-note.gif)
        >After the editing is complete, Kubernetes will automatically apply the updates.

3.  Enable the ReadWriteOncePod feature gate for kubelet.

    >![](/public_sys-resources/en/icon-notice.gif) 
    >The dynamic Kubelet configuration function is not used since v1.22 and deleted in v1.24. Therefore, you need to perform the following operations on kubelet on each worker node in the cluster.

    1.  Use a remote access tool, such as PuTTY, to log in to any worker node in the Kubernetes cluster through the management IP address.
    2.  Run the  **vi /var/lib/kubelet/config.yaml**  command, press  **I**  or  **Insert**  to enter the editing state, and add  **ReadWriteOncePod: true**  to the  **featureGates**  field of the KubeletConfiguration object. If the  **featureGates**  field does not exist, add it at the same time. After the modification is complete, press  **Esc**  and enter  **:wq!**  to save the modification.

        ```
        apiVersion: kubelet.config.k8s.io/v1beta1
        featureGates:
          ReadWriteOncePod: true
          ...
        ```

        >![](/public_sys-resources/en/icon-note.gif)
        >The default path of the kubelet configuration file is  **/var/lib/kubelet/config.yaml**. Enter the path based on site requirements.

    3.  After the configuration is complete, run the  **systemctl restart kubelet**  command to restart kubelet.

