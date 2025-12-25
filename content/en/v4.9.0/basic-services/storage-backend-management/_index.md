---
title: "Storage Backend Management"
linkTitle: "Storage Backend Management"
description: 
weight: 1
---

Backend is an abstract concept of Huawei storage resources. Each Huawei storage device can abstract multiple backend resources using features such as tenants, storage pools, and protocols. Each backend exists independently and defines Huawei storage information required for providing persistent volumes for Kubernetes clusters.

This section describes how to use the oceanctl tool to configure and manage storage backends.

## Description of the oceanctl Tool{#section1490867112}

-   You have obtained the oceanctl tool, copied the oceanctl tool to the environment directory, for example,  **/usr/local/bin**, and obtained the execute permission. The oceanctl tool is stored in  **/bin/oceanctl**  of the software package.
-   The oceanctl tool depends on  **kubectl**  \(for the Kubernetes platform\) or  **oc**  \(for the OpenShift platform\) commands. Therefore, you need to run the tool on a node where  **kubectl**  or  **oc**  commands can be executed.
-   By default, the user who runs  **oceanctl**  commands must have the read and write permissions on the  **/var/log**  directory. If you do not have the permissions on the directory, run the  **--log-dir=/path/to/custom**  command to specify a directory on which you have the permissions as the log file directory.
-   **huawei-csi**  is the default namespace used by oceanctl to create a backend.
-   For details about  **oceanctl**  commands, see  [Description of oceanctl Commands](/docs/command-parameter-description/description-of-oceanctl-commands).



