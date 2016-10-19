FROM microsoft/cntk:base-image

ENV SCIPY_VERSION="0.18.0"

RUN apt-get -y update && \
    apt-get -y install \
      libjasper-dev \
      libjpeg-dev \
      libpng-dev \
      libtiff-dev
    
RUN pip install pytest sphinx-rtd-theme Pillow

##################### SCIPY #####################

RUN wget -q -O - https://github.com/scipy/scipy/releases/download/v${SCIPY_VERSION}/scipy-${SCIPY_VERSION}.tar.gz | tar -zxf - && \
    cd scipy-${SCIPY_VERSION} && \
    python setup.py build && \
    python setup.py install && \
    cd .. && \
    rm -rf scipy-${SCIPY_VERSION}

##################### SETUP CNTK #####################

WORKDIR /cntk

RUN git clone --depth=1 -b master https://github.com/Microsoft/CNTK.git . && \
    CONFIGURE_OPTS="\
      --with-cuda=/usr/local/cuda \
      --with-gdk-include=/usr/local/cuda/include \
      --with-gdk-nvml-lib=/usr/local/cuda/lib64/stubs \
      --with-kaldi=${KALDI_PATH} \
      --with-cudnn=${CUDNN_DIR}" && \
    mkdir -p build/gpu/release && \
    cd build/gpu/release && \
    ../../../configure $CONFIGURE_OPTS --with-openblas=/usr/local/openblas && \
    make -j"$(nproc)" all && \
    cd ../../.. && \
    mkdir -p build-mkl/gpu/release && \
    cd build-mkl/gpu/release && \
    ../../../configure $CONFIGURE_OPTS --with-mkl=/usr/local/CNTKCustomMKL && \
    make -j"$(nproc)" all

RUN cd Examples/Image/Miscellaneous/CIFAR-10 && \
    python CifarDownload.py && \
    python CifarConverter.py cifar-10-batches-py && \
    cd ../../../..

RUN cd Examples/Image/MNIST/AdditionalFiles && \
    python mnist_convert.py && \
    cd ../../../..

ENV PATH=/cntk/build/gpu/release/bin:$PATH
