---
title: "Creating a Storage Backend"
linkTitle: "Creating a Storage Backend"
description: 
weight: 1
---

## Prerequisites{#section358111304711}

-   You have obtained the management IP address, username, and password of the storage device.
-   You have obtained configuration information such as the storage pool name and storage protocol. For details about the configuration items, see section  [Configuring the Storage Backend](/docs/basic-services/storage-backend-management/configuring-the-storage-backend).

## Procedure{#section557492184715}

1.  Prepare the secret configuration file, for example,  **backend-secret.yaml**. For details about the fields in the secret configuration file, see  [Table 1](#table19947114583113).

    ```yaml
    apiVersion: v1
    kind: Secret
    metadata:
      name: backend-demo
      namespace: huawei-csi
    type: Opaque
    stringData:
      user: "admin"
      password: "******"
      authenticationMode: "0"
    ```

    Create a secret.

    ```
    kubectl apply -f backend-secret.yaml
    ```

    **Table  1**  Secret field description

    <a name="table19947114583113"></a>
    <table><thead align="left"><tr id="row89472045163110"><th class="cellrowborder" valign="top" width="18%" id="mcps1.2.6.1.1"><p id="p1794719455315"><a name="p1794719455315"></a><a name="p1794719455315"></a>Parameter</p>
    </th>
    <th class="cellrowborder" valign="top" width="42%" id="mcps1.2.6.1.2"><p id="p119470457312"><a name="p119470457312"></a><a name="p119470457312"></a>Description</p>
    </th>
    <th class="cellrowborder" valign="top" width="10%" id="mcps1.2.6.1.3"><p id="p1994718455316"><a name="p1994718455316"></a><a name="p1994718455316"></a>Mandatory</p>
    </th>
    <th class="cellrowborder" valign="top" width="10%" id="mcps1.2.6.1.4"><p id="p17947144553117"><a name="p17947144553117"></a><a name="p17947144553117"></a>Default Value</p>
    </th>
    <th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.5"><p id="p1947104511315"><a name="p1947104511315"></a><a name="p1947104511315"></a>Remarks</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row16947194503111"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p3947445103116"><a name="p3947445103116"></a><a name="p3947445103116"></a>user</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p494824518316"><a name="p494824518316"></a><a name="p494824518316"></a>Username for logging in to the storage.</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p19948245103114"><a name="p19948245103114"></a><a name="p19948245103114"></a>Yes</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p594817450314"><a name="p594817450314"></a><a name="p594817450314"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
    </tr>
    <tr id="row89481745103113"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p99481545113119"><a name="p99481545113119"></a><a name="p99481545113119"></a>password</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p694814515312"><a name="p694814515312"></a><a name="p694814515312"></a>Password for logging in to the storage.</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p1948345103110"><a name="p1948345103110"></a><a name="p1948345103110"></a>Yes</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p11948845173112"><a name="p11948845173112"></a><a name="p11948845173112"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
    </tr>
    <tr id="row29481045153113"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p1194844533119"><a name="p1194844533119"></a><a name="p1194844533119"></a>authenticationMode</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p19948245173110"><a name="p19948245173110"></a><a name="p19948245173110"></a>Authentication mode for logging in to the storage. The value can be:</p>
    <a name="ul6470437113514"></a><a name="ul6470437113514"></a><ul id="ul6470437113514"><li><strong id="b2018293511312"><a name="b2018293511312"></a><a name="b2018293511312"></a>0</strong>: local authentication</li><li><strong id="b3316339153113"><a name="b3316339153113"></a><a name="b3316339153113"></a>1</strong>: LDAP authentication</li></ul>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p189481645103113"><a name="p189481645103113"></a><a name="p189481645103113"></a>No</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p1394894519313"><a name="p1394894519313"></a><a name="p1394894519313"></a>0</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p29481945103112"><a name="p29481945103112"></a><a name="p29481945103112"></a>Only OceanStor Dorado, OceanStor V5, OceanStor V6, OceanStor A600, and OceanStor A800 support LDAP authentication.</p>
    </td>
    </tr>
    <tr id="row1994819451314"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p79489452311"><a name="p79489452311"></a><a name="p79489452311"></a>maxClientThreads</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p1294884553119"><a name="p1294884553119"></a><a name="p1294884553119"></a>Maximum number of concurrent connections to a storage backend.</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p10948345163112"><a name="p10948345163112"></a><a name="p10948345163112"></a>No</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p6948124543119"><a name="p6948124543119"></a><a name="p6948124543119"></a>30</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p69487457313"><a name="p69487457313"></a><a name="p69487457313"></a>The value ranges from 1 to 30.</p>
    </td>
    </tr>
    </tbody>
    </table>

2.  Create a ConfigMap resource for the storage backend to store the management configuration of the storage device.

    Prepare the ConfigMap configuration file. The following describes how to create an OceanStor SAN storage backend of the iSCSI protocol type. The value of the  **csi.json**  key is the storage backend configuration in JSON format. For details about the configuration items, see  [Configuring the Storage Backend](/docs/basic-services/storage-backend-management/configuring-the-storage-backend).

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: backend-demo
      namespace: huawei-csi
    data:
      csi.json: |-
        {
          "backends": {
            "storage": "oceanstor-san",
            "name": "backend-demo",
            "namespace": "huawei-csi",
            "urls": ["https://192.168.129.157:8088"],
            "pools": ["StoragePool001"],
            "provisioner": "csi.huawei.com",
            "parameters": {
              "protocol": "iscsi",
              "portals": ["10.10.30.20", "10.10.30.21"]
            },
            "maxClientThreads": "30"
          }
        }
    ```

    Create a ConfigMap.

    ```
    kubectl apply -f backend-configmap.yaml
    ```

3.  Create a StorageBackendClaim resource to trigger the CSI controller to access the storage backend. For details about the fields in StorageBackendClaim, see  [Table 2](#table1290132113815).

    Prepare the StorageBackendClaim configuration file, for example,  **backend-claim.yaml**.

    ```yaml
    apiVersion: xuanwu.huawei.io/v1
    kind: StorageBackendClaim
    metadata:
      name: backend-demo
      namespace: huawei-csi
    spec:
      provider: csi.huawei.com
      configmapMeta: huawei-csi/backend-demo
      secretMeta: huawei-csi/backend-demo
      maxClientThreads: "30"
    ```

    Create a StorageBackendClaim.

    ```
    kubectl apply -f backend-claim.yaml
    ```

    **Table  2**  StorageBackendClaim spec field description

    <a name="table1290132113815"></a>
    <table><thead align="left"><tr id="row7105821103819"><th class="cellrowborder" valign="top" width="18%" id="mcps1.2.6.1.1"><p id="p310542119382"><a name="p310542119382"></a><a name="p310542119382"></a>Parameter</p>
    </th>
    <th class="cellrowborder" valign="top" width="42%" id="mcps1.2.6.1.2"><p id="p19105162163812"><a name="p19105162163812"></a><a name="p19105162163812"></a>Description</p>
    </th>
    <th class="cellrowborder" valign="top" width="10%" id="mcps1.2.6.1.3"><p id="p1810532119388"><a name="p1810532119388"></a><a name="p1810532119388"></a>Mandatory</p>
    </th>
    <th class="cellrowborder" valign="top" width="10%" id="mcps1.2.6.1.4"><p id="p410532163812"><a name="p410532163812"></a><a name="p410532163812"></a>Default Value</p>
    </th>
    <th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.5"><p id="p910562173818"><a name="p910562173818"></a><a name="p910562173818"></a>Remarks</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row16105821183812"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p0106192119386"><a name="p0106192119386"></a><a name="p0106192119386"></a>provider</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p7106112193815"><a name="p7106112193815"></a><a name="p7106112193815"></a>Provider name, which is used to match the CSI plug-in.</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p51061421113818"><a name="p51061421113818"></a><a name="p51061421113818"></a>Yes</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p31068213389"><a name="p31068213389"></a><a name="p31068213389"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p121063215381"><a name="p121063215381"></a><a name="p121063215381"></a>The value is fixed to <strong id="b1731712553517"><a name="b1731712553517"></a><a name="b1731712553517"></a>csi.huawei.com</strong>.</p>
    </td>
    </tr>
    <tr id="row1210662114383"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p9106221133816"><a name="p9106221133816"></a><a name="p9106221133816"></a>configmapMeta</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p610682133812"><a name="p610682133812"></a><a name="p610682133812"></a>Reference to the ConfigMap of the storage configuration information. The format is <em id="i3676141053718"><a name="i3676141053718"></a><a name="i3676141053718"></a>&lt;namespace&gt;</em>/<em id="i784051593710"><a name="i784051593710"></a><a name="i784051593710"></a>&lt;name&gt;</em>.</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p1510682113382"><a name="p1510682113382"></a><a name="p1510682113382"></a>Yes</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p71065214385"><a name="p71065214385"></a><a name="p71065214385"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p131061211387"><a name="p131061211387"></a><a name="p131061211387"></a>The value must be the same as the name of the ConfigMap created in step 2.</p>
    </td>
    </tr>
    <tr id="row81062021203820"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p71061821183820"><a name="p71061821183820"></a><a name="p71061821183820"></a>secretMeta</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p16106132118383"><a name="p16106132118383"></a><a name="p16106132118383"></a>Reference to the secret of the storage authentication information. The format is <em id="i1939318202398"><a name="i1939318202398"></a><a name="i1939318202398"></a>&lt;namespace&gt;</em>/<em id="i23932020123915"><a name="i23932020123915"></a><a name="i23932020123915"></a>&lt;name&gt;</em>.</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p1910632114388"><a name="p1910632114388"></a><a name="p1910632114388"></a>Yes</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p121066211386"><a name="p121066211386"></a><a name="p121066211386"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p310610213381"><a name="p310610213381"></a><a name="p310610213381"></a>The value must be the same as the name of the secret created in step 1.</p>
    </td>
    </tr>
    <tr id="row61067217387"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p2106621153816"><a name="p2106621153816"></a><a name="p2106621153816"></a>maxClientThreads</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p11060217388"><a name="p11060217388"></a><a name="p11060217388"></a>Maximum number of concurrent connections to a storage backend.</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p81062217388"><a name="p81062217388"></a><a name="p81062217388"></a>No</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p16107102116381"><a name="p16107102116381"></a><a name="p16107102116381"></a>30</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p610762113818"><a name="p610762113818"></a><a name="p610762113818"></a>The value ranges from 1 to 30.</p>
    </td>
    </tr>
    </tbody>
    </table>

4.  Check the storage backend creation result.

    ```
    kubectl get sbct
    ```

    The following is an example of the command output. If the online status of StorageBackendContent is  **true**, the creation is successful.

    ```
    NAME              CLAIM                       SN               VENDORNAME   PROVIDERVERSION   ONLINE   AGE
    content-xxxxxxx   huawei-csi/backend-demo     xxxxxxxxxxxxxx   Huawei       4.13.0            true     53d
    ```

