---
title: "CCE或CCE Agile卸载华为CSI"
linkTitle: "CCE或CCE Agile卸载华为CSI"
description: 
weight: 2
---

本章节介绍如何在CCE或CCE Agile平台卸载华为CSI，以CCE Agile v22.3.2为例。

## 操作步骤{#section1489941282414}

1.  登录CCE Agile平台。
2.  在主页单击“模板市场\> 模板实例 ”，进入模板实例页面。
3.  选择华为CSI模板实例，单击“卸载”，在弹出的提示框中单击“确定”。

    ![](/css-docs/figures/卸载-ch.png)

4.  卸载huawei-csi-host-info对象，请参考[卸载huawei-csi-host-info对象](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section870813403017)进行操作。
5.  卸载webhook资源，请参考[卸载Webhook资源](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section871155813014)进行操作。
6.  （可选）卸载快照依赖组件服务，请参考[卸载Snapshot依赖组件服务](/v4.5.0/installation-and-deployment/uninstalling-huawei-csi/uninstalling-huawei-csi-using-helm/uninstalling-csi-dependent-component-services#section48371491319)进行操作。

