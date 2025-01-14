# Beginner's Guide to Building Firmware & Flipper Zero Applications
This guide aims to introduce one to building and installing a release version of the firmware, as well as how to build one application from source using the Flipper Build Tool.

## Prerequisites
This guide assumes you have the following:

- Knowledge of how to navigate files and folders using `cd` in the command line
- A working install of [Git](https://git-scm.com/downloads)
- About 2 gigabytes of free space
- Access to the [Flipper Zero Firmware github page](https://github.com/flipperdevices/flipperzero-firmware)

## Building Your First Firmware

1. Create a folder on your PC where you will store the firmware
    - Ideally the path to this folder should have no spaces in the name to avoid any issues (I.E. `C:\Users\yourname\Desktop\myfirmware\`)
1. Open up command prompt or powershell and `cd` into this directory
1. Clone the firmware down to this folder using `git clone --recursive https://github.com/flipperdevices/flipperzero-firmware.git` (this will take a few minutes)
1. `cd` into the resulting `flipperzero-firmware` directory git created.
1. Once git has finished, we can now select a firmware version to check out. As of writing, 1.1.2 is the latest, so we can do `git checkout 1.1.2`. This will switch the code to the point 1.1.2 was released.

    **Note:** *Should you need to see what list of version tags are available, you can do `git tag --list` and scroll to the bottom by holding the Page Down key.*

    **Note 2:** ***[DO NOT DOWNGRADE BELOW VERSION 1.1.2](https://github.com/flipperdevices/flipperzero-firmware/releases/tag/1.1.2)***, *as this can create issues with the alarm and battery meter.*

1. We are now prepared to build the firmware with the [Flipper Build Tool](https://developer.flipper.net/flipperzero/doxygen/fbt.html) that is included with the firmware.
1. To create a Flipper Zero firmware update package using the Flipper Build Tool, simply run `./fbt updater_package` and wait a few minutes. 
1. If all went well, the command should have finished without any errors. It should have also created a folder inside the `flipperzero-firmware` directory called `dist` and reported at the end that update files were placed in this folder. 
1. Navigate into the `flipperzero-firmware` directory and go to the `dist/f7-D/` folder. There are two items of interest in this folder, ^^depending on which update method you want to do^^:
    - `flipper-z-f7-update-local.tgz`: This is a compressed archive ready to be given to qFlipper to with the ^^Install From File^^ button, or via [Flipper Lab](https://lab.flipper.net) by connecting and going to Settings -> enable Third Party fw and then choosing *INSTALL FROM FILE*
    - `f7-update-local/`: This folder contains uncompressed update files ready to be used directly on your Flipper Zero. Simply copy this folder to your Flipper Zero under the `SD Card/Update/` folder. Then on your Flipper Zero, use the file browser and go inside the folder to run the `update` file within the `f7-update-local/` folder you copied over.

Congratulations! You have now built and installed your own firmware!

!!! note "Protips"
    - If you want a more streamlined way of updating your firmware changes, you can use `./fbt flash_usb_full` to build AND install the firmware to the device all in one go!
    - To clear out build files and ensure you have a clean build directory if you make changes or want to switch versions, run `./fbt -c` to remove any old build files. Then build the firmware as normal.
    - If you have no idea what you were doing and want to undo ALL changes made since the last commit as well as delete any random files not tracked by git, you can these commands in order: `git clean -dxf` & `git reset --hard` 


## Building Your First Application
This part of the guide assumes that you were able to complete the above steps for the firmware build successfully.

Similar to building firmware, applications can be built using the Flipper Build Tool as well. Additionally, Flipper Zero applications must be built for the ^^**same**^^ firmware version your Flipper Zero has installed. 

To demonstrate building an application, we will use the [Fortune Cookie app.](https://github.com/evillero/fortune_cookie)

1. In your `Flipperzero-firmware` directory, there should be a folder called `applications_user`, this is the folder we will be placing apps we want to build into. 
1. `cd` into this directory.
1. Run `git clone https://github.com/evillero/fortune_cookie.git` to copy down the fortune cookie app. You should now have a folder called `fortune_cookie` in your `applications_user` directory.
1. Inside that folder, open up the `application.fam` file in your text editor of choice. Note the category name after `fap_category`, in this case `Games`. We will need this info for later. You may close your text editor out.
1. `cd` back to your `flipperzero-firmware` directory. 
1. Run `./fbt fap_dist` to build the code of all apps in the `applications_user` directory. 
1. Assuming fbt did not report any errors, the app should now be built
    - If you did hit errors, you'll need to contact the application author and ask them to fix it, or fix it yourself. As of v1.1.2 the Flipper Zero does not have a stable API, so applications *can* break with each update.  
1. Go in to the `dist/F7-D/` directory. You will notice a new `apps/` folder here. Go into this folder
1. Remembering the `fap_category` value from the prior steps was `Games` from our notes earlier, we now know that we can go into the `Games` folder thats inside the `apps` folder.
1. Here you will find `fortune_cookie.fap` as well as any other items categorized as games. These are ready to use.
1. Open up qFlipper or Flipper lab, and copy `fortune_cookie.fap` into `SD Card/apps/Games`, creating the `Games` folder if you do not have one. 
1. On your Flipper Zero, go to Apps -> Games, and your Fortune cookie app should be there. Simply click it and run it!

!!! note "Protip"
    If you grab the `appid` from the `application.fam` file, you can build, upload, and launch this app to the Flipper Zero all in one step! Simply do `./fbt launch APPSRC=fortune_cookie`
