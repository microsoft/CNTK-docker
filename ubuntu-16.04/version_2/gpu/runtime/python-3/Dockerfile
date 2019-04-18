# Tag: nvidia/cuda:10.0-cudnn7-devel-ubuntu16.04
# Created: 2018-10-22T21:14:30.605789926Z
# Label: com.nvidia.cuda.version: 10.0.
# Label: com.nvidia.cudnn.version: 7.3.1.20
# Label: com.nvidia.nccl.version: 2.3.5
#
# To build, run from the parent with the command line:
# 	docker build -t <image name> -f CNTK-GPU-Image/Dockerfile .

# Ubuntu 16.04.5
FROM nvidia/cuda@sha256:362e4e25aa46a18dfa834360140e91b61cdb0a3a2796c8e09dadb268b9de3f6b

ARG CNTK_VERSION="2.7"
LABEL maintainer "MICROSOFT CORPORATION" \
      com.microsoft.cntk.version="$CNTK_VERSION"

ENV CNTK_VERSION="$CNTK_VERSION"

# Install CNTK as the default backend for Keras
ENV KERAS_BACKEND=cntk

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
    ([ "$CNTK_VERSION" != "2.4" ] || VERIFY_SHA256="true") && \
    CNTK_SHA256="a5afc9ce736b7f63b505bf4449baea6677993c1af177dd0d0c5ef8fc08fdd3f4" && \
    wget -q https://cntk.ai/BinaryDrop/CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU.tar.gz && \
    ([ "$VERIFY_SHA256" != "true" ] || (echo "$CNTK_SHA256 CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU.tar.gz" | sha256sum --check --strict -)) && \
    tar -xzf CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU.tar.gz && \
    rm -f CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU.tar.gz && \
    /bin/bash /cntk/Scripts/install/linux/install-cntk.sh --py-version 35 --docker

WORKDIR /root
