---
title: "oceanctl命令说明"
linkTitle: "oceanctl命令说明"
description: 
weight: 3
---

## 帮助说明{#section1117411442508}

-   获取oceanctl帮助说明。

    ```
    oceanctl --help
    ```

-   查看oceanctl版本号。

    ```
    oceanctl version
    ```

-   指定自定义日志文件目录，以查看oceanctl版本号为例。

    ```
    oceanctl version --log-dir=/path/to/custom
    ```

## 创建存储后端{#section68961238162410}

-   执行以下命令获取创建后端帮助。

    ```
    oceanctl create backend -h
    ```

-   执行以下命令根据指定的yaml文件创建存储后端。

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml
    ```

-   执行以下命令根据指定的json文件创建存储后端，json文件仅支持通过json格式导出huawei-csi-configmap文件。

    ```
    oceanctl create backend -f /path/to/configmap.json -i json
    ```

-   执行以下命令在指定命名空间创建一个存储后端。

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml -n <namespace>
    ```

-   执行以下命令创建存储后端，并忽略存储后端名称校验，例如大写和字符“\_”，非必要请勿使用该命令。

    ```
    oceanctl create backend -f /path/to/backend.yaml -i yaml --not-validate-name
    ```

-   执行以下命令创建存储后端，并指定provisioner，其中“csi.oceanstor.com”是安装时指定的驱动名称，详情可以参考[4](/docs/installation-and-deployment/installing-huawei-csi/installing-huawei-csi-using-helm/installing-huawei-csi-on-the-cce-or-cce-agile-platform#li4307135252018)。

    >![](/css-docs/public_sys-resources/zh-cn/icon-note.gif)  
    >仅在CCE或CCE Agile平台创建后端时使用该命令。

    ```
    oceanctl create backend -f /path/to/backend.yaml  -i yaml --provisioner=csi.oceanstor.com
    ```

## 查询存储后端{#section1746114212110}

-   执行以下命令获取查询后端帮助。

    ```
    oceanctl get backend -h
    ```

-   执行以下命令查询默认命名空间下单个存储后端。

    ```
    oceanctl get backend <backend-name>
    ```

-   执行以下命令查询指定命名空间下所有存储后端。

    ```
    oceanctl get backend -n <namespace>
    ```

-   执行以下命令格式化输出，当前支持json，yaml和wide。

    ```
    oceanctl get backend <backend-name> -o json
    ```

## 更新存储后端{#section20491912142516}

-   执行以下命令获取更新后端帮助。

    ```
    oceanctl update backend -h
    ```

-   执行以下命令更新默认命名空间下指定存储后端信息。

    ```
    oceanctl update backend <backend-name> --password
    ```

-   执行以下命令更新指定命名空间存储后端信息。

    ```
    oceanctl update backend <backend-name> -n <namespace> --password
    ```

## 删除存储后端{#section1473712371285}

-   执行以下命令获取删除后端帮助。

    ```
    oceanctl delete backend -h
    ```

-   执行以下命令删除默认命名空间下指定存储后端。

    ```
    oceanctl delete backend <backend-name> 
    ```

-   执行以下命令删除默认命名空间下所有存储后端。

    ```
    oceanctl delete backend  --all
    ```

-   执行以下命令删除指定命名空间下存储后端。

    ```
    oceanctl delete backend <backend-name...> -n <namespace>
    ```

## 创建存储后端证书{#section16801122125214}

-   执行以下命令获取查询证书帮助。

    ```
    oceanctl create cert -h
    ```

-   执行以下命令根据指定的crt证书文件为默认命名空间单个存储后端创建证书。

    ```
    oceanctl create cert <name> -f /path/to/cert.crt -b <backend-name> 
    ```

-   执行以下命令根据指定的crt证书文件为指定命名空间单个存储后端创建证书。

    ```
    oceanctl create cert <name> -f /path/to/cert.crt -b <backend-name> -n <namespace>
    ```

-   执行以下命令根据指定的pem证书文件为指定命名空间单个存储后端创建证书。

    ```
    oceanctl create cert <name> -f /path/to/cert.pem -b <backend-name> -n <namespace>
    ```

## 查询存储后端证书{#section11544144412475}

-   执行以下命令获取查询证书帮助。

    ```
    oceanctl get cert -h
    ```

-   执行以下命令查询默认命名空间指定存储后端的证书。

    ```
    oceanctl get cert -b <backend-name>
    ```

-   执行以下命令查询指定命名空间下指定存储后端的证书。

    ```
    oceanctl get cert -b <backend-name> -n <namespace>
    ```

## 更新存储后端证书{#section1215513912218}

-   执行以下命令获取更新证书帮助。

    ```
    oceanctl update cert -h
    ```

-   执行以下命令根据指定的crt证书文件为默认命名空间指定存储后端更新证书。

    ```
    oceanctl update cert -b <backend-name> -f /path/to/cert.crt
    ```

-   执行以下命令根据指定的crt证书文件为指定命名空间指定存储后端更新证书。

    ```
    oceanctl update cert -b <backend-name> -n <namespace> -f /path/to/cert.crt
    ```

-   执行以下命令根据指定的pem证书文件为指定命名空间指定存储后端更新证书。

    ```
    oceanctl update cert -b <backend-name> -n <namespace> -f /path/to/cert.pem
    ```

## 删除存储后端证书{#section1394334712223}

-   执行以下命令获取删除证书帮助。

    ```
    oceanctl delete cert -h
    ```

-   执行以下命令删除默认命名空间指定存储后端的证书。

    ```
    oceanctl delete cert -b <backend-name> 
    ```

-   执行以下命令删除指定命名空间指定存储后端的证书。

    ```
    oceanctl delete cert -b <backend-name> -n <namespace>
    ```

