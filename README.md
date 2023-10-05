# Linux Update-Alternatives

Ever wonder how to reset the default editor to vim? Install another version of gcc? Install the latest python 3.7 version? Here's the answer without going to use virtual environment as you can manage your own environment!

## Resetting Your Default Editor

**Step 1**  
Install vim  
```bash
sudo apt-get install vim -y
```

**Step 2**  
Choosing vim as the default editor  
```bash
sudo update-alternatives --config editor

# There are 5 choices for the alternative editor (providing /usr/bin/editor).
# 
#   Selection    Path                Priority   Status
# ------------------------------------------------------------
#   0            /bin/nano            40        auto mode
#   1            /bin/ed             -100       manual mode
#   2            /bin/nano            40        manual mode
#   3            /usr/bin/code        0         manual mode
# * 4            /usr/bin/vim.basic   30        manual mode
#   5            /usr/bin/vim.tiny    15        manual mode
# 
# Press <enter> to keep the current choice[*], or type selection number: 

# Choose 4!
```

## Installing a newer version of gcc on Ubuntu 16

**Step 1**  
Install tool chain to find g++7 and gcc-7
```bash
sudo apt-get install -y software-properties-common
# Install tool chain to find g++-7 and gcc-7 in apt
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get install g++-7 gcc-7 -y
```

**Step 2**  
Remove anything that is named as g++ or gcc  
```bash
# Remove g++ or gcc if you have them
sudo update-alternatives --remove-all g++
sudo update-alternatives --remove-all gcc
```

**Step 3**  
Add g++-7 and gcc-7 to update-alternatives  
```bash
# Add in new g++ and gcc
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 60 \
--slave /usr/bin/g++ g++ /usr/bin/g++-7
```

**Extra Steps**  
Look at your gcc and g++  
```bash
# Choose your g++ or gcc (if you already remove them by default you only have one gcc)
sudo update-alternatives --config gcc
```

Ref: https://askubuntu.com/questions/26498/how-to-choose-the-default-gcc-and-g-version

## Installing Python 3.7 on Ubuntu 18

**Step 1**  
Start by updating the packages list and installing the prerequisites  
```bash
sudo apt update
sudo apt install software-properties-common
```

**Step 2**  
Add deadsnakes PPA to your sources list:  
```bash
sudo add-apt-repository ppa:deadsnakes/ppa
```

**Step 3**  
Install Python 3.7  
```bash
sudo apt install python3.7

# To verify if it is installed
ls /usr/bin/pyhton*
# /usr/bin/python            /usr/bin/python2-config  /usr/bin/python3.6-config   /usr/bin/python3.7m       /usr/bin/python-config
# /usr/bin/python2           /usr/bin/python2-qr      /usr/bin/python3.6m         /usr/bin/python3-config
# /usr/bin/python2.7         /usr/bin/python3         /usr/bin/python3.6m-config  /usr/bin/python3m
# /usr/bin/python2.7-config  /usr/bin/python3.6       /usr/bin/python3.7          /usr/bin/python3m-config
```

**Step 4**  
Setup python3.7 as the default python3 bin  
```bash
# WARNING, better do not do this and instead use method below, as some dependecies still depend on python3.6
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.7 80
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 10
```

Now that should do the trick, but if you do not want to mess with the system, you can always call python3.7 by  
```bash
python3.7 -m http.server 8080
```

## References

- Basic of update-alternatives [link](https://www.youtube.com/watch?v=cC9GeDNDjjM)
- GUI of update-alternative [link](https://www.youtube.com/watch?v=cC9GeDNDjjM)
- Python3.7 Installation on Ubuntu 18 [link](https://linuxize.com/post/how-to-install-python-3-7-on-ubuntu-18-04/)
