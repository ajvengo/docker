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
        gdebi-core \
        git \
        git-buildpackage \
        gpg \
        gpg-agent \
        lld \
        lsb-release \
        nano \
        ninja-build \
        openssh-client \
        pkg-config \
        zstd && \
    echo "deb [arch=amd64] https://apt.diamant-sk.ru/ubuntu focal main" >/etc/apt/sources.list.d/diamant.list && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0DF38BB2921381DA && \
    rm /var/lib/apt/lists/*_*

ENV PATH="/usr/lib/ccache:$PATH"
ENV CCACHE_DIR="/var/ccache"
ENV CC="gcc"
ENV CXX="g++"
ENV CFLAGS="-march=skylake"
ENV CXXFLAGS="$CFLAGS"
ENV LDFLAGS="-fuse-ld=lld"
