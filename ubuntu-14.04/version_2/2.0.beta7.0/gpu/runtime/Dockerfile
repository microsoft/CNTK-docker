# General TODO: add packages SHA

# Ubuntu 14.04, CUDA 7.5 (will be 8)
# FROM nvidia/cuda:8.0-runtime
FROM nvidia/cuda:7.5-runtime

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
ENV ANACONDA_PREFIX="/root/anaconda3"
RUN ANACONDA_VERSION="3-4.1.1" && \
    ANACONDA_MD5="d0dc08d241f83ffc763504db50008e5b" && \
    wget -q https://repo.continuum.io/archive/Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh && \
    echo "$ANACONDA_MD5 Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh" | md5sum --check --strict - && \
    chmod a+x ./Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh && \
    ./Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh -b -p ${ANACONDA_PREFIX} && \
    rm -rf /Anaconda${ANACONDA_VERSION}-Linux-x86_64.sh 

# Get CNTK Binary Distribution
RUN CNTK_VERSION="2-0-beta5-0" && \
    wget -q -O - https://cntk.ai/BinaryDrop/CNTK-${CNTK_VERSION}-Linux-64bit-GPU.tar.gz | tar -xzf -

ENV PATH=/cntk/cntk/bin:$PATH \
    LD_LIBRARY_PATH=/cntk/cntk/lib:/cntk/cntk/dependencies/lib:$LD_LIBRARY_PATH

# Set up Anaconda environment

ENV SCRIPT_DIR="/cntk/Scripts/install/linux" \
    CNTK_BIN_PATH="/cntk/cntk/bin" \
    CNTK_PY34_ENV_NAME="cntk-py34"


ENV CNTK_DISPLAY_VERSION="2.0 Beta 5" \
    CNTK_LIB_PATH="/cntk/cntk/lib" \
    CNTK_DEP_LIB_PATH="/cntk/cntk/dependencies/lib" \
    CNTK_EXAMPLES_PATH="/cntk/Examples" \
    CNTK_TUTORIALS_PATH="/cntk/Tutorials" \
    CNTK_BINARY="$CNTK_BIN_PATH/cntk" \
    CNTK_PY34_ENV_FILE="$SCRIPT_DIR/conda-linux-cntk-py34-environment.yml" \
    CNTK_WHEEL_PATH="/cntk/cntk/python/cntk-2.0.beta5.0-cp34-cp34m-linux_x86_64.whl" \
    \
    CONDA="/root/anaconda3/bin/conda" \
    PY_ACTIVATE="/root/anaconda3/bin/activate" \
    PY_DEACTIVATE="/root/anaconda3/bin/deactivate" \
    \
    CNTK_PY34_ENV_PREFIX="$ANACONDA_PREFIX/envs/$CNTK_PY34_ENV_NAME" \
    ACTIVATE_SCRIPT_NAME="activate-cntk"

RUN "$CONDA" env update --file "$CNTK_PY34_ENV_FILE" --name "$CNTK_PY34_ENV_NAME"  && \
    /bin/bash -c "source $PY_ACTIVATE $CNTK_PY34_ENV_PREFIX && \
    pip install $CNTK_WHEEL_PATH && \
    source $PY_DEACTIVATE" && \
    # Create activation script
    echo "if [ -z \"\$BASH_VERSION\" ]; then\n\
  echo Error: only Bash is supported.\n\
elif [ \"\$(basename \"\$0\" 2> /dev/null)\" == \"$ACTIVATE_SCRIPT_NAME\" ]; then\n\
  echo Error: this script is meant to be sourced. Run 'source activate-cntk'\n\
else\n\
  source \"$PY_ACTIVATE\" \"$CNTK_PY34_ENV_PREFIX\"\n\
\n\
  cat <<MESSAGE\n\
\n\
************************************************************\n\
CNTK is activated.\n\
\n\
Please checkout tutorials and examples here:\n\
  $CNTK_TUTORIALS_PATH\n\
  $CNTK_EXAMPLES_PATH\n\
\n\
To deactivate the environment run\n\
\n\
  source $PY_DEACTIVATE\n\
\n\
************************************************************\n\
MESSAGE\n\
\n\
fi\n\
" > /root/activate-cntk && \
    # Add login Welcome message
    echo "\n# CNTK Welcome Message\n\
cat <<MESSAGE\n\
\n\
************************************************************\n\
Welcome to Microsoft Cognitive Toolkit (CNTK) v. $CNTK_DISPLAY_VERSION\n\
\n\
To activate CNTK Python Environment run\n\
\n\
  source $ACTIVATE_SCRIPT_NAME\n\
\n\
Please checkout tutorials and examples here:\n\
  $CNTK_TUTORIALS_PATH\n\
  $CNTK_EXAMPLES_PATH\n\
************************************************************\n\
\n\
MESSAGE\n\
" >> /root/.bashrc

# Clean-up
# RUN apt-get update && apt-get -y autoremove \
#        && \
#    rm -rf /var/lib/apt/lists/*

WORKDIR /root
