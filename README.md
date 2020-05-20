# Install-Packages-Jetson-ARM-Family

*** Copy Right 2020 Kevin Yu. All rights reserved.

*** Author: Kevin Yu

*** Update Time: 2020/05/19

This repo aims to give you clear instructions on how to install packages in AArch64(ARM) Platform, especially in Jetson family. All the packages have been tested on Jetson AGX Xavier and Jetson Nano.

*** Notes: the instructions below are for manual installation. For auto installation, you may find the installation script [HERE](https://github.com/yqlbu/jetson-install)

## Dependencies Installation
Before performing any installation, you may need to install the following basic dependencies.
```shell script
$ sudo apt-get install -y nano curl 
$ sudo apt-get install -y python3-pip python3-dev
$ sudo apt-get install -y python-pip
$ sudo apt-get install -y python-setuptools
$ sudo apt-get install -y python3-setuptools
$ sudo apt-get install -y python3-opencv
$ sudo apt-get install -y libcanberra-gtk0 libcanberra-gtk-module
```

Table of Contents
-----------------

* [Pytorch](#pytorch)
* [Tensorflow](#tensorflow)
* [LLVM](#llvm)
* [Numba](#numba)
* [ONNX](#onnx)
* [Jetson-stats](#jetson-stats)
* [VSCode](#vs-code-for-aarch64)
* [Archiconda3](#archiconda3)
* [OpenCV](#opencv)
* [Pycharm](#pycharm)
* [Docker](#docker)

Pytorch
-------

PyTorch v1.4.0 (JetPack 4.2 / 4.3)


Python 3.6 - torch-1.4.0-cp36-cp36m-linux_aarch64.whl

```shell script
$ wget https://nvidia.box.com/shared/static/ncgzus5o23uck9i5oth2n8n06k340l6k.whl -O torch-1.4.0-cp36-cp36m-linux_aarch64.whl
$ sudo apt-get install python3-pip libopenblas-base libopenmpi-dev 
$ pip3 install Cython
$ pip3 install numpy torch-1.4.0-cp36-cp36m-linux_aarch64.whl
```

Torchvision v0.5.0 (compatible with PyTorch v1.4.0)

```shell script
$ sudo apt-get install libjpeg-dev zlib1g-dev
$ git clone --branch v0.5.0 https://github.com/pytorch/vision torchvision
$ cd torchvision
$ sudo python setup.py install
$ cd ../
$ pip install 'pillow<7' # not needed for torchvision v0.5.0+
```

Verfication

```shell script
$ python3
>> import torch
>> print(torch.__version__)
```

To install other versions of PyTorch and Torchvision, please visit site [HERE](https://forums.developer.nvidia.com/t/pytorch-for-jetson-nano-version-1-5-0-now-available/72048)

<a name="pytorch"></a>

Tensorflow
----------

Python 3.6 + JetPack4.4

```shell script
sudo apt-get install libhdf5-serial-dev hdf5-tools libhdf5-dev zlib1g-dev zip libjpeg8-dev liblapack-dev libblas-dev gfortran
sudo apt-get install python3-pip
sudo pip3 install -U pip
sudo pip3 install -U pip testresources setuptools numpy==1.16.1 future==0.17.1 mock==3.0.5 h5py==2.9.0 keras_preprocessing==1.0.5 keras_applications==1.0.8 gast==0.2.2 futures protobuf pybind11
# TF-2.x
$ sudo pip3 install --pre --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v44 tensorflow
# TF-1.15
$ sudo pip3 install --pre --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v44 ‘tensorflow<2’
```

Python 3.6 + JetPack4.3

```shell script
$ sudo apt-get install libhdf5-serial-dev hdf5-tools libhdf5-dev zlib1g-dev zip libjpeg8-dev
$ sudo apt-get install python3-pip
$ sudo pip3 install -U pip
$ sudo pip3 install -U numpy grpcio absl-py py-cpuinfo psutil portpicker six mock requests gast h5py astor termcolor protobuf keras-applications keras-preprocessing wrapt google-pasta
# TF-2.x
$ sudo pip3 install --pre --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v43 tensorflow==2.1.0+nv20.3
# TF-1.15
$ sudo pip3 install --pre --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v43 tensorflow==1.15.2+nv20.3
```

To install other versions of Tensorflow, checkout the sites below:  

Jetson Xavier: [HERE](https://forums.developer.nvidia.com/t/official-tensorflow-for-jetson-agx-xavier/65523)

Jetson Nano: [HERE](https://forums.developer.nvidia.com/t/official-tensorflow-for-jetson-nano/71770)

<a name="tensorflow"></a>

LLVM
----

LLVM v3.9 (Python3.6 + JetPack 4.3/4.4)

```shell script
$ sudo apt-get install llvm-3.9
$ export LLVM_CONFIG=/usr/lib/llvm-3.9/bin/llvm-config
$ cd ~
$ wget https://github.com/numba/llvmlite/archive/v0.16.0.zip
$ unzip v0.16.0.zip
$ cd llvmlite-0.16.0
$ sudo chmod 777 -R /usr/local/lib/python3.6/dist-packages/
$ python3 setup.py install
```

<a name="LLVM"></a>

Numba
-----

Numba v0.31 (Python3.6 + JetPack 4.3/4.4)

*** Notes: Numba requires **LLVM** pre-built, so please check out the instructions for [LLVM](#LLVM) and have it installed before installing Numba.

```shell script
$ pip3 install numba==0.31 --user
```

<a name="Numba"></a>

ONNX
----

ONNX v1.4.1 (Python3.6 + JetPack 4.3/4.4)

```shell script
$ sudo apt install protobuf-compiler libprotoc-dev
$ pip install onnx==1.4.1
```
<a name="Numba"></a>

Jetson Stats
------------

Jetson-stats is a package to monitoring and control your NVIDIA Jetson [Xavier NX, Nano, AGX Xavier, TX1, TX2] Works with all NVIDIA Jetson ecosystem.

```shell script
$ cd ~
$ sudo -H pip install jetson-stats
$ sudo -H pip install -U jetson-stats
```

<a name="jetson-stats"></a>

VS Code for aarch64
-------------------

```shell script
$ cd ~
$ curl -s https://packagecloud.io/install/repositories/swift-arm/vscode/script.deb.sh | sudo bash
$ sudo apt-get install -y code-oss
```

<a name="vs-code-for-aarch64"></a>

Archiconda3
-----------

Archiconda3 is a distribution of conda for 64 bit ARM. Anaconda is a free and open-source distribution of the Python and R programming languages for scientific computing (data science, machine learning applications, large-scale data processing, predictive analytics, etc.), that aims to simplify package management and deployment. Like Virtualenv, Anaconda also uses the concept of creating environments so as to isolate different libraries and versions.

```shell script
$ cd ~
$ wget https://github.com/Archiconda/build-tools/releases/download/0.2.3/Archiconda3-0.2.3-Linux-aarch64.sh
$ sudo sh Archiconda3-0.2.3-Linux-aarch64.sh
$ rm -rf Archiconda3-0.2.3-Linux-aarch64.sh
$ cd ~
$ sudo chown -R $USER archiconda3/
$ export PATH=~/archiconda3/bin:$PATH
$ conda config --add channels conda-forge
$ conda -V
```

Please checkout site [HERE](https://github.com/yqlbu/archiconda3) for usage guide.

<a name="archiconda3"></a>

OpenCV
------

OpenCV v4.1.1 (Python2.7/3.6+ JetPack4.3/4.4)

```shell script
$ cd ~
$ wget https://raw.githubusercontent.com/yqlbu/jetson-install/master/install_opencv4.1.1_jetson.sh
$ wget https://raw.githubusercontent.com/yqlbu/jetson-install/master/remove.sh
$ unzip opencv_4.1.1
$ sudo chmod +x remove.sh
$ sudo chmod +x install_opencv4.1.1_jetson.sh
$ ./remove.sh
$ ./install_opencv4.1.1_jetson.sh
```

*** You may modify the script to install custom version of OpenCV

<a name="opencv"></a>

Pycharm
-------

PyCharm Professional

PyCharm is an integrated development environment (IDE) used in computer programming, specifically for the Python language. It is developed by the Czech company JetBrains.

```shell script
$ cd ~
$ sudo apt-get update && sudo apt-get install -y openjdk-8-jdk
$ wget https://download.jetbrains.com/python/pycharm-professional-2019.3.4.tar.gz?_ga=2.42966822.2056165753.1586158936-1955479096.1586158936 -O pycharm-professional-2019.3.4.tar.gz
$ tar -xzf pycharm-professional-2019.3.4.tar.gz && cd pycharm-2019.3.4/bin
$ sudo chmod +x pycharm.sh && mv pycharm.sh pycharm
$ sudo rm -rf pycharm-professional-2019.3.4.tar.gz
$ cd ~
$ echo 'export PATH=/home/'$USER'/pycharm-2019.3.4/bin:$PATH' >> .bashrc
```

<a name="pycharm"></a>

Docker
------

Docker is basically a container engine which uses the Linux Kernel features like namespaces and control groups to create containers on top of an operating system and automates application deployment on the container. Docker uses Copy-on-write union file system for its backend storage.

```shell script
$ cd ~
$ sudo wget -qO- https://get.docker.com/ | sh
$ sudo usermod -aG docker $USER
$ sudo systemctl enable docker 
```

<a name="docker"></a>
