---
title: "Downloading a Container Image"
linkTitle: "Downloading a Container Image"
description: 
weight: 3
---

## Downloading a Container Image Using containerd{#section15713611153419}

1.  Run the following command to download an image to a local path. In the command,  _image:tag_  indicates the image to be pulled and its tag.

    ```
    ctr image pull <image>:<tag>
    ```

2.  Run the following command to export the image to a file. In the command,  _image:tag_  indicates the image to be exported, and  _file_  indicates the name of the exported image file.

    ```
    ctr image export <file>.tar <image>:<tag>
    ```

## Downloading a Container Image Using Docker{#section5466193511236}

1.  Run the following command to download an image to a local path. In the command,  _image:tag_  indicates the image to be pulled.

    ```
    docker pull <image>:<tag>
    ```

2.  Run the following command to export the image to a file. In the command,  _image:tag_  indicates the image to be exported, and  _file_  indicates the name of the exported image file.

    ```
    docker save <image>:<tag> -o <file>.tar
    ```

## Downloading a Container Image Using Podman{#section137495322810}

1.  Run the following command to download an image to a local path. In the command,  _image:tag_  indicates the image to be pulled.

    ```
    podman pull <image>:<tag>
    ```

2.  Run the following command to export the image to a file. In the command,  _image:tag_  indicates the image to be exported, and  _file_  indicates the name of the exported image file.

    ```
    podman save <image>:<tag> -o <file>.tar 
    ```

