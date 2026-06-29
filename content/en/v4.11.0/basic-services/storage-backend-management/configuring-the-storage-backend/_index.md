---
title: "Configuring the Storage Backend"
linkTitle: "Configuring the Storage Backend"
description: 
weight: 1
---

>![](/css-docs/public_sys-resources/en-us/icon-note.gif)  
>1.  When oceanctl is used to create a storage backend, the entered account and key information is stored in the  [Secret](https://kubernetes.io/docs/concepts/configuration/secret/)  object. It is recommended that the customer container platform encrypt the Secret object based on the suggestions of the supplier or K8s community. For details about how to encrypt the Secret object in the K8s community, see  [Encrypting Confidential Data at Rest](https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/).
>2.  When a backend is created using a .json file, the backend name of an earlier version may contain uppercase letters or underscores \(\_\). In this case, the old name is remapped to a new name. The mapping process automatically occurs and does not affect the original functions. For example,  **ABC\_123**  is mapped to  **abc-123-fd68e**. The mapping rules are as follows:
>    -   Uppercase letters are converted to lowercase letters.
>    -   An underscore \(\_\) is converted to a hyphen \(-\).
>    -   A 5-digit hash code is added to the end.
>3.  If a storage backend is connected to a vStore, the vStore name cannot be changed after the storage backend is created.






