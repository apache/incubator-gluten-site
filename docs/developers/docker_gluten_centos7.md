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

# To access HDFS or S3, you need to add the parameters `--enable_hdfs=ON` and `--enable_s3=ON`
# If you have the same error with issue-3283, you need to add the parameter `--compile_arrow_java=ON`
./dev/buildbundle-veloxbe.sh

# You can also build with custom profile and properties
mvn clean install -Pspark-3.5 -Dhadoop.version=3.3.3 -Pbackends-velox -Pceleborn -Puniffle -DskipTests -Dmaven.source.skip
```
