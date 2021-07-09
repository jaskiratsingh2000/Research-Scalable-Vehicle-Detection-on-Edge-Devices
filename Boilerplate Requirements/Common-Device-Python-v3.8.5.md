## Installation of Python 3.8.5

> **(Applicable on Raspberry Pi 4, Raspberry Pi Zero W, and Jetsan Nano)**

Below are the following steps to install python 3.8.5 on the Hardware Devices.

### Update the System

* Updating the system before installing the Python.
```
sudo apt-get update
```

### Prequisistes
* Before installing Python 3.8.5 there are some dependencies that we need to install. Use the following command to install the required dependencies.
```
sudo apt-get install -y build-essential tk-dev libncurses5-dev libncursesw5-dev libreadline6-dev libdb5.3-dev libgdbm-dev libsqlite3-dev libssl-dev libbz2-dev libexpat1-dev liblzma-dev zlib1g-dev libffi-dev tar wget vim
```

### Download Python
* Downloading the Python from the official website using the following command:
```
wget https://www.python.org/ftp/python/3.8.5/Python-3.8.5.tgz
```

### Install Python 3.8.5
* Now we extract and install Python from the source.
```
sudo tar zxf Python-3.8.5.tgz
cd Python-3.8.5
sudo ./configure --enable-optimizations
sudo make -j 4
sudo make altinstall
```

### Check Python Version
* Now Python is installed you can check the version using the following command.
```
python3.8 -V
```

### Make python 3.8.5 as the default version
* If you want to use python 3.8 as a default version you can create an alias.
```
echo "alias python3=/usr/local/bin/python3.8" >> ~/.bashrc
```
* Then source the .bashrc file.
```
source ~/.bashrc
```

### Check Python Version
* After creating an alias check the python version again.
```
python -V
Python 3.8.5
```

Now you have successfully installed Python 3.8.5 on your hardware device
