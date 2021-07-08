## Installing the TorchVision v0.8.1

### Installing Dependencies
The only dependency for the python package of torchvision is numpy, and I suggest using your distro's package manager to download a binary version rather than compiling it yourself.
Some other dependencies are also needed, like openblas, libgom, pillow etc. The Python interpreter will warn you upon import what you are missing.

**Raspbian dependencies can be installed with:**
```
sudo apt install libopenblas-dev libblas-dev m4 cmake cython python3-dev python3-yaml python3-setuptools python3-wheel python3-pillow python3-numpy
```

### Build Options
```bash
export NO_CUDA=1
export NO_DISTRIBUTED=1
export NO_MKLDNN=1 
export BUILD_TEST=0
export MAX_JOBS=4
```

### Compiling the Source Code

* Clong the repository from the pytorch and moving inside it.
```
git clone https://github.com/pytorch/vision && cd vision
```
* Checking the version that you need to install. (Here v0.8.1)
```
git checkout v0.8.1
```
* Installing the submodules updates recursively
```
git submodule update --init --recursive
```
* setup.py is a python file, the presence of which is an indication that the module/package you are about to install has likely been packaged and distributed with Distutils, which is the standard for distributing Python Modules.
```
python3.8 setup.py bdist_wheel
python3.8 setup.py install --user
```

This finally 🎉 installs the TorchVision 0.8.1 on Raspberry Pi 4
