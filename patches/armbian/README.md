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
$ mkdir build/patch/u-boot/u-boot-sunxi/board_luckystarh3

# copy the patches
$ cp repo/patches/armbian/u-boot/* \
     build/patch/u-boot/u-boot-sunxi/board_luckystarh3/

```

### Copy the kernel patch
> patch of kernel version is `5.15`
```
$ cp repo/patches/armbian/kernel/* \
     build/patch/kernel/sunxi-current/patches.armbian/
```

### Build
```
$ ./compile.sh BRANCH=current                                       \
               PROGRESS_LOG_TO_FILE=yes                             \
               ARMBIAN_MIRROR="https://mirrors.ustc.edu.cn/armbian" \
               CREATE_PATCHES=yes                                   \
               BOARD=luckystarh3                                    \
               KERNEL_ONLY=no
```

## Issue & Problem
If you meet any errors,  
please check your log files saved under `build/output/debug/`.

\\ Happy exploring /
