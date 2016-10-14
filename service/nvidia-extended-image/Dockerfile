FROM nvidia/cuda:7.5-cudnn5-devel

# Environment variables
ENV CUB_VERSIONS="1.4.1 1.5.2" \
    STAGE_DIR=/root/gpu/install \
    CUDNN_DIR=/usr/local/cudnn \
    CUDA_DIR=/usr/local/cuda-7.5

RUN mkdir -p $STAGE_DIR

RUN apt-get -y update && \
    apt-get -y install build-essential wget

# To be able to build and run *all* samples as well as fix CUDA install warnings
# you also need these packages installed, which is *not* going to be done by default
# RUN apt-get -y update && apt-get -y install freeglut3-dev libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev

WORKDIR $STAGE_DIR

##################### NVIDIA CUB #####################

# Not creating link as CNTK uses particular version of CUB and needs to be tested with every new one.
RUN for CUB_VERSION in $CUB_VERSIONS; do \
      CUB_STRING=cub-$CUB_VERSION; \
      wget -O - --no-verbose https://github.com/NVlabs/cub/archive/$CUB_VERSION.tar.gz | tar -xzf - -C /usr/local; \
      test -f /usr/local/$CUB_STRING/cub/cub.cuh; \
    done

##################### SETUP NVIDIA DIRS FOR CNTK #####################

RUN mkdir -p ${CUDNN_DIR}/cuda/include && \
    ln -s /usr/include/cudnn.h ${CUDNN_DIR}/cuda/include/cudnn.h && \
    mkdir -p ${CUDNN_DIR}/cuda/lib64 && \
    ln -s /etc/alternatives/libcudnn_so ${CUDNN_DIR}/cuda/lib64/libcudnn.so

##################### NVIDIA Samples #####################

# Make and Run the CUDA deviceQuery sample
RUN apt-get -y update && apt-get install -y --force-yes --no-install-recommends \
        cuda-samples-$CUDA_PKG_VERSION && \
    rm -rf /var/lib/apt/lists/*
WORKDIR /usr/local/cuda/samples/1_Utilities/deviceQuery
RUN make
CMD ./deviceQuery
WORKDIR /root/
