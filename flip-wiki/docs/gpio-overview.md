# GPIO Modules Overview
Per the [Flipper official documentation](https://docs.flipper.net/gpio-and-modules), GPIO modules allow you to extend the Flipper Zero's capabilities with addon modules. 

## Popular modules
The below is NOT a complete list, and only lists a few of the popular avaliable modules for the Flipper Zero.

### CC1101
!!! warning
    there are many poor quality clones sold online. Source **genuine Ebyte CC1101 modules** when you can to avoid ineffective hardware.

CC1101 modules allow you potentially increase the range of both transmitting and receiving subghz frequencies on your Flipper Zero. However, these modules are typically only tuned for effectively transmitting well on one given frequency or on a small frequency range. Common tunings often select for either 433 MHz or 900 MHz. These devices do not have modifiable firmware and are ready to use out of the box. 

### ESP32
ESP32's are a microcontroller that can include Wi-Fi as well as Bluetooth or Zigbee and come in a variety of different form factors. Some popular ones are:

- [Official Flipper Wi-Fi Development Board](https://docs.flipper.net/development/hardware/Wi-Fi-developer-board) (based on ESP32-S2)
- ESP32-WROOM
- ESP32-S2-WROVER
- ESP32-S3

They can act as standalone devices and/or connect to the Flipper Zero's GPIO in order to provide communication between the devices. All ESP32 devices require firmware to run. This can either be pre-flashed by the seller or it can be left to the buyer as a task to do. Current Popular firmwares:

- [Black Magic](https://github.com/flipperdevices/blackmagic-esp32-s2): This firmware is geared for debugging Flipper Zero applications. Intended for the official Wi-Fi development board, but can be run on other equivalent ESP32 models with the proper pinouts.
- [Marauder](https://github.com/justcallmekoko/ESP32Marauder): This firmware will work on most ESP32's and enables them to perform **2.4 GHz only** Wi-Fi offensive and defensive tests. It also includes select bluetooth features as well on specific ESP32 boards that are bluetooth capable. 


### NRF-24
These modules are capable of handling either bluetooth communication or direct 2.4 GHz communication (Not including Wi-Fi). 
These chips do not contain modifiable firmware, and are ready to go out of the box to be used for projects. These are currently only really used to perform the [mousejacking](https://www.bastille.net/research/vulnerabilities/mousejack) technique. 

!!! note
    Mousejacking only works on a very specific [small list of wireless mice and mice/keyboard combos](https://www.bastille.net/research/vulnerabilities/mousejack/affected-devices). Outside of these devices, it is likely that this technique **cannot be used at all**.