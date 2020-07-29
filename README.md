# Linux Update-Alternatives

Ever wonder how to reset the default editor to vim? Install another version of gcc? Install the latest python 3.7 version? Here's the answer without going to use virtual environment as you can manage your own environment!

## Resetting Your Default Editor

**Step 1**  
Install vim
```bash
sudo apt-get install vim
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



## References

- Basic of update-alternatives [link](https://www.youtube.com/watch?v=cC9GeDNDjjM)
- GUI of update-alternative [link](https://www.youtube.com/watch?v=cC9GeDNDjjM)