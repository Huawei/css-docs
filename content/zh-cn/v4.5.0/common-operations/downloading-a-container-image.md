---
title: "下载容器镜像"
linkTitle: "下载容器镜像"
description: 
weight: 3
---

## 使用containerd下载容器镜像{#section15713611153419}

1.  执行以下命令，下载镜像到本地。其中  _image:tag_  表示需要拉取的镜像及其标签。

    ```
    ctr image pull <image>:<tag>
    ```

2.  执行以下命令，导出镜像到文件。其中  _image:tag_  表示需要导出的镜像，_file_  表示镜像导出后的文件名称。

    ```
    ctr image export <file>.tar <image>:<tag>
    ```

## 使用Docker下载容器镜像{#section5466193511236}

1.  执行以下命令，下载镜像到本地。其中_image:tag_表示需要拉去的镜像。

    ```
    docker pull <image>:<tag>
    ```

2.  执行以下命令，导出镜像到文件。其中  _image:tag_  表示需要导出的镜像，_file_  表示镜像导出后的文件名称。

    ```
    docker save <image>:<tag> -o <file>.tar
    ```

## 使用Podman下载容器镜像{#section137495322810}

1.  执行以下命令，下载镜像到本地。其中_image:tag_表示需要拉去的镜像。

    ```
    podman pull <image>:<tag>
    ```

2.  执行以下命令，导出镜像到文件。其中  _image:tag_  表示需要导出的镜像，_file_  表示镜像导出后的文件名称。

    ```
    podman save <image>:<tag> -o <file>.tar 
    ```

