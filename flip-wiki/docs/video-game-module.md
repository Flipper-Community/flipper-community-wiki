# Video Game Module

The [Video Game Module](https://docs.flipper.net/video-game-module), developed and sold by [Flipper Devices](https://shop.flipperzero.one/products/video-game-module-for-flipper-zero), is an exciting gaming GPIO attachment that takes your Flipper Zero to the next level. Here’s what it offers:

- **Motion Sensor**: Adds a new dimension of interactivity by detecting motion for games or creative projects.  
- **USB-C Port**: Connect to external devices or power up with ease.  
- **HDMI Port**: Play your games or display visuals on monitors and TVs.  
- **14-Pin GPIO Port**: Connect external peripherals or explore custom projects with ease.  
- **Raspberry Pi RP2040 Microcontroller**: Delivers high performance and flexibility for endless possibilities.  

---

## Features  

The Video Game Module unlocks a wide range of capabilities:  
- **Gaming on the Big Screen**: Play your Flipper Zero games on your TV or monitor, enhanced with motion controls for hands-free action.  
- **Standalone Mode**: Use it independently of the Flipper Zero for gaming or as a powerful prototyping tool.  
- **Open Source**: With open-source firmware and schematics, you can tweak, extend, and share your own enhancements.  
- **Seamless Compatibility**: Fully integrates with Flipper Zero for gaming and development, while remaining versatile for other projects.  

---

## Firmware  

Flashing the Video Game Module is easy with the [Video Game Module Tool App](https://lab.flipper.net/apps/video_game_module_tool). Here's what you can do:  
- **Install Official Firmware**: Directly update through the app for hassle-free setup.  
- **Use Custom Firmware**: Load `.uf2` files onto your Flipper Zero’s SD card to unlock custom features.  

You can also flash the Raspberry Pi Pico series using this app! Just follow this simple wiring guide:  

### Wiring Guide  (Pico -> Flipper Zero)
- **SWCLK** (left debug pin) → **Pin 10 (SWC)**  
- **GND** → **Pin 11 (GND)**  
- **SWDIO** (right debug pin) → **Pin 12 (SIO)**  
- **Pin 36 (3V3 OUT)** → **Pin 9 (3v3)**  
- **Pin 39 (VSYS)** → **Pin 1 (5v)**  
- **Pin 1 (TX)** → **Pin 14 (RX)**  
- **Pin 2 (RX)** → **Pin 13 (TX)**  