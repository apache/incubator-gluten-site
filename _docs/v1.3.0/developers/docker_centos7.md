---
layout: page
title: Docker script for CentOS 7
nav_order: 7
parent: Developers
grand_parent: v1.3.0
permalink: /archives/v1.3.0/developers/docker-centos7/
---
Here is a docker script we verified to build Gluten+Velox backend on CentOS 7:

Run on host as root user:
```bash
docker pull centos:7
docker run -itd --name gluten centos:7 /bin/bash
docker attach gluten
```

Run in docker:
```bash
yum -y install epel-release centos-release-scl
yum -y install \
    git236 \
    dnf \
    cmake3 \
    devtoolset-9 \
    java-1.8.0-openjdk \
    java-1.8.0-openjdk-devel \
    ninja-build \
    wget \
    autoconf \
    autoconf-archive \
    automake \
    perl-IPC-Cmd \
    libicu-devel \
    bison \
    libtool \
    patch \
    flex \
    sudo

# gluten need maven version >=3.6.3
wget https://downloads.apache.org/maven/maven-3/3.8.8/binaries/apache-maven-3.8.8-bin.tar.gz
tar -xvf apache-maven-3.8.8-bin.tar.gz
mv apache-maven-3.8.8 /usr/lib/maven
export MAVEN_HOME=/usr/lib/maven
export PATH=${PATH}:${MAVEN_HOME}/bin

# cmake 3.x is required
ln -s /usr/bin/cmake3 /usr/local/bin/cmake

# enable gcc 9
. /opt/rh/devtoolset-9/enable || exit 1

export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk
export PATH=$JAVA_HOME/bin:$PATH

git clone https://github.com/oap-project/gluten.git
cd gluten

# To access HDFS or S3, you need to add the parameters `--enable_hdfs=ON` and `--enable_s3=ON`
# If you have the same error with issue-3283, you need to add the parameter `--compile_arrow_java=ON`
./dev/buildbundle-veloxbe.sh
```
