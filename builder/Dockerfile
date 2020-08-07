# syntax = docker/dockerfile:experimental

FROM ubuntu:20.04

MAINTAINER Vladimir Rapatskiy <rapatsky@gmail.com>

WORKDIR /tmp

ENV TZ=Europe/Moscow

RUN \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ >/etc/timezone && \
    apt -q update && \
    apt -yq upgrade && \
    apt install -yq --no-install-recommends \
        build-essential \
        ca-certificates \
        ccache \
        cmake \
        curl \
        debhelper \
        devscripts \
        equivs \
        g++ \
        git \
        git-buildpackage \
        lld \
        nano \
        ninja-build \
        zstd && \
    rm /var/lib/apt/lists/*_*

ENV PATH="/usr/lib/ccache:$PATH"
ENV CCACHE_DIR="/var/ccache"
ENV CC="gcc"
ENV CXX="g++"
ENV CFLAGS="-march=skylake"
ENV CXXFLAGS="$CFLAGS"
ENV LDFLAGS="-fuse-ld=lld"
