## Installation of PyTorch v1.7.0 on Jetsan Nano

For this research I was required to have PyTorch v1.7 on Jetsan Nano but installing was the problem.
* PyTorch doesn’t have official ARMv7 or ARMv8 builds. While you can get PyTorch if you have NVIDIA Jetson hardware, there are no builds for other generic boards.😞

Now the main issue on Jetsa Nano is that it is Python version 3.6 by default and due to this it also has package wheels fo this python distribution and hence since our work is on Pthon version 3.8.5 so we have to build from source
So the only solution was: **Build PyTorch from source.**

### Installing Dependencies
The only dependency for the python package of torch is numpy, and I suggest using your distro's package manager to download a binary version rather than compiling it yourself.
Some other dependencies are also needed, like openblas, libgom, pillow etc. The Python interpreter will warn you upon import what you are missing.

**Jetsan Nano dependencies can be installed with:**
```
sudo apt install libopenblas-dev libblas-dev m4 cmake cython python3-dev python3-yaml python3-setuptools python3-wheel python3-pillow python3-numpy
```

### Download Pytorch from GitHub
* Cloning the PyTorch repository with the 1.7 branch ( 1.7 Denotes the version here)
```
git clone --recursive --branch 1.7 http://github.com/pytorch/pytorch

```
* Moving inside the `pytorch` folder
```
cd pytorch
```

### Installing requirements to build PyTorch
* installing the requirements that are needed to build the pytorch
```
python3.8 -m pip install -r requirements.txt
```

### Build PyTorch
* setup.py is a python file, the presence of which is an indication that the module/package you are about to install has likely been packaged and distributed with Distutils, which is the standard for distributing Python Modules.
```
python3.8 setup.py install --user
```
