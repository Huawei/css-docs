---
title: "配置存储后端"
linkTitle: "配置存储后端"
description: 
weight: 1
---

>![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
>1.  使用oceanctl创建存储后端时，输入的账号和秘钥信息保存在[Secret](https://kubernetes.io/zh-cn/docs/concepts/configuration/secret/)对象中，建议客户容器平台根据供应商或者K8s社区的建议自行对Secret进行加密。K8s社区对Secret加密可参考[静态加密机密数据](https://kubernetes.io/zh-cn/docs/tasks/administer-cluster/encrypt-data/)。
>2.  通过json文件创建后端时，旧版本的backend名称中可能存在大写字母或"\_"字符。如果出现这种情况，旧的名称将会被重映射为一个新的名称，映射过程自动发生，不会影响原有功能。例如“ABC\_123”将会被映射为“abc-123-fd68e”，具体映射规则如下：
>    -   大写字母转换成小写字母。
>    -   "\_"字符转换成“-”字符。
>    -   末尾追加5位Hash码。
>3.  当存储后端对接租户时，在存储后端创建完成后，不允许修改租户名称。






