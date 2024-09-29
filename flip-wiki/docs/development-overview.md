# Development Overview
Flipper Zero development is done via two primary tools:

- [**FBT**](https://github.com/flipperdevices/flipperzero-firmware/blob/dev/documentation/fbt.md): This tool is the complete build tool, and it included when doing a full clone of the flipper zero firmware repository. This tool allows for the building of any component (firmware, app, or animation) for the Flipper Zero.  

- [**UFBT**](https://github.com/flipperdevices/flipperzero-ufbt): Considered the 'lite' version of FBT, this tool is focused on external app building only. 

Both of these tool currently provide a command in their respective documentation to get a Visual Studio Code environment up and running.

## Development Documentation
The official documentation for development [**can be found here**](https://developer.flipper.net/flipperzero/doxygen/).

Work is ongoing to continue to add more information to the official development docs, and the source code is still currently the best way to study how things work.

As linked in the official development docs, a few sample applications can be found [here](https://github.com/flipperdevices/flipperzero-firmware/tree/dev/applications/examples).


## Useful Links

### Official Links
* [Flipper Application Package Overview](https://github.com/flipperdevices/flipperzero-firmware/blob/dev/documentation/AppsOnSDCard.md)
* [Flipper Zero development keynote presentation](https://miro.com/app/board/o9J_l1XZfbw=/?share_link_id=887297737912): Contains lots of basic core knowledge surrounding development.
* [Flipper Zero GUI Overview](https://miro.com/app/board/uXjVOa4cno8=/): Describes the design and workflow intended for drawing GUI items.
* [Flipper Zero API symbols](https://github.com/flipperdevices/flipperzero-firmware/blob/dev/targets/f7/api_symbols.csv): Provided as a list of API functions and headers, any items here with a `+` on them should be active. 

### Community Links

* [Flipper zero dev tutorials from Derek Jamison](https://github.com/jamisonderek/flipper-zero-tutorials/wiki)
    * Associated [Youtube Channel](https://www.youtube.com/@MrDerekJamison/featured)