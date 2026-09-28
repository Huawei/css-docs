---
title: "创建存储后端"
linkTitle: "创建存储后端"
description: 
weight: 1
---

## 前提条件{#section358111304711}

-   已获取存储设备的管理IP地址、用户名、密码等信息。
-   已获取存储池名称、存储协议等配置信息，具体配置项说明请参考配置存储后端章节。

## 操作步骤{#section557492184715}

1.  准备Secret配置文件，如backend-secret.yaml，Secret中字段说明见[表1 Secret字段说明](#table19947114583113)。

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

    执行以下命令创建Secret。

    ```
    kubectl apply -f backend-secret.yaml
    ```

    **表 1**  Secret字段说明

    <a name="table19947114583113"></a>
    <table><thead align="left"><tr id="row89472045163110"><th class="cellrowborder" valign="top" width="18%" id="mcps1.2.6.1.1"><p id="p1794719455315"><a name="p1794719455315"></a><a name="p1794719455315"></a>参数</p>
    </th>
    <th class="cellrowborder" valign="top" width="42%" id="mcps1.2.6.1.2"><p id="p119470457312"><a name="p119470457312"></a><a name="p119470457312"></a>描述</p>
    </th>
    <th class="cellrowborder" valign="top" width="10%" id="mcps1.2.6.1.3"><p id="p1994718455316"><a name="p1994718455316"></a><a name="p1994718455316"></a>必选</p>
    </th>
    <th class="cellrowborder" valign="top" width="10%" id="mcps1.2.6.1.4"><p id="p17947144553117"><a name="p17947144553117"></a><a name="p17947144553117"></a>默认值</p>
    </th>
    <th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.5"><p id="p1947104511315"><a name="p1947104511315"></a><a name="p1947104511315"></a>备注</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row16947194503111"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p3947445103116"><a name="p3947445103116"></a><a name="p3947445103116"></a>user</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p494824518316"><a name="p494824518316"></a><a name="p494824518316"></a>用于登录存储的用户名。</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p19948245103114"><a name="p19948245103114"></a><a name="p19948245103114"></a>是</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p594817450314"><a name="p594817450314"></a><a name="p594817450314"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
    </tr>
    <tr id="row89481745103113"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p99481545113119"><a name="p99481545113119"></a><a name="p99481545113119"></a>password</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p694814515312"><a name="p694814515312"></a><a name="p694814515312"></a>用于登录存储的密码。</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p1948345103110"><a name="p1948345103110"></a><a name="p1948345103110"></a>是</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p11948845173112"><a name="p11948845173112"></a><a name="p11948845173112"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 ">&nbsp;&nbsp;</td>
    </tr>
    <tr id="row29481045153113"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p1194844533119"><a name="p1194844533119"></a><a name="p1194844533119"></a>authenticationMode</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p19948245173110"><a name="p19948245173110"></a><a name="p19948245173110"></a>用于登录存储的认证模式。可配值如下：</p>
    <a name="ul6470437113514"></a><a name="ul6470437113514"></a><ul id="ul6470437113514"><li>"0"：本地认证</li><li>"1"：LDAP认证</li></ul>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p189481645103113"><a name="p189481645103113"></a><a name="p189481645103113"></a>否</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p1394894519313"><a name="p1394894519313"></a><a name="p1394894519313"></a>"0"</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p29481945103112"><a name="p29481945103112"></a><a name="p29481945103112"></a>仅 OceanStor Dorado/OceanStor V5/OceanStor V6/OceanStor A600/OceanStor A800 存储支持配置LDAP认证</p>
    </td>
    </tr>
    <tr id="row1994819451314"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p79489452311"><a name="p79489452311"></a><a name="p79489452311"></a>maxClientThreads</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p1294884553119"><a name="p1294884553119"></a><a name="p1294884553119"></a>同时连接到存储后端的最大连接数。</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p10948345163112"><a name="p10948345163112"></a><a name="p10948345163112"></a>否</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p6948124543119"><a name="p6948124543119"></a><a name="p6948124543119"></a>30</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p69487457313"><a name="p69487457313"></a><a name="p69487457313"></a>范围1~30。</p>
    </td>
    </tr>
    </tbody>
    </table>

2.  创建存储后端对应的ConfigMap资源，用于保存存储设备的管理配置信息。

    准备ConfigMap配置文件，以下以创建iSCSI协议类型的OceanStor SAN存储后端为例。其中csi.json键的值为存储后端配置的JSON格式，各配置项说明请按存储类型参考[配置存储后端](/docs/basic-services/storage-backend-management/configuring-the-storage-backend)章节。

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

    执行以下命令创建ConfigMap。

    ```
    kubectl apply -f backend-configmap.yaml
    ```

3.  创建StorageBackendClaim资源，触发CSI控制器接入存储后端，StorageBackendClaim中字段说明见[表2 StorageBackendClaim spec字段说明](#table1290132113815)。

    准备StorageBackendClaim配置文件，如backend-claim.yaml。

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

    执行以下命令创建StorageBackendClaim。

    ```
    kubectl apply -f backend-claim.yaml
    ```

    **表 2**  StorageBackendClaim spec字段说明

    <a name="table1290132113815"></a>
    <table><thead align="left"><tr id="row7105821103819"><th class="cellrowborder" valign="top" width="18%" id="mcps1.2.6.1.1"><p id="p310542119382"><a name="p310542119382"></a><a name="p310542119382"></a>参数</p>
    </th>
    <th class="cellrowborder" valign="top" width="42%" id="mcps1.2.6.1.2"><p id="p19105162163812"><a name="p19105162163812"></a><a name="p19105162163812"></a>描述</p>
    </th>
    <th class="cellrowborder" valign="top" width="10%" id="mcps1.2.6.1.3"><p id="p1810532119388"><a name="p1810532119388"></a><a name="p1810532119388"></a>必选</p>
    </th>
    <th class="cellrowborder" valign="top" width="10%" id="mcps1.2.6.1.4"><p id="p410532163812"><a name="p410532163812"></a><a name="p410532163812"></a>默认值</p>
    </th>
    <th class="cellrowborder" valign="top" width="20%" id="mcps1.2.6.1.5"><p id="p910562173818"><a name="p910562173818"></a><a name="p910562173818"></a>备注</p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row16105821183812"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p0106192119386"><a name="p0106192119386"></a><a name="p0106192119386"></a>provider</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p7106112193815"><a name="p7106112193815"></a><a name="p7106112193815"></a>供应者名称，用于匹配CSI插件。</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p51061421113818"><a name="p51061421113818"></a><a name="p51061421113818"></a>是</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p31068213389"><a name="p31068213389"></a><a name="p31068213389"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p121063215381"><a name="p121063215381"></a><a name="p121063215381"></a>固定填写：csi.huawei.com</p>
    </td>
    </tr>
    <tr id="row1210662114383"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p9106221133816"><a name="p9106221133816"></a><a name="p9106221133816"></a>configmapMeta</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p610682133812"><a name="p610682133812"></a><a name="p610682133812"></a>存储配置信息的ConfigMap引用，格式为&lt;namespace&gt;/&lt;name&gt;。</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p1510682113382"><a name="p1510682113382"></a><a name="p1510682113382"></a>是</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p71065214385"><a name="p71065214385"></a><a name="p71065214385"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p131061211387"><a name="p131061211387"></a><a name="p131061211387"></a>需与步骤2中创建的ConfigMap名称一致。</p>
    </td>
    </tr>
    <tr id="row81062021203820"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p71061821183820"><a name="p71061821183820"></a><a name="p71061821183820"></a>secretMeta</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p16106132118383"><a name="p16106132118383"></a><a name="p16106132118383"></a>存储认证信息的Secret引用，格式为&lt;namespace&gt;/&lt;name&gt;。</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p1910632114388"><a name="p1910632114388"></a><a name="p1910632114388"></a>是</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p121066211386"><a name="p121066211386"></a><a name="p121066211386"></a>-</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p310610213381"><a name="p310610213381"></a><a name="p310610213381"></a>需与步骤1中创建的Secret名称一致。</p>
    </td>
    </tr>
    <tr id="row61067217387"><td class="cellrowborder" valign="top" width="18%" headers="mcps1.2.6.1.1 "><p id="p2106621153816"><a name="p2106621153816"></a><a name="p2106621153816"></a>maxClientThreads</p>
    </td>
    <td class="cellrowborder" valign="top" width="42%" headers="mcps1.2.6.1.2 "><p id="p11060217388"><a name="p11060217388"></a><a name="p11060217388"></a>同时连接到存储后端的最大连接数。</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.3 "><p id="p81062217388"><a name="p81062217388"></a><a name="p81062217388"></a>否</p>
    </td>
    <td class="cellrowborder" valign="top" width="10%" headers="mcps1.2.6.1.4 "><p id="p16107102116381"><a name="p16107102116381"></a><a name="p16107102116381"></a>30</p>
    </td>
    <td class="cellrowborder" valign="top" width="20%" headers="mcps1.2.6.1.5 "><p id="p610762113818"><a name="p610762113818"></a><a name="p610762113818"></a>范围1~30。</p>
    </td>
    </tr>
    </tbody>
    </table>

4.  执行以下命令检查存储后端创建结果。

    ```
    kubectl get sbct
    ```

    命令结果示例如下，StorageBackendContent在线状态为true，则创建成功。

    ```
    NAME              CLAIM                       SN               VENDORNAME   PROVIDERVERSION   ONLINE   AGE
    content-xxxxxxx   huawei-csi/backend-demo     xxxxxxxxxxxxxx   Huawei       4.13.0            true     53d
    ```

