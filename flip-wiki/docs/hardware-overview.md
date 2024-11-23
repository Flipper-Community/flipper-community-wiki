# Hardware Development Overview
Flipper Zero offers a number of GPIO pins that offer multiple peripheral modes as well. Official documentation for the GPIO header, including details on power available to modules, [**can be found here**](https://docs.flipper.net/gpio-and-modules).

## Expansion Modules
The Flipper Zero RTOS allows for automatic discovery of modules plugged in to the GPIO header via the [Expansion Module Protocol](https://developer.flipper.net/flipperzero/doxygen/expansion_protocol.html). An example of this is the [Video Game Module](https://docs.flipper.net/video-game-module).

It is not necessary for modules to support the Expansion Module Protocol, many modules available today do not; but it does allow for automatic discovery and configuration.

## Flipper Applications and GPIO
Flipper applications have full control over GPIO with some caveats on what pins can have their interrupts modified or peripherals they can be used for. See the official documentation linked above for an overview of that.

The [official development documentation](https://developer.flipper.net/flipperzero/doxygen/) has some basic documentation at the moment on interacting with GPIO pins and their peripheral modes. Development of this documentation is ongoing and will be updated over time.


## Useful Links

### Official Links
* [Flipper Expansion Module Protocol](https://developer.flipper.net/flipperzero/doxygen/expansion_protocol.html)
* [Flipper GPIO and Modules Overview](https://docs.flipper.net/gpio-and-modules)
* [Flipper Zero External Module Blueprints](https://docs.flipper.net/development/hardware/modules-blueprints)
* [Flipper Zero Schematics and BOM](https://docs.flipper.net/development/hardware/schematic)

### Community Links
* [PCB EDA Libraries](https://github.com/kbembedded/flipper-gpio-eda/): Provides schematic symbol and footprint libraries to make GPIO module development easier. Currently has libraries for KiCad and EagleCAD.
