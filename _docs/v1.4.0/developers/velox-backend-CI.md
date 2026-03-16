---
layout: page
title: velox backend CI
nav_order: 13
parent: Developers
grand_parent: v1.4.0
---
# Velox Backend CI

GHA workflows are defined under `.github/workflows/`.

## Docker Build
We have a weekly job defined in `docker_image.yml` to build docker images based on `Dockerfile.centos7-static-build` and `Dockerfile.centos8-dynamic-build` for CI verification.

## Vcpkg Caching
Gluten main branch is pulled down during docker build. And vcpkg will cache binary data of all dependencies defined under dev/vcpkg.
These binary data is cached into `/var/cache/vcpkg` and CI job can re-use them in new build. By setting `VCPKG_BINARY_SOURCES=clear` in env.,
reusing vcpkg cache can be disabled.

## Arrow Libs Pre-installation
Arrow libs are pre-installed in docker, assuming they are not actively changed, then not necessarily to be re-built every time.

## Updating Docker Image
Two GitHub secrets `DOCKERHUB_USER` & `DOCKERHUB_TOKEN` can be used to push docker image to docker hub: https://hub.docker.com/r/apache/gluten/tags.
Note GitHub secrets are not retrievable in PR from forked repo.