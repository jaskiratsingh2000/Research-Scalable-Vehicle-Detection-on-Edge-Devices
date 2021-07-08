## Installation of PyTorch v1.7.0 on Raspberry Pi 4

Fr this research I was required to have PyTorch v1.7 on RPi4 but installing was the problem.
* PyTorch doesn’t have official ARMv7 or ARMv8 builds. While you can get PyTorch if you have NVIDIA Jetson hardware, there are no builds for other generic boards.😞

* ONNX, no real options
I had the idea to export my trained model to ONNX (Open Neural Network eXchange format), but then what.
  * There are two projects:
     * Microsoft’s ONNX Runtime - doesn’t support RPi2
     * Snips Tract - Seems super-cool but Rust underneath (nothing against Rust, just not familiar)
So the only solution was: **Build PyTorch from source.**

### Installing Dependencies
The only dependency for the python package of torch is numpy, and I suggest using your distro's package manager to download a binary version rather than compiling it yourself.
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
The wheel file will be created in `pytorch/dist/*` after running the following commands.

* Clong the repository from the pytorch and moving inside it.
```
git clone https://github.com/pytorch/pytorch --recursive && cd pytorch
```
* Checking the version that you need to install. (Here v1.7.0)
```
git checkout v1.7.0
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

This finally 🎉 installs the PyTorch 1.70 on Raspberry Pi 4
