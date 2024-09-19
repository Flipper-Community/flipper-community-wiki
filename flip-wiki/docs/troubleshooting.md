# Troubleshooting
For guides to troubleshoot some of the more obscure flipper issues, see the items below.


## Windows

### Flipper not appearing under Bluetooth in Win11
If you are attempting to use either badusb in bluetooth mode or the remote function of the flipper, Windows 11 now requires a new setting to see the flipper. 

1. Open Settings from your start menu
1. Go to **Bluetooth & Devices**
1. change **Bluetooth Device Discovery** to `Advanced`

Your flippers should now be discoverable. 

### DFU mode is not being recognized by Qflipper
This commonly occurs when a driver is conflicting with the DFU driver.
To remedy this, follow the steps below:

1. download the [Zadig driver tool](https://github.com/pbatard/libwdi/releases/)
1. With you flipper unplugged, do the steps necessary to put your flipper into DFU mode
1. open the Zadig tool
1. in the zadig tool, choose `Options`, then `List all devices`
1. choose the `DFU in FS mode` item
1. make sure the winusb driver is selected, then press `Reinstall driver`

Close the tool out, unplug your flipper and plug it back in. Qflipper should now recognize your flipper.

## Linux

### Flipper not recognized by Qflipper
Typically this issues is the result of not installing the udev rules. To fix this, follow the steps below:

1. open a terminal and `cd` to the directory of your qflipper appimage
1. run `./qFlipper-x86_64.AppImage rules install `
1. once this reports it installed successfully, reboot your pc

Alternatively, you may try running qflipper with `sudo`, however this is not ideal and has security implications. 

### Fedora Qflipper not detecting Flipper
First, verify you installed the udev rules from the steps detailed in this page.
If it still is not detected, you may be experiencing a known conflict between the udev rules of flipper and the udev rules of the `sysdemd-udev`package.
This will require you to manually apply a fix related to one of the udev rules.

See [this Github issue](https://github.com/flipperdevices/qFlipper/issues/154#issuecomment-1371038376) for further details. 

### Ubuntu cannot run the appimage
This is likely due to a missing library. 

1. Verify you have enabled the `Universe` repo, and updated your local apt database using `apt update` 
1. run `sudo apt install libfuse2` to install the missing libfuse2 library. 
1. make sure your appimage is set as executable

The appimage should now run. 
