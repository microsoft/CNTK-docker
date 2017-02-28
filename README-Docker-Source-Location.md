# How to locate CNTK Docker Images source code

This Repository contains the source code of [CNTK Official Docker Hub Images](https://hub.docker.com/r/microsoft/cntk/). This document helps navigating through the source code for different versions.

## Versions up to 2.0 Beta 11

Source code for CNTK Docker Images up to version 2.0 Beta 11 are available in `master` branch of this Repository. Each version has a dedicated folder tree. To obtain the source code go to the following paths:

* Version 1.x: [`/ubuntu-14.04/version_1/`](https://github.com/Microsoft/CNTK-docker/tree/master/ubuntu-14.04/version_1)
* Version 2.x: [`/ubuntu-14.04/version_2/`](https://github.com/Microsoft/CNTK-docker/tree/master/ubuntu-14.04/version_2)

Note that ***not*** all CNTK versions have the correspondent Docker Hub Images.

## Versions 2.0 Beta 12 and higher

Starting from version 2.0 Beta 12 we switched to *tag system*. To locate a particular release you need to checkout the tag corresponding to the version and go to the following paths:

* `/ubuntu-14.04/version_2/gpu` - GPU Versions
* `/ubuntu-14.04/version_2/cpu` - CPU-only Versions

(We do not provide hyper-links for the paths above, because these links will be tag-dependent; see example below on how to access the code)

### Example of locating the source code for a particular version

In this example we show how to locate the source code of CNTK Official Docker Images for the **version 2.0 Beta 12**.

#### GitHub Web Interface

 Select the required tag via Branch/Tag selector (top-left corner of Source web-page at GitHub). Example: to access the sources for version 2.0 Beta 12 select the tag `v2.0.beta11.0` and go to the following paths:

* [`/ubuntu-14.04/version_2/gpu`](https://github.com/Microsoft/CNTK-docker/tree/v2.0.beta12.0/ubuntu-14.04/version_2/gpu) - GPU Versions
* [`/ubuntu-14.04/version_2/cpu`](https://github.com/Microsoft/CNTK-docker/tree/v2.0.beta12.0/ubuntu-14.04/version_2/cpu) - CPU-only Versions

#### Local copy of CNTK-docker Repository

If you have cloned CNTK-docker Repository on your machine use the following git commands:

* `git tag` to display all existing tags
* `git checkout <tag_name>` to checkout a particular tag

Example: to access the sources for version 2.0 Beta 12 check-out the corresponding tag:
```
git checkout v2.0.beta12.0
```
Then go to the following paths:

* `/ubuntu-14.04/version_2/gpu` - GPU Versions
* `/ubuntu-14.04/version_2/cpu` - CPU-only Versions

## Information on CNTK

**[Main ReadMe of CNTK-docker Repository](https://github.com/Microsoft/CNTK-docker/blob/master/README.md)**

**[CNTK Homepage](https://cntk.ai)**  
**[CNTK Source Code at GitHub](https://github.com/microsoft/cntk)**  
**[CNTK Wiki](https://github.com/microsoft/cntk/wiki)**