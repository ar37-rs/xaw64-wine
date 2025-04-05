# Current state
## Wine
Version: 10.4

## Box64
Version: 0.3.5

# Installation:
### Install desktop for native termux
[(Read for more info on how to setup xfce4)](https://github.com/ar37-rs/xfce4-termux)

or

[(using termux-desktop from here)](https://github.com/sabamdarif/termux-desktop/tree/main)

### Make sure if wget is installed
```
pkg install wget
```

### Install xaw64 (Bash script only)
```
cd $HOME && rm -rf ~/xaw64 && wget https://github.com/ar37-rs/xaw64-wine/raw/refs/heads/main/xaw64 && chmod +x ~/xaw64
```

### and then
```
~/xaw64 install
```

# Usage
Read more from [here](https://github.com/ar37-rs/xow64-wine)

# Note
Some commands and drivers might not available, just use default builtin termux drivers.
