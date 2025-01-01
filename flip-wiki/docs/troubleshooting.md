# Troubleshooting
For guides to troubleshoot some of the more obscure Flipper Zero issues, see the items below.


## Flipper Zero

### Forgotten/unknown Flipper Zero PIN
[See the official docs page for PIN reset instructions.](https://docs.flipper.net/basics/control#c_9ya)

If you are still having problems, browse your MicroSD card and delete the hidden `.int` folder and try the above steps in the docs again. 


### Flipper Zero is experiencing lag or behaving slow
This is an issue that is most commonly caused by certain development features being enabled and putting strain on the CPU of the flipper. 
To fix this, run through the following steps:

1. Press the center button on your flipper
1. navigate to **Settings**
1. Scroll down and select **System**
1. Scroll down again and check that the following options are set:
    - **Log Level**: `Default`
    - **Debug**: `OFF`
    - **Heap Trace**: `None`

After these are set, press back and leave the menu. Reboot your flipper. The issue should now be gone. 

### Infrared or SubGHz does not appear to be working
This is an issue that *can* occur from switching between firmwares. To fix this, try the following:

1. Connect your flipper to your PC
1. Open Up qFlipper
1. go to your SD card files
1. make sure **Show Hidden Files** is enabled
1. on your SD card, locate and delete the `/.int` folder
    - This will delete out the old misconfigured settings from past firmwares.
1. Go back to qFlipper, and reinstall the latest firmware
1. Unplug and try using your Flipper Zero again to verify the device works as expected.

### After firmware downgrade the battery status does not work
It is recommended [that you do not downgrade below version 1.1.2](https://github.com/flipperdevices/flipperzero-firmware/releases/tag/1.1.2) due to a total rework of [how the battery gauge works](https://github.com/flipperdevices/flipperzero-firmware/pull/3912) as well as a rework of the internal clock. If for some reason you do need to downgrade, you will need to do the following **prior to downgrading below 1.1.2 version:**

- Turn off any alarm settings under **Settings -> Clocks & Alarms**
- compile and run the [battery gauge tool](https://github.com/skotopes/flipperzero_gauge_tool) to unseal security settings on the battery gauge


## Windows

!!! Note
    Before trying Windows troubleshooting, try the [Official qFlipper Troubleshooting Guide](https://docs.flipper.net/qFlipper/windows-debug) **FIRST!**
    
    If those steps did not help, you may continue below.

### Flipper Zero not appearing under Bluetooth in Windows 11
If you are attempting to use either badusb in bluetooth mode or the remote function of the flipper, Windows 11 now requires a new setting to see the flipper. 

1. Open Settings from your start menu
1. Go to **Bluetooth & Devices**
1. change **Bluetooth Device Discovery** to `Advanced`

Your Flipper Zero should now be discoverable. 

### DFU mode is not being recognized by qFlipper
This commonly occurs when a driver is conflicting with the DFU driver.
To remedy this, follow the steps below:

1. Download the [Zadig driver tool](https://github.com/pbatard/libwdi/releases/)
1. With you Flipper Zero unplugged, do the steps necessary to put your Flipper Zero into DFU mode
1. Open the Zadig tool
1. In the Zadig tool, choose `Options`, then `List all devices`
1. Choose the `DFU in FS mode` item
1. Make sure the winusb driver is selected, then press `Reinstall driver`

Close the tool out, unplug your Flipper Zero and plug it back in. qFlipper should now recognize your flipper.

## Linux

### Error while loading shared libraries: libOpenGL.so.0
This error most commonly occurs on Debian, but can occur on some other distros as well. 
To fix this, you will need to install the `libopengl0` package.

On Debian, this can be done via `sudo apt install libopengl0`. 


### Flipper Zero not recognized by qFlipper
Typically this issues is the result of not installing the udev rules. To fix this, follow the steps below:

1. open a terminal and `cd` to the directory of your qFlipper appimage
1. run `./qFlipper-x86_64.AppImage rules install `
1. once this reports it installed successfully, reboot your pc

Alternatively, you may try running qFlipper with `sudo`, however this is not ideal and has security implications. 

### Fedora qFlipper not detecting Flipper Zero
First, verify you installed the udev rules from the steps detailed in this page.
If it still is not detected, you may be experiencing a known conflict between the udev rules of Flipper Zero and the udev rules of the `sysdemd-udev`package.
This will require you to manually apply a fix related to one of the udev rules.

See [this Github issue](https://github.com/flipperdevices/qFlipper/issues/154#issuecomment-1371038376) for further details. 

### Ubuntu cannot run the appimage
This is likely due to a missing library. 

1. Verify you have enabled the `Universe` repo, and updated your local apt database using `apt update` 
1. run `sudo apt install libfuse2` to install the missing libfuse2 library. 
1. make sure your appimage is set as executable

The appimage should now run. 

## ChromeOS

### qFlipper returns permission denied
ChromeOS users will have to only utilize [Flipper Lab](https://lab.flipper.net), no other option is currently possible for ChromeOS. 

While ChromeOS does allow USB devices to access Linux environments via `Settings > Linux > USB preferences`, the security hardening features of ChromeOS 
prevent udev scripts from applying the `uaccess` property to the device within the context of the secure linux container, which is needed for qFlipper to properly access the Flipper Zero. Attempting to run qFlipper with `sudo -E` is also fruitless.
This roadblock lies firmly on the ChromeOS side for the time being. While Flipper Labs is nearly at feature parity with qFlipper, it cannot perform a DFU recovery. Should such a need arise, you will need temporary access to a non ChromeOS based PC. 
