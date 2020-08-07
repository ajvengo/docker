# syntax = docker/dockerfile:experimental

FROM ubuntu:20.04

MAINTAINER Vladimir Rapatskiy <rapatsky@gmail.com>

WORKDIR /tmp

ENV TZ=Europe/Moscow

RUN sed -i 's/archive./ru.archive./' /etc/apt/sources.list && \
    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
    echo $TZ >/etc/timezone && \
    rm -f /etc/apt/apt.conf.d/docker-clean && \
    echo 'Binary::apt::APT::Keep-Downloaded-Packages "true";' >/etc/apt/apt.conf.d/keep-cache

RUN --mount=type=cache,target=/var/cache/apt --mount=type=cache,target=/var/lib/apt \
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
        zstd

ENV PATH="/usr/lib/ccache:$PATH"
ENV CCACHE_DIR="/var/ccache"
ENV CC="gcc"
ENV CXX="g++"
ENV CFLAGS="-march=skylake"
ENV CXXFLAGS="$CFLAGS"
ENV LDFLAGS="-fuse-ld=lld"
