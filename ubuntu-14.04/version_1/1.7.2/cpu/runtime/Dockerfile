# Ubuntu 14.04
FROM ubuntu:14.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    # General and Python
        ca-certificates \
        libjasper-runtime \
        python-dev \
        python-numpy \
        python-pip \
        python-yaml \
        wget \
    # For Open MPI
        gcc \
        g++ \
        make \
    # For scipy
        gfortran \
        libatlas-base-dev \
        libblas-dev \
        liblapack-dev \
    # For Pillow
        libfreetype6 \
        libfreetype6-dev \
        libjpeg62-dev \
        libjpeg8 \
        && \
        apt-get build-dep -y --no-install-recommends \
        python-imaging \
        && \
    rm -rf /var/lib/apt/lists/*

# Install Pillow and scipy
RUN pip install Pillow scipy && rm -rf /root/.cache/pip

# Install Open MPI
RUN OPENMPI_VERSION=1.10.3 && \
    wget -q -O - https://www.open-mpi.org/software/ompi/v1.10/downloads/openmpi-${OPENMPI_VERSION}.tar.gz | tar -xzf - && \
    cd openmpi-${OPENMPI_VERSION} && \
    ./configure --prefix=/usr/local/mpi && \
    make -j"$(nproc)" install && \
    rm -rf /openmpi-${OPENMPI_VERSION}

ENV PATH /usr/local/mpi/bin:$PATH
ENV LD_LIBRARY_PATH /usr/local/mpi/lib:$LD_LIBRARY_PATH

# Get CNTK Binary Distribution
RUN CNTK_VERSION=1-7-2 && \
    wget -q -O - https://cntk.ai/BinaryDrop/CNTK-${CNTK_VERSION}-Linux-64bit-CPU-Only.tar.gz | tar -xzf -

ENV PATH /cntk/cntk/bin:$PATH
ENV LD_LIBRARY_PATH /cntk/cntk/lib:/cntk/cntk/dependencies/lib:$LD_LIBRARY_PATH

# Clean-up
RUN apt-get update && apt-get -y autoremove \
        && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /cntk
