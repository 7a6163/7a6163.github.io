+++
title = "自行升級 Docker"
template = "page.html"
date = 2021-06-27T20:09:27+08:00
[taxonomies]
tags = ["debug"]
[extra]
summary = "自行升級 Docker"
+++

最近遇到一個 Bug 實際追下去後才發現到是 AWS 提供的 docker 版本不是最新的，Docker 網站有提供編譯好的執行檔，可以直接下載覆蓋原有執行擋，爾後套件更新也會一並升上去。

```bash
$ wget https://download.docker.com/linux/static/stable/x86_64/docker-20.10.7.tgz
$ tar zxvf docker-20.10.7.tgz
$ sudo cp docker-20.10.7/docker /user/bin/docker
```
