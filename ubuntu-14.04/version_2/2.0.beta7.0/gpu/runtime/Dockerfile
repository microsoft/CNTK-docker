# General TODO: add packages SHA

# Ubuntu 14.04, CUDA 7.5
FROM nvidia/cuda:8.0-runtime

RUN apt-get update && apt-get install -y --no-install-recommends \
    # General and Python
        ca-certificates \
        wget \
    # For Open MPI
        gcc \
        g++ \
        make \
    # For Anaconda
    #    bzip2 \
    #    coreutils \
    # For Image Reader
        libjasper1 \
        libjpeg8 \
        libpng12-0 \
        && \
    rm -rf /var/lib/apt/lists/*

# Install Open MPI
RUN OPENMPI_VERSION=1.10.4 && \
    wget -q -O - https://www.open-mpi.org/software/ompi/v1.10/downloads/openmpi-${OPENMPI_VERSION}.tar.gz | tar -xzf - && \
    cd openmpi-${OPENMPI_VERSION} && \
    ./configure --prefix=/usr/local/mpi && \
    make -j"$(nproc)" install && \
    rm -rf /openmpi-${OPENMPI_VERSION}

ENV PATH /usr/local/mpi/bin:$PATH
ENV LD_LIBRARY_PATH /usr/local/mpi/lib:$LD_LIBRARY_PATH

# Install Anaconda
RUN ANACONDA_VERSION=3-4.1.1 && ANACONDA_PREFIX=/root/anaconda3 && \
    wget -q https://repo.continuum.io/archive/Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh && \
    chmod a+x ./Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh && \
    ./Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh -b -p ${ANACONDA_PREFIX} && \
    rm -rf /Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh 

# Get CNTK Binary Distribution
RUN CNTK_VERSION=2-0-beta5-0 && \
    wget -q -O - https://cntk.ai/BinaryDrop/CNTK-${CNTK_VERSION}-Linux-64bit-GPU.tar.gz | tar -xzf -

ENV PATH /cntk/cntk/bin:$PATH
ENV LD_LIBRARY_PATH /cntk/cntk/lib:/cntk/cntk/dependencies/lib:$LD_LIBRARY_PATH

# Clean-up
RUN apt-get update && apt-get -y autoremove \
        && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /cntk
