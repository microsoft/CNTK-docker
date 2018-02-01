# Ubuntu 16.04
FROM ubuntu:16.04

LABEL maintainer "MICROSOFT CORPORATION" \
      com.microsoft.cntk.version="2.4"

ENV CNTK_VERSION="2.4"

RUN apt-get update && apt-get install -y --no-install-recommends \
    # General
        ca-certificates \
        wget \
        sudo \
        build-essential \
        && \
    # Clean-up
    apt-get -y autoremove \
        && \
    rm -rf /var/lib/apt/lists/*

# Get CNTK Binary Distribution
RUN CNTK_VERSION_DASHED=$(echo $CNTK_VERSION | tr . -) && \
    CNTK_SHA256="2ed7917d426025d7dd722c7d7fda5f55e6bbec7a293a3bfc4cb163c10b4b27f6" && \
    wget -q https://cntk.ai/BinaryDrop/CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-CPU-Only.tar.gz && \
    echo "$CNTK_SHA256 CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-CPU-Only.tar.gz" | sha256sum --check --strict - && \
    tar -xzf CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-CPU-Only.tar.gz && \
    rm -f CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-CPU-Only.tar.gz && \
    /bin/bash /cntk/Scripts/install/linux/install-cntk.sh --py-version 27 --docker

WORKDIR /root
