---
title: "Uninstalling Huawei CSI on CCE or CCE Agile"
linkTitle: "Uninstalling Huawei CSI on CCE or CCE Agile"
description: 
weight: 2
---

This section describes how to uninstall Huawei CSI on the CCE or CCE Agile platform. The following uses CCE Agile v22.3.2 as an example.

## Procedure{#section1489941282414}

1.  Log in to the CCE Agile platform.
2.  On the home page, choose  **Charts**  \>  **Releases**. The  **Releases**  page is displayed.
3.  Select a Huawei CSI release and click  **Uninstall**. In the displayed dialog box, click  **OK**.

    ![](/figures/卸载-en.png)

4.  Uninstall the huawei-csi-host-info object. For details, see  [Uninstalling the huawei-csi-host-info Object](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section870813403017).
5.  Uninstall the webhook resource. For details, see  [Uninstalling a Webhook Resource](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section871155813014).
6.  \(Optional\) Uninstall the snapshot-dependent component service. For details, see  [Uninstalling the Snapshot-Dependent Component Service](/docs/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section48371491319).

