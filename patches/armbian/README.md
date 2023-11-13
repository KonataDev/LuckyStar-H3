## To build an Armbian image

\\((@ > ω <@))o (Armbian)~  


### Tools & Source Code
```
$ sudo apt -y install git
$ git clone https://github.com/armbian/build --depth 1
```

### Copy the board file
```
$ cp repo/patches/armbian/board/luckystar-h3.csc \
     build/config/boards/
```

### Copy the u-boot patches
> patch of u-boot version is `v2022.07`
```
# create the patch directory, all patches will be
# applied automatically before build the u-boot

$ mkdir -p build/userpatches/u-boot/u-boot-sunxi/board_luckystar-h3

# copy the patches

$ cp repo/patches/armbian/u-boot/* \
     build/userpatches/u-boot/u-boot-sunxi/board_luckystar-h3/
```

### Copy the kernel patch
> patch of kernel version is `5.15`
```
# create the patch directory, all patches will be
# applied automatically before build the kernel

$ mkdir -p build/userpatches/kernel/archive/sunxi-5.15

# copy the patches

$ cp repo/patches/armbian/kernel/* \
     build/userpatches/kernel/archive/sunxi-5.15/
```

### Build
```
$ ./compile.sh BRANCH=current                                       \
               PROGRESS_LOG_TO_FILE=yes                             \
               ARMBIAN_MIRROR="https://mirrors.ustc.edu.cn/armbian" \
               BOARD='luckystar-h3'
```

## Issue & Problem
If you meet any errors,  
please check your log files saved under `build/output/debug/`.

\\ Happy exploring /
