---
title: "A Pod Fails to Be Created and the Log Shows That the Execution of the mount Command Times Out"
linkTitle: "A Pod Fails to Be Created and the Log Shows That the Execution of the mount Command Times Out"
description: 
weight: 4
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

When a Pod is being created, the Pod keeps in the  **ContainerCreating**  status. In this case, check the log information of huawei-csi-node \(for details, see  [Viewing Huawei CSI Logs](/docs/common-o-m-operations/collecting-information/viewing-huawei-csi-logs)\). The log shows that the execution of the mount command times out.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

Cause 1: The configured service IP address is disconnected. As a result, the  **mount**  command execution times out and fails.

Cause 2: For some operating systems, such as Kylin V10 SP1 and SP2, it takes a long time to run the  **mount**  command in a container using NFSv3. As a result, the  **mount**  command may time out and error message "error: exit status 255" is displayed. The possible cause is that the value of  **LimitNOFILE**  of container runtime containerd is too large \(over 1 billion\).

Cause 3: The mounting may fail due to network problems. The default mounting timeout period of CSI is 30 seconds. If the mounting still fails after 30 seconds, logs show that the execution of the  **mount**  command times out.

## Solution or Workaround{#en-us_topic_0000001279996521_section164471213145410}

1.  Run the  **ping**  command to check whether the service IP network is connected. If the ping fails, the fault is caused by cause 1. In this case, configure an available service IP address. If the ping succeeds, go to  [2](#li21141916181411).
2.  <a name="li21141916181411"></a>Go to any container where the  **mount**  command can be executed and use NFSv3 to run the  **mount**  command. If the command times out, the fault may be caused by cause 2. Run the  **systemctl status containerd.service**  command to check the configuration file path, and then run the  **cat **_/xxx/containerd.service_  command to check the configuration file. If the file contains  **LimitNOFILE=infinity**  or the value of  **LimitNOFILE**  is 1 billion, go to  [3](#li560665881414). Otherwise, contact Huawei technical support engineers.
3.  <a name="li560665881414"></a>For cause 2, perform the following operations:
    -   Try using NFSv4.0.
    -   Change the value of  **LimitNOFILE**  to a proper one by referring to  [change solution provided by the community](https://github.com/containerd/containerd/issues/3201). This solution will restart the container runtime. Evaluate the impact on services.

4.  Manually mount the file system on the host machine where the mounting fails. If the required time exceeds 30 seconds, check whether the network between the host machine and the storage node is normal. An example of the  **mount**  command is as follows.
    -   Run the following command to create a test directory.

        ```
        mkdir /tmp/test_mount
        ```

    -   Run the  **mount**  command to mount the file system and observe the time consumed. The value of  _ip:nfs\_share\_path_  can be obtained from the huawei-csi-node log. For details, see  [Viewing Huawei CSI Logs](/docs/common-o-m-operations/collecting-information/viewing-huawei-csi-logs).

        ```
        time mount ip:nfs_share_path /tmp/test_mount
        ```

    -   After the test is complete, run the following command to unmount the file system.

        ```
        umount /tmp/test_mount
        ```

