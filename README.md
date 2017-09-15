**See how to use the images in [CNTK Wiki](https://docs.microsoft.com/en-us/cognitive-toolkit/CNTK-Docker-Containers).**

The following tags default to images based on ubuntu:14.04 (CPU), nvidia/cuda:8.0-runtime-ubuntu14.04 (v.2.x GPU) and nvidia/cuda:7.5-runtime (v.1.x GPU).

### Version 2 Images
#### Python 3.4 and 3.5

**GPU ([NVIDIA Docker](https://github.com/nvidia/nvidia-docker) is required)**

* `2.2-gpu-python3.5-cuda8.0-cudnn6.0`, `latest` ([/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.2/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile))
* `2.1-gpu-python3.5-cuda8.0-cudnn6.0` ([/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.1/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile))
* `2.0-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile))
* `2.0.rc3-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc3/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile))
* `2.0.rc2-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc2/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile))
* `2.0.rc1-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc1/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile))
* `2.0.beta15.0-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta15.0/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile))
* `2.0.beta12.0-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta12.0/ubuntu-14.04/version_2/gpu/runtime/python-3/Dockerfile))
* `2.0.beta11.0-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/2.0.beta11.0/gpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta11.0/ubuntu-14.04/version_2/2.0.beta11.0/gpu/runtime/Dockerfile))
* `2.0.beta10.0-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/2.0.beta10.0/gpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta10.0/ubuntu-14.04/version_2/2.0.beta10.0/gpu/runtime/Dockerfile))
* `2.0.beta9.0-runtime-gpu-python3.5-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/2.0.beta9.0/gpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta9.0/ubuntu-14.04/version_2/2.0.beta9.0/gpu/runtime/Dockerfile))
* `2.0.beta8.0-runtime-gpu-python3.4-cuda8.0-cudnn5.1`, ([/ubuntu-14.04/version_2/2.0.beta8.0/gpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta8.0/ubuntu-14.04/version_2/2.0.beta8.0/gpu/runtime/Dockerfile))
* `2.0.beta7.0-runtime-gpu-python3.4-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/2.0.beta7.0-Ubuntu14/gpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta7.0-Ubuntu14/ubuntu-14.04/version_2/2.0.beta7.0/gpu/runtime/Dockerfile))

**CPU**

* `2.2-cpu-python3.5` ([/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.2/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile))
* `2.1-cpu-python3.5` ([/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.1/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile))
* `2.0-cpu-python3.5` ([/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile))
* `2.0.rc3-cpu-python3.5` ([/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc3/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile))
* `2.0.rc2-cpu-python3.5` ([/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc2/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile))
* `2.0.rc1-cpu-python3.5` ([/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc1/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile))
* `2.0.beta15.0-cpu-python3.5` ([/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta15.0/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile))
* `2.0.beta12.0-cpu-python3.5` ([/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta12.0/ubuntu-14.04/version_2/cpu/runtime/python-3/Dockerfile))
* `2.0.beta11.0-cpu-python3.5` ([/ubuntu-14.04/version_2/2.0.beta11.0/cpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta11.0/ubuntu-14.04/version_2/2.0.beta11.0/cpu/runtime/Dockerfile))
* `2.0.beta10.0-cpu-python3.5` ([/ubuntu-14.04/version_2/2.0.beta10.0/cpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta10.0/ubuntu-14.04/version_2/2.0.beta10.0/cpu/runtime/Dockerfile))
* `2.0.beta9.0-runtime-cpu-python3.5` ([/ubuntu-14.04/version_2/2.0.beta9.0/cpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta9.0/ubuntu-14.04/version_2/2.0.beta9.0/cpu/runtime/Dockerfile))
* `2.0.beta8.0-runtime-cpu-python3.4` ([/ubuntu-14.04/version_2/2.0.beta8.0/cpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta8.0/ubuntu-14.04/version_2/2.0.beta8.0/cpu/runtime/Dockerfile))
* `2.0.beta7.0-runtime-cpu-python3.4` ([/ubuntu-14.04/version_2/2.0.beta7.0/cpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta7.0/ubuntu-14.04/version_2/2.0.beta7.0/cpu/runtime/Dockerfile))

#### Python 2.7

**GPU ([NVIDIA Docker](https://github.com/nvidia/nvidia-docker) is required)**

* `2.2-gpu-python2.7-cuda8.0-cudnn6.0` ([/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.2/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile))
* `2.1-gpu-python2.7-cuda8.0-cudnn6.0` ([/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.1/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile))
* `2.0-gpu-python2.7-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile))
* `2.0.rc3-gpu-python2.7-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc3/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile))
* `2.0.rc2-gpu-python2.7-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc2/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile))
* `2.0.rc1-gpu-python2.7-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc1/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile))
* `2.0.beta15.0-gpu-python2.7-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta15.0/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile))
* `2.0.beta12.0-gpu-python2.7-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta12.0/ubuntu-14.04/version_2/gpu/runtime/python-2/Dockerfile))
* `2.0.beta11.0-gpu-python2.7-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/2.0.beta11.0/gpu/runtime/python-2.7/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta11.0/ubuntu-14.04/version_2/2.0.beta11.0/gpu/runtime/python-2.7/Dockerfile))
* `2.0.beta10.0-gpu-python2.7-cuda8.0-cudnn5.1` ([/ubuntu-14.04/version_2/2.0.beta10.0/gpu/runtime/python-2.7/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta10.0/ubuntu-14.04/version_2/2.0.beta10.0/gpu/runtime/python-2.7/Dockerfile))

**CPU**

* `2.2-cpu-python2.7` ([/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.2/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile))
* `2.1-cpu-python2.7` ([/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.1/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile))
* `2.0-cpu-python2.7` ([/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile))
* `2.0.rc3-cpu-python2.7` ([/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc3/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile))
* `2.0.rc2-cpu-python2.7` ([/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc2/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile))
* `2.0.rc1-cpu-python2.7` ([/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.rc1/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile))
* `2.0.beta15.0-cpu-python2.7` ([/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta15.0/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile))
* `2.0.beta12.0-cpu-python2.7` ([/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta12.0/ubuntu-14.04/version_2/cpu/runtime/python-2/Dockerfile))
* `2.0.beta11.0-cpu-python2.7` ([/ubuntu-14.04/version_2/2.0.beta11.0/cpu/runtime/python-2.7/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta11.0/ubuntu-14.04/version_2/2.0.beta11.0/cpu/runtime/python-2.7/Dockerfile))
* `2.0.beta10.0-cpu-python2.7` ([/ubuntu-14.04/version_2/2.0.beta10.0/cpu/runtime/python-2.7/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/v2.0.beta10.0/ubuntu-14.04/version_2/2.0.beta10.0/cpu/runtime/python-2.7/Dockerfile))

### Version 1 Images

**GPU ([NVIDIA Docker](https://github.com/nvidia/nvidia-docker) is required)**

* `1.7.2-runtime-gpu-cuda7.5-cudnn5.1` ([/ubuntu-14.04/version_1/1.7.2/gpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/master/ubuntu-14.04/version_1/1.7.2/gpu/runtime/Dockerfile))

**CPU**

* `1.7.2-runtime-cpu` ([/ubuntu-14.04/version_1/1.7.2/cpu/runtime/Dockerfile](https://github.com/Microsoft/CNTK-docker/blob/master/ubuntu-14.04/version_1/1.7.2/cpu/runtime/Dockerfile))

**[How to locate CNTK Docker Images Sources](https://github.com/Microsoft/CNTK-docker/blob/master/README-Docker-Source-Location.md)**

**[CNTK Homepage](https://cntk.ai)**  
**[CNTK Source Code at GitHub](https://github.com/microsoft/cntk)**  
**[CNTK Wiki](https://docs.microsoft.com/en-gb/cognitive-toolkit/)**
