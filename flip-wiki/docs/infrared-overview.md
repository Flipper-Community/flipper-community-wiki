# Infrared Overview
The Flipper Zero contains both an infrared receiver and 3 powerful infrared LED's that have a transmit range of about a maximum of 10 meters, depending on the environment. The infrared system is only half duplex, meaning it can only transmit or receive. It cannot do both at the same time. By default, the Flipper Zero can transmit at frequencies up to 56 kHz, but only receive frequencies at 38 kHz. 

For general usage information, [see the official documentation page on infrared](https://docs.flipper.net/infrared).

## Hardware

### Transmitter
The infrared LED's are driven directly by the underlying hardware [using several hardware timers and DMA](https://github.com/flipperdevices/flipperzero-firmware/blob/7291e6bd46c564400cdd3e9e7434f2c6e3a5ff28/targets/f7/furi_hal/furi_hal_infrared.c#L30), and have no true limit for carrier frequency other than what this configuration will allow from a stability standpoint. Limited reports have suggested that using a carrier frequency at or above 56 kHz *may* introduce instability with timing. For this reason, the [Flipper Zero firmware conservatively limits the transmitter to 56 kHz](https://github.com/flipperdevices/flipperzero-firmware/blob/7291e6bd46c564400cdd3e9e7434f2c6e3a5ff28/targets/furi_hal_include/furi_hal_infrared.h#L16) via `INFRARED_MAX_FREQUENCY`. There is no notable hardware risk if one desires to change this value, so long as it is understood that higher values are not guaranteed to be accurate in transmission timings for all scenarios. One limited testing of 76 kHz confirmed that devices will respond to this custom higher carrier frequency from the Flipper Zero, even though the timings are not perfect. 

[An upcoming change in the dev firmware](https://github.com/flipperdevices/flipperzero-firmware/pull/4070/commits/5096b9c88ba8b2788a976c4b0baa891ef128221a) will allow IR frequencies of up to 1 MHz, which is the theoretical limit of what the MCU can handle. 

### Receiver
The Flipper Zero includes a Vishay TSOP75338TR receiver. This receiver is configured to receive a carrier frequency of 38 kHz while filtering out external environmental noise. This also means that the Flipper Zero is not capable from a hardware perspective of receiving carrier frequencies above 38 kHz. 

## Useful Links

### Official Links
- [Flipper infrared file format layout](https://developer.flipper.net/flipperzero/doxygen/infrared_file_format.html)

### Community Links
- [Flipper-IRDB](https://github.com/Lucaslhm/Flipper-IRDB): Community driven database of Flipper Zero formatted infrared files that anyone can contribute to.
- [IrScrutinizer](https://github.com/bengtmartensson/IrScrutinizer/releases): A tool to convert many infrared formats into IRDB formatting, which can be easily converted into a form recognizable by the Flipper Zero. 
