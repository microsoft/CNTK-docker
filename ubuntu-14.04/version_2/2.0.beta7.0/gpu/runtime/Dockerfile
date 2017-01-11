# Ubuntu 14.04, CUDA 8.0
FROM nvidia/cuda:8.0-runtime
# FROM nvidia/cuda:7.5-runtime

LABEL maintainer "MICROSOFT CORPORATION"
LABEL com.microsoft.cntk.version="2.0.beta7.0"

ENV CNTK_VERSION="2.0.beta7.0"

RUN apt-get update && apt-get install -y --no-install-recommends \
    # General
        ca-certificates \
        wget \
    # For Open MPI
        gcc \
        g++ \
        make \
    # For Image Reader
        libjasper1 \
        libjpeg8 \
        libpng12-0 \
    # For Kaldi Reader
        libgfortran3 \
        && \
    rm -rf /var/lib/apt/lists/*

# Install Open MPI
RUN OPENMPI_VERSION="1.10.4" && \
    OPENMPI_SHA1="84d035e7ab1572e5ebc086049f05b694d2158844" && \
    wget -q https://www.open-mpi.org/software/ompi/v1.10/downloads/openmpi-${OPENMPI_VERSION}.tar.gz && \
    echo "$OPENMPI_SHA1 openmpi-${OPENMPI_VERSION}.tar.gz" | sha1sum --check --strict - && \
    tar -xzf openmpi-${OPENMPI_VERSION}.tar.gz && \
    cd openmpi-${OPENMPI_VERSION} && \
    ./configure --prefix=/usr/local/mpi && \
    make -j"$(nproc)" install && \
    cd .. && \
    rm -rf /openmpi-${OPENMPI_VERSION} && \
    rm -rf openmpi-${OPENMPI_VERSION}.tar.gz

ENV PATH=/usr/local/mpi/bin:$PATH \
    LD_LIBRARY_PATH=/usr/local/mpi/lib:$LD_LIBRARY_PATH

# Install Anaconda
RUN ANACONDA_PREFIX="/root/anaconda3" && \
    ANACONDA_VERSION="3-4.1.1" && \
    ANACONDA_MD5="d0dc08d241f83ffc763504db50008e5b" && \
    wget -q https://repo.continuum.io/archive/Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh && \
    echo "$ANACONDA_MD5 Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh" | md5sum --check --strict - && \
    chmod a+x ./Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh && \
    ./Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh -b -p ${ANACONDA_PREFIX} && \
    rm -rf /Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh 

# Get CNTK Binary Distribution
RUN CNTK_VERSION_DASHED=$(echo $CNTK_VERSION | tr . -) && \
    CNTK_SHA256="5e8ed1dfeee828ed84f9bdd29a3682c396eb92e3fb6b78afe6d6a2d7e51f9ca9" && \
    wget -q https://cntk.ai/BinaryDrop/CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU.tar.gz && \
    echo "$CNTK_SHA256 CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU.tar.gz" | sha256sum --check --strict - && \
    tar -xzf CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU.tar.gz && \
    rm -f CNTK-${CNTK_VERSION_DASHED}-Linux-64bit-GPU.tar.gz

ENV PATH=/cntk/cntk/bin:$PATH \
    LD_LIBRARY_PATH=/cntk/cntk/lib:/cntk/cntk/dependencies/lib:$LD_LIBRARY_PATH

# Copy Anaconda setup script
# TODO. Implement via modifying Binary Drop package
COPY install-cntk-docker.sh /cntk/Scripts/install/linux

# Set up Anaconda environment
RUN cd /cntk/Scripts/install/linux && \
    /bin/bash -c ./install-cntk-docker.sh

# Clean-up
RUN apt-get update && apt-get -y autoremove \
        && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /root
