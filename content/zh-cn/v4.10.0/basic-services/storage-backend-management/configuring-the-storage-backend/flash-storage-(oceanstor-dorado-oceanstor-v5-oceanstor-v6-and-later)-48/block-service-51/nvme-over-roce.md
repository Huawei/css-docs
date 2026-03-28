---
title: "NVMe over RoCE"
linkTitle: "NVMe over RoCE"
description: 
weight: 3
---

本章节介绍创建NVMe over RoCE协议类型的存储后端

## 配置项说明{#section2854172414476}

**表 1**  backend配置项说明

<a name="table9126101819192"></a>
<table><thead align="left"><tr id="row10127131813194"><th class="cellrowborder" valign="top" width="13.266105345604077%" id="mcps1.2.6.1.1"><p id="p5631154913199"><a name="p5631154913199"></a><a name="p5631154913199"></a>参数</p>
</th>
<th class="cellrowborder" valign="top" width="37.771685921284515%" id="mcps1.2.6.1.2"><p id="p463104991916"><a name="p463104991916"></a><a name="p463104991916"></a>描述</p>
</th>
<th class="cellrowborder" valign="top" width="7.1176816134717065%" id="mcps1.2.6.1.3"><p id="p1463134917198"><a name="p1463134917198"></a><a name="p1463134917198"></a>必选参数</p>
</th>
<th class="cellrowborder" valign="top" width="6.8533385549246155%" id="mcps1.2.6.1.4"><p id="p6919415195119"><a name="p6919415195119"></a><a name="p6919415195119"></a>默认值</p>
</th>
<th class="cellrowborder" valign="top" width="34.9911885647151%" id="mcps1.2.6.1.5"><p id="p10631049171910"><a name="p10631049171910"></a><a name="p10631049171910"></a>备注</p>
</th>
</tr>
</thead>
<tbody><tr id="row111271188193"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p1233915445454"><a name="zh-cn_topic_0000001324610777_p1233915445454"></a><a name="zh-cn_topic_0000001324610777_p1233915445454"></a>storage</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p3339204417453"><a name="zh-cn_topic_0000001324610777_p3339204417453"></a><a name="zh-cn_topic_0000001324610777_p3339204417453"></a>存储服务类型。</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p533910449459"><a name="zh-cn_topic_0000001324610777_p533910449459"></a><a name="zh-cn_topic_0000001324610777_p533910449459"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p15919151545111"><a name="p15919151545111"></a><a name="p15919151545111"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001324610777_p17339174424512"><a name="zh-cn_topic_0000001324610777_p17339174424512"></a><a name="zh-cn_topic_0000001324610777_p17339174424512"></a>固定填写：oceanstor-san。</p>
</td>
</tr>
<tr id="row15127618111910"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p733904424519"><a name="zh-cn_topic_0000001324610777_p733904424519"></a><a name="zh-cn_topic_0000001324610777_p733904424519"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p23903331109"><a name="zh-cn_topic_0000001324610777_p23903331109"></a><a name="zh-cn_topic_0000001324610777_p23903331109"></a>存储后端名称。支持小写字母、数字和特殊字符"-"，且需要以字母或数字开头，最多63个字符。</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p18339944154510"><a name="zh-cn_topic_0000001324610777_p18339944154510"></a><a name="zh-cn_topic_0000001324610777_p18339944154510"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p18919015125112"><a name="p18919015125112"></a><a name="p18919015125112"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p1874481011019"><a name="p1874481011019"></a><a name="p1874481011019"></a>请保证存储后端名称唯一。</p>
</td>
</tr>
<tr id="row765135132312"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p1650357236"><a name="p1650357236"></a><a name="p1650357236"></a>namespace</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p1466335142311"><a name="p1466335142311"></a><a name="p1466335142311"></a>命名空间。</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p176653592311"><a name="p176653592311"></a><a name="p176653592311"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p391981510517"><a name="p391981510517"></a><a name="p391981510517"></a>huawei-csi</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p866103515237"><a name="p866103515237"></a><a name="p866103515237"></a>存储后端必须与华为CSI在相同的命名空间中。</p>
</td>
</tr>
<tr id="row1212714182196"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p153399449451"><a name="zh-cn_topic_0000001324610777_p153399449451"></a><a name="zh-cn_topic_0000001324610777_p153399449451"></a>urls</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p430691742216"><a name="zh-cn_topic_0000001324610777_p430691742216"></a><a name="zh-cn_topic_0000001324610777_p430691742216"></a>存储设备的管理URL。参数格式为列表。支持按照域名或者IP+端口的方式进行配置。</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p1233934484518"><a name="zh-cn_topic_0000001324610777_p1233934484518"></a><a name="zh-cn_topic_0000001324610777_p1233934484518"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p691916153512"><a name="p691916153512"></a><a name="p691916153512"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><a name="ul96961628201612"></a><a name="ul96961628201612"></a><ul id="ul96961628201612"><li>当管理URL为IPv6类型时，URL格式为：https://[IPv6地址]:端口号。</li></ul>
</td>
</tr>
<tr id="row7127101841917"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p17111241100"><a name="zh-cn_topic_0000001324610777_p17111241100"></a><a name="zh-cn_topic_0000001324610777_p17111241100"></a>pools</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p1671172411012"><a name="zh-cn_topic_0000001324610777_p1671172411012"></a><a name="zh-cn_topic_0000001324610777_p1671172411012"></a>存储设备的存储池。参数格式为列表。</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p971172414020"><a name="zh-cn_topic_0000001324610777_p971172414020"></a><a name="zh-cn_topic_0000001324610777_p971172414020"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p19191715195117"><a name="p19191715195117"></a><a name="p19191715195117"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="zh-cn_topic_0000001324610777_p117122413014"><a name="zh-cn_topic_0000001324610777_p117122413014"></a><a name="zh-cn_topic_0000001324610777_p117122413014"></a>填写存储池名称。</p>
</td>
</tr>
<tr id="row1312711851911"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p20613155814116"><a name="zh-cn_topic_0000001324610777_p20613155814116"></a><a name="zh-cn_topic_0000001324610777_p20613155814116"></a>parameters.protocol</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p12810447425"><a name="zh-cn_topic_0000001324610777_p12810447425"></a><a name="zh-cn_topic_0000001324610777_p12810447425"></a>存储协议。参数格式为字符串。</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p1261313581616"><a name="zh-cn_topic_0000001324610777_p1261313581616"></a><a name="zh-cn_topic_0000001324610777_p1261313581616"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p109191715115118"><a name="p109191715115118"></a><a name="p109191715115118"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><a name="ul555819319152"></a><a name="ul555819319152"></a><ul id="ul555819319152"><li>固定填写：roce</li><li>请确保对接的计算节点已安装nvme-cli工具，并且nvme-cli工具版本在1.9及以上。</li></ul>
</td>
</tr>
<tr id="row61271618121913"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="zh-cn_topic_0000001324610777_p12730821724"><a name="zh-cn_topic_0000001324610777_p12730821724"></a><a name="zh-cn_topic_0000001324610777_p12730821724"></a>parameters.portals</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="zh-cn_topic_0000001324610777_p127300212214"><a name="zh-cn_topic_0000001324610777_p127300212214"></a><a name="zh-cn_topic_0000001324610777_p127300212214"></a>业务访问端口。节点会使用该端口对存储资源进行读写访问。参数格式为一个列表</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="zh-cn_topic_0000001324610777_p8730621026"><a name="zh-cn_topic_0000001324610777_p8730621026"></a><a name="zh-cn_topic_0000001324610777_p8730621026"></a>是</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p15919101510519"><a name="p15919101510519"></a><a name="p15919101510519"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><a name="ul73520114122"></a><a name="ul73520114122"></a><ul id="ul73520114122"><li>支持IPv6。</li><li>支持配置多个端口</li></ul>
</td>
</tr>
<tr id="row36316121111"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p2064181219115"><a name="p2064181219115"></a><a name="p2064181219115"></a>supportedTopologies</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p18642127115"><a name="p18642127115"></a><a name="p18642127115"></a>存储拓扑感知配置。参数格式为列表类型的JSON。</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p864111251119"><a name="p864111251119"></a><a name="p864111251119"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p1191961545114"><a name="p1191961545114"></a><a name="p1191961545114"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p176418120111"><a name="p176418120111"></a><a name="p176418120111"></a>如果启用存储拓扑感知，需要配置该参数。具体请参考<a href="/css-docs/docs/common-o-m-operations/configuring-storage-topology-awareness">配置存储拓扑感知</a>。</p>
</td>
</tr>
<tr id="row11363104441311"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p0363164461310"><a name="p0363164461310"></a><a name="p0363164461310"></a>maxClientThreads</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p1236374461311"><a name="p1236374461311"></a><a name="p1236374461311"></a>同时连接到存储后端的最大连接数。</p>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p43631344161310"><a name="p43631344161310"></a><a name="p43631344161310"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p16919715145113"><a name="p16919715145113"></a><a name="p16919715145113"></a>30</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p7363204412133"><a name="p7363204412133"></a><a name="p7363204412133"></a>范围1~30，如果不配置该参数，或参数值不在规定范围内，则取用默认值30。</p>
</td>
</tr>
<tr id="row51574418229"><td class="cellrowborder" valign="top" width="13.266105345604077%" headers="mcps1.2.6.1.1 "><p id="p3158541228"><a name="p3158541228"></a><a name="p3158541228"></a>authenticationMode</p>
</td>
<td class="cellrowborder" valign="top" width="37.771685921284515%" headers="mcps1.2.6.1.2 "><p id="p31581743223"><a name="p31581743223"></a><a name="p31581743223"></a>登录存储后端的认证模式。</p>
<p id="p13386105733415"><a name="p13386105733415"></a><a name="p13386105733415"></a>支持两种模式：</p>
<a name="ul41301430359"></a><a name="ul41301430359"></a><ul id="ul41301430359"><li>local：本地认证</li><li>ldap：LDAP认证</li></ul>
</td>
<td class="cellrowborder" valign="top" width="7.1176816134717065%" headers="mcps1.2.6.1.3 "><p id="p315894172213"><a name="p315894172213"></a><a name="p315894172213"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="6.8533385549246155%" headers="mcps1.2.6.1.4 "><p id="p121587482213"><a name="p121587482213"></a><a name="p121587482213"></a>local</p>
</td>
<td class="cellrowborder" valign="top" width="34.9911885647151%" headers="mcps1.2.6.1.5 "><p id="p24702584253"><a name="p24702584253"></a><a name="p24702584253"></a>当华为企业存储为OceanStor V5时，LDAP域认证服务器ID必须为0。</p>
</td>
</tr>
</tbody>
</table>

## 创建存储后端{#section427044474916}

1.  准备后端配置文件，如backend.yaml。

    ```yaml
    storage: "oceanstor-san"
    name: "backend-demo"
    namespace: "huawei-csi"
    urls:
      - "https://192.168.129.157:8088"
    pools:
      - "StoragePool001"
    parameters:
      protocol: "roce"
      portals:
        - "10.10.30.20"
        - "10.10.30.21"
    maxClientThreads: "30"
    ```

2.  执行以下命令创建存储后端。

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml
    ```

    命令结果示例如下：

    ```
    NUMBER  CONFIGURED    NAME           STORAGE              URLS                
    1       false         backend-demo   oceanstor-san        https://192.168.129.157:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

3.  输入待创建后端序号，并输入账号密码。

    ```
    Please enter the backend number to configure (Enter 'exit' to exit):1
    Please enter this backend user name: admin
    Please enter this backend password:
    
    Backend backend-demo is configured
    NUMBER  CONFIGURED    NAME            STORAGE              URLS               
    1       true          backend-demo    oceanstor-san        https://192.168.129.157:8088 
    Please enter the backend number to configure (Enter 'exit' to exit):
    ```

4.  检查存储后端创建结果。

    ```
    oceanctl get backend
    ```

    命令结果示例如下，后端状态为Bound，则创建成功。

    ```
    NAMESPACE     NAME            PROTOCOL    STORAGETYPE      SN                    STATUS  ONLINE  URL                 
    huawei-csi    backend-demo    roce        oceanstor-san    xxxxxxxxxxxxxxxxxxxx  Bound   true    https://192.168.129.157:8088   
    ```

