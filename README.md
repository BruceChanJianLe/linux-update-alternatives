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

## Installing Python 3.7 on Ubuntu 18

**Step 1**  


## References

- Basic of update-alternatives [link](https://www.youtube.com/watch?v=cC9GeDNDjjM)
- GUI of update-alternative [link](https://www.youtube.com/watch?v=cC9GeDNDjjM)