---
title: "通信矩阵"
linkTitle: "通信矩阵"
description: 
weight: 4
---

<a name="table931616272414"></a>
<table><tbody><tr id="row1033919211246"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.1.1"><p id="p1534019252410"><a name="p1534019252410"></a><a name="p1534019252410"></a>源设备</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.1.1 "><p id="p134072132418"><a name="p134072132418"></a><a name="p134072132418"></a>CSI controller所在主机</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.1.1 "><p id="p183401228246"><a name="p183401228246"></a><a name="p183401228246"></a>CSI controller所在主机</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.1.1 "><p id="p734062102415"><a name="p734062102415"></a><a name="p734062102415"></a>CSI node所在主机</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.1.1 "><p id="p0340172202413"><a name="p0340172202413"></a><a name="p0340172202413"></a>Kubernetes master节点</p>
</td>
</tr>
<tr id="row834018219248"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.2.1"><p id="p1734017232418"><a name="p1734017232418"></a><a name="p1734017232418"></a>源IP</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.2.1 "><p id="p53408272410"><a name="p53408272410"></a><a name="p53408272410"></a>源设备IP</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.2.1 "><p id="p8340182132418"><a name="p8340182132418"></a><a name="p8340182132418"></a>源设备IP</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.2.1 "><p id="p534022112415"><a name="p534022112415"></a><a name="p534022112415"></a>源设备IP</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.2.1 "><p id="p1734019232412"><a name="p1734019232412"></a><a name="p1734019232412"></a>源设备IP</p>
</td>
</tr>
<tr id="row103402211246"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.3.1"><p id="p133401723243"><a name="p133401723243"></a><a name="p133401723243"></a>源端口</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.3.1 "><p id="p534092102412"><a name="p534092102412"></a><a name="p534092102412"></a>1024~65536</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.3.1 "><p id="p153400219247"><a name="p153400219247"></a><a name="p153400219247"></a>1024~65536</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.3.1 "><p id="p113405292411"><a name="p113405292411"></a><a name="p113405292411"></a>1024~65536</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.3.1 "><p id="p9340627246"><a name="p9340627246"></a><a name="p9340627246"></a>1024~65536</p>
</td>
</tr>
<tr id="row113406218243"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.4.1"><p id="p103401029247"><a name="p103401029247"></a><a name="p103401029247"></a>目的设备</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.4.1 "><p id="p434042132415"><a name="p434042132415"></a><a name="p434042132415"></a>存储设备</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.4.1 "><p id="p73407262411"><a name="p73407262411"></a><a name="p73407262411"></a>CSI controller所在主机</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.4.1 "><p id="p183409242413"><a name="p183409242413"></a><a name="p183409242413"></a>CSI node所在主机</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.4.1 "><p id="p19340192142412"><a name="p19340192142412"></a><a name="p19340192142412"></a>CSI controller所在主机</p>
</td>
</tr>
<tr id="row6340192192415"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.5.1"><p id="p53401023247"><a name="p53401023247"></a><a name="p53401023247"></a>目的IP</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.5.1 "><p id="p3340022246"><a name="p3340022246"></a><a name="p3340022246"></a>存储阵列管理IP</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.5.1 "><p id="p4340182122416"><a name="p4340182122416"></a><a name="p4340182122416"></a>目的设备IP</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.5.1 "><p id="p734072112413"><a name="p734072112413"></a><a name="p734072112413"></a>目的设备IP</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.5.1 "><p id="p183401925247"><a name="p183401925247"></a><a name="p183401925247"></a>目的设备IP</p>
</td>
</tr>
<tr id="row123406212248"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.6.1"><p id="p1234115272416"><a name="p1234115272416"></a><a name="p1234115272416"></a>目的端口（监听）</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.6.1 "><p id="p9341328241"><a name="p9341328241"></a><a name="p9341328241"></a>8088</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.6.1 "><p id="p16341142112415"><a name="p16341142112415"></a><a name="p16341142112415"></a>9808</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.6.1 "><p id="p103411252414"><a name="p103411252414"></a><a name="p103411252414"></a>9800</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.6.1 "><p id="p13341102192411"><a name="p13341102192411"></a><a name="p13341102192411"></a>4433</p>
</td>
</tr>
<tr id="row183411824247"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.7.1"><p id="p33419217249"><a name="p33419217249"></a><a name="p33419217249"></a>协议</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.7.1 "><p id="p1634110252416"><a name="p1634110252416"></a><a name="p1634110252416"></a>TCP</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.7.1 "><p id="p4341024247"><a name="p4341024247"></a><a name="p4341024247"></a>TCP</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.7.1 "><p id="p2341927247"><a name="p2341927247"></a><a name="p2341927247"></a>TCP</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.7.1 "><p id="p9341142112417"><a name="p9341142112417"></a><a name="p9341142112417"></a>TCP</p>
</td>
</tr>
<tr id="row103411525246"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.8.1"><p id="p63418222413"><a name="p63418222413"></a><a name="p63418222413"></a>端口说明</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.8.1 "><p id="p11341102152414"><a name="p11341102152414"></a><a name="p11341102152414"></a>用于卷创建/管理/删除等一系列动作</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.8.1 "><p id="p03411626243"><a name="p03411626243"></a><a name="p03411626243"></a>用于Kubernetes对CSI controller的健康检查</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.8.1 "><p id="p12341323241"><a name="p12341323241"></a><a name="p12341323241"></a>用于Kubernetes对CSI node的健康检查</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.8.1 "><p id="p2034102162417"><a name="p2034102162417"></a><a name="p2034102162417"></a>用于调用webhook校验</p>
</td>
</tr>
<tr id="row123416216249"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.9.1"><p id="p173416282418"><a name="p173416282418"></a><a name="p173416282418"></a>监听端口是否可更改</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.9.1 "><p id="p123416213245"><a name="p123416213245"></a><a name="p123416213245"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.9.1 "><p id="p1434120210249"><a name="p1434120210249"></a><a name="p1434120210249"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.9.1 "><p id="p163411528242"><a name="p163411528242"></a><a name="p163411528242"></a>否</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.9.1 "><p id="p123411721243"><a name="p123411721243"></a><a name="p123411721243"></a>是</p>
</td>
</tr>
<tr id="row133411927244"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.10.1"><p id="p334122142411"><a name="p334122142411"></a><a name="p334122142411"></a>认证方式</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.10.1 "><p id="p23416216248"><a name="p23416216248"></a><a name="p23416216248"></a>用户名/密码</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.10.1 "><p id="p9341162152415"><a name="p9341162152415"></a><a name="p9341162152415"></a>证书认证</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.10.1 "><p id="p9341102142410"><a name="p9341102142410"></a><a name="p9341102142410"></a>证书认证</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.10.1 "><p id="p203415213245"><a name="p203415213245"></a><a name="p203415213245"></a>证书认证</p>
</td>
</tr>
<tr id="row5341162172415"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.11.1"><p id="p1341420248"><a name="p1341420248"></a><a name="p1341420248"></a>加密方式</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.11.1 "><p id="p334152152416"><a name="p334152152416"></a><a name="p334152152416"></a>TLS 1.3/TLS 1.2</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.11.1 "><p id="p63411827245"><a name="p63411827245"></a><a name="p63411827245"></a>TLS 1.3/TLS 1.2</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.11.1 "><p id="p1134114215242"><a name="p1134114215242"></a><a name="p1134114215242"></a>TLS 1.3/TLS 1.2</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.11.1 "><p id="p8341428243"><a name="p8341428243"></a><a name="p8341428243"></a>TLS 1.3/TLS 1.2</p>
</td>
</tr>
<tr id="row20341202142416"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.12.1"><p id="p234115211248"><a name="p234115211248"></a><a name="p234115211248"></a>所属平面</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.12.1 "><p id="p83419292419"><a name="p83419292419"></a><a name="p83419292419"></a>OM</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.12.1 "><p id="p934110222419"><a name="p934110222419"></a><a name="p934110222419"></a>运维面</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.12.1 "><p id="p73411721248"><a name="p73411721248"></a><a name="p73411721248"></a>运维面</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.12.1 "><p id="p153412232414"><a name="p153412232414"></a><a name="p153412232414"></a>运维面</p>
</td>
</tr>
<tr id="row143419242410"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.13.1"><p id="p434122182418"><a name="p434122182418"></a><a name="p434122182418"></a>特殊场景</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.13.1 "><p id="p113415212413"><a name="p113415212413"></a><a name="p113415212413"></a>无</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.13.1 "><p id="p1734172132413"><a name="p1734172132413"></a><a name="p1734172132413"></a>无</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.13.1 "><p id="p103413215245"><a name="p103413215245"></a><a name="p103413215245"></a>无</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.13.1 "><p id="p23411216247"><a name="p23411216247"></a><a name="p23411216247"></a>无</p>
</td>
</tr>
<tr id="row103416216249"><th class="firstcol" valign="top" width="19.958004199580042%" id="mcps1.1.6.14.1"><p id="p534115216245"><a name="p534115216245"></a><a name="p534115216245"></a>备注</p>
</th>
<td class="cellrowborder" valign="top" width="16.98830116988301%" headers="mcps1.1.6.14.1 "><p id="p834114216248"><a name="p834114216248"></a><a name="p834114216248"></a>源端口部分放开即可</p>
</td>
<td class="cellrowborder" valign="top" width="21.657834216578344%" headers="mcps1.1.6.14.1 "><p id="p73411227241"><a name="p73411227241"></a><a name="p73411227241"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="21.01789821017898%" headers="mcps1.1.6.14.1 "><p id="p1834172102410"><a name="p1834172102410"></a><a name="p1834172102410"></a>-</p>
</td>
<td class="cellrowborder" valign="top" width="20.377962203779624%" headers="mcps1.1.6.14.1 "><p id="p183414219248"><a name="p183414219248"></a><a name="p183414219248"></a>可参考CSI用户指南修改webhook端口</p>
</td>
</tr>
</tbody>
</table>

