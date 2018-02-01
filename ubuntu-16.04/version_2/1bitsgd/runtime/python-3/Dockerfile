# Ubuntu 16.04, CUDA 9.0
FROM nvidia/cuda:9.0-runtime-ubuntu16.04

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
    CNTK_SHA256="fa65f4a03b8350b6968ffeea0de28f4081057dfd489d04151a6ccb7510bf292e" && \
    wget -q https://cntk.ai/BinaryDrop/CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU-1bit-SGD.tar.gz && \
    echo "$CNTK_SHA256 CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU-1bit-SGD.tar.gz" | sha256sum --check --strict - && \
    tar -xzf CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU-1bit-SGD.tar.gz && \
    rm -f CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU-1bit-SGD.tar.gz && \
    /bin/bash /cntk/Scripts/install/linux/install-cntk.sh --py-version 35 --docker

WORKDIR /root
