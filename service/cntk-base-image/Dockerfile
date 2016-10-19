FROM microsoft/cntk:nvidia-extended-image

ENV OPENCV_VERSION="3.1.0" \
    OPENCV_VARIANT=noCuda \
    OPENBLAS_VERSION="0.2.18" \
    KALDI_VERSION=c024e8aa \
    KALDI_PATH=/usr/local/kaldi-${KALDI_VERSION} \
    OPENMPI_VERSIONBASE=1.10 \
    LIBZIP_VERSION=1.1.2 \
    BOOST_VERSION="1_60_0" \
    STAGE_DIR=/cntk-staging

ENV OPENMPI_VERSION=${OPENMPI_VERSIONBASE}.3
ENV OPENMPI_STRING=openmpi-${OPENMPI_VERSION}

RUN apt-get -y update && \
    apt-get -y install \
      autotools-dev \
      byacc \
      libibverbs-dev \
      ibverbs-utils \
      libibmad-dev \
      libibumad-dev \
      librdmacm-dev \
      libmlx4-1 \
      unzip \
      cmake \
      libgtk2.0-dev \
      pkg-config \
      libavcodec-dev \
      libavformat-dev \
      libswscale-dev \
      libprotobuf8 \
      gdb \
      gcc \
      nano \
      vim \
      joe \
      curl \
      jq \
      gawk \
      psmisc \
      python \
      python-yaml \
      python-jinja2 \
      python-urllib3 \
      python-tz \
      python-nose \
      python-prettytable \
      python-netifaces \
      python-dev \
      python-pip \
      python-mysqldb \
      python-numpy \
      openjdk-7-jre \
      openjdk-7-jdk \
      openssh-server \
      openssh-client \
      git \
      inotify-tools \
      rsync \
      realpath \
      # Used for libzip
      zlib1g-dev \
      # Used in MVAPICH2 MPI install:
      rpm2cpio \
    # For OpenBlas
      gfortran \
      gfortran-multilib \
      liblapacke-dev \
    # perf utility dependencies
      libdw1 \
      libnuma1 \
      libunwind8 \
    # For Kaldi
      automake \
      libtool \
      autoconf \
      subversion \
      libatlas-base-dev \
    # For Kaldi's dependencies
      libapr1 libaprutil1 libltdl-dev libltdl7 libserf-1-1 libsigsegv2 libsvn1 m4 \
      && \
    pip install subprocess32

WORKDIR $STAGE_DIR

##################### BOOST #####################

RUN BOOST_DOTTED_VERSION=$(echo ${BOOST_VERSION} | tr _ .) && \
    wget -q -O - https://sourceforge.net/projects/boost/files/boost/${BOOST_DOTTED_VERSION}/boost_${BOOST_VERSION}.tar.gz/download | tar -xzf - && \
    cd boost_${BOOST_VERSION} && \
    ./bootstrap.sh --prefix=/usr/local/boost-${BOOST_DOTTED_VERSION} --with-libraries=filesystem,system,test  && \
    ./b2 -d0 -j"$(nproc)" install  && \
    rm -rf $STAGE_DIR/boost_${BOOST_VERSION}  && \
    # Sanity check:
    test -d /usr/local/$BOOST_STRING/include && \
    test -d /usr/local/$BOOST_STRING/lib

##################### OPENMPI #####################

RUN wget -q -O - https://www.open-mpi.org/software/ompi/v${OPENMPI_VERSIONBASE}/downloads/${OPENMPI_STRING}.tar.gz | tar -xzf - && \
    cd ${OPENMPI_STRING} && \
    ./configure --with-verbs --prefix=/usr/local/${OPENMPI_STRING} && \
    make -j"$(nproc)" install && \
    rm -rf $STAGE_DIR/${OPENMPI_STRING} && \
    ln -s /usr/local/${OPENMPI_STRING} /usr/local/mpi && \
    # Sanity check:
    test -f /usr/local/mpi/bin/mpic++

# Update environment variables
ENV PATH /usr/local/mpi/bin:$PATH
ENV LD_LIBRARY_PATH=/usr/local/lib:/usr/local/mpi/lib:$LD_LIBRARY_PATH

##################### LIBZIP #####################

RUN wget -q -O - http://nih.at/libzip/libzip-${LIBZIP_VERSION}.tar.gz | tar -xzf - && \
    cd libzip-${LIBZIP_VERSION} && \
    ./configure && \
    make -s -j $(nproc) all && \
    make -s install && \
    cd /root && \
    rm -rf $STAGE_DIR/libzip-${LIBZIP_VERSION}

ENV LD_LIBRARY_PATH /usr/local/lib:$LD_LIBRARY_PATH

##################### OPENCV #####################

RUN wget -q -O - https://github.com/Itseez/opencv/archive/${OPENCV_VERSION}.tar.gz | tar -xzf - && \
    cd opencv-${OPENCV_VERSION} && \
    cmake -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=/usr/local/opencv-${OPENCV_VERSION} . && \
    make -j"$(nproc)" install && \
    rm -rf $STAGE_DIR/opencv-${OPENCV_VERSION} && \
    # Sanity check:
    test -f /usr/local/opencv-${OPENCV_VERSION}/include/opencv2/opencv.hpp

##################### OPENBLAS #####################

RUN wget -q -O - https://github.com/xianyi/OpenBLAS/archive/v${OPENBLAS_VERSION}.tar.gz | tar -xzf - && \
    cd OpenBLAS-${OPENBLAS_VERSION} && \
    make -j"$(nproc)" USE_OPENMP=1 | tee make.log && \
    grep -qF 'OpenBLAS build complete. (BLAS CBLAS LAPACK LAPACKE)' make.log && \
    grep -qF 'Use OpenMP in the multithreading.' make.log && \
    make PREFIX=/usr/local/openblas install && \
    rm -rf $STAGE_DIR/OpenBLAS-${OPENBLAS_VERSION}

ENV LD_LIBRARY_PATH /usr/local/openblas/lib:$LD_LIBRARY_PATH \
    BLAS=/usr/local/openblas/lib/libopenblas.so \
    LAPACK=/usr/local/openblas/lib/libopenblas.so

##################### KALDI #####################

RUN mv /bin/sh /bin/sh.orig && \
    ln -s -f /bin/bash /bin/sh && \
    mkdir $KALDI_PATH && \
    wget --no-verbose -O - https://github.com/kaldi-asr/kaldi/archive/$KALDI_VERSION.tar.gz | tar -xzf - --strip-components=1 -C $KALDI_PATH && \
    cd $KALDI_PATH && \
    cd tools && \
    perl -pi -e 's/^# (OPENFST_VERSION = 1.4.1)$/\1/' Makefile && \
    ./extras/check_dependencies.sh && \
    make -j $(nproc) all && \
    cd ../src && \
    ./configure --openblas-root=/usr/local/openblas --shared && \
    make -j $(nproc) depend && \
    make -j $(nproc) all && \
  # Remove some unneeded stuff in $KALDI_PATH to reduce size
    find $KALDI_PATH -name '*.o' -print0 | xargs -0 rm && \
    for dir in $KALDI_PATH/src/*bin; do make -C $dir clean; done && \
    mv -f /bin/sh.orig /bin/sh

##################### CNTK #####################

# Install CNTK custom MKL, version 1
RUN mkdir /usr/local/CNTKCustomMKL && \
    wget --no-verbose -O - https://www.cntk.ai/mkl/CNTKCustomMKL-Linux-1.tgz | \
    tar -xzf - -C /usr/local/CNTKCustomMKL

# Install CNTK custom MKL, version 2
RUN wget --no-verbose -O - https://www.cntk.ai/mkl/CNTKCustomMKL-Linux-2.tgz | \
    tar -xzf - -C /usr/local/CNTKCustomMKL

RUN rmdir $STAGE_DIR
