---
layout: page
title: Docker script for Pre-build CentOS 7
nav_order: 7
parent: Developers
grand_parent: Documentations
permalink: /docs/developers/docker-gluten-centos7/
---
Here is a docker script we verified to build Gluten+Velox backend on Pre-build CentOS 7:

Run on host as root user:
```bash
docker pull apache/gluten:vcpkg-centos-7
docker run -itd --name gluten-centos-7 apache/gluten:vcpkg-centos-7 /bin/bash
docker attach gluten
```

Run in docker:
```bash
git clone https://github.com/apache/incubator-gluten.git gluten
cd gluten

bash dev/ci-velox-buildstatic-centos-7.sh
mvn clean install -Pspark-3.5 -Dhadoop.version=3.3.3 -Pbackends-velox -Pceleborn -Puniffle -DskipTests -Dmaven.source.skip
```
