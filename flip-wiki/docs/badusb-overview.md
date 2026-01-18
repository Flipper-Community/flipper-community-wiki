# BadUSB Overview
BadUSB is an [official feature of the Flipper Zero](https://docs.flipper.net/bad-usb) that can allow the device to act as a high speed keyboard to automatically type just about anything you would be able to do on a normal keyboard, just significantly faster via USB or Bluetooth. BadUSB now also supports mouse movement and click commands. 

The BadUSB scripting language is based on [Duckyscript 1.0](https://web.archive.org/web/20220816200129/http://github.com/hak5darren/USB-Rubber-Ducky/wiki/Duckyscript). Unlike later version of Duckyscript, this version only supports sending keys to a PC, not receiving any files or info back to the Flipper Zero itself. The Flipper Zero's version of Duckyscript also supports changing the USB ID presented to the computer in the event one wishes to make the devices appear as a specific brand of keyboard. 


On a fresh firmware install of the official firmware, several non-destructive fun sample scripts will be placed in the `badusb` folder of your device. These are simple text files and can be read with notepad to see what they do prior to running them. 

## Supported Keys
Current up to date supported keys and other useful BadUSB script commands can be found at the [Official BadUSB developer documentation site](https://developer.flipper.net/flipperzero/doxygen/badusb_file_format.html). 

For convenience, a basic list of supported keys can be found below:

- Mouse click, move, and scroll
- Standard alphanumeric typing keys
- Special characters
- CTRL, ALT, SHIFT, WIN, SYSRQ keys
- All function lock keys (caps, scroll, and number lock)
- Special keys such as insert, home, page-up, etc.
- Media keys, including volume
- ALT+NUMPAD combos
- Fn key / Mac Globe key
- F1-F12 keys
- Arrow keys

## Javascript Utilization
BadUSB scripts are very basic and simply go down the list of commands sequentially, offering no execution order control. 

With the introduction of javascript and the BadUSB module included as part of the javascript implementation, one can begin to add more advanced logic to BadUSB scripts such as loops, conditionals, GUI menus, and other items. 

For more information on this subject, see the [Javascript wiki page](javascript-overview.md)

