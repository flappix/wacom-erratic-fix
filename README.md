# wacom-erratic-fix
Software fix for hardware defect of Wacom tablet which has erratically cursor movement.

Tablets with this issue produce images like that when you are drawing

![](https://github.com/flappix/wacom-erratic-fix/raw/master/path945.png)

## Installation

1. Download xf86-input-wacom source code (tested with version 0.39.0): https://github.com/linuxwacom/xf86-input-wacom/releases
2. Extract source code: ```tar -vxf xf86-input-wacom-0.39.0.tar.bz2```
3. Download [patch](https://raw.githubusercontent.com/flappix/wacom-erratic-fix/master/patch) from this repository
4. Apply patch: ```cd xf86-input-wacom-0.39.0; patch src/wcmCommon.c < ../patch```
4. build and install: ```./configure && make && sudo make install```


## Configuration
This patch ist just preventing large movements between two consecutive frames. The maximum allowed value is hard coded with ```200```. You might want to adjust this value according to your needs by changeing the line ```int max_move = 200;``` in the patch file.

Too small values will disable you to draw fast lines while too high values will not fix the hardware issue.
