# Beginner's Guide To Installing GhostESP For Use With The Flipper Zero
This guide shows how to install GhostESP onto an ESP32 based board for use with the Flipper Zero. GhostESP can also be used on its own, but the steps below focus on a Flipper-friendly setup.

The steps are similar for other ESP32 based boards, but you will need to select the firmware build for your specific board.

There are three methods listed below to flash the board. **You only need to select one method.**

The general steps are:

1. Check the [Prerequisites](#prerequisites)
1. Choose ^^one^^ method to flash your board under [Flashing Methods](#flashing-methods)
1. Follow the [After Flashing](#after-flashing) steps to connect to your board
1. Optional: Install the [GhostESP companion app](#installing-the-ghostesp-companion-app)

## Prerequisites

- A compatible ESP32 board. GhostESP supports the ESP32-Wroom, ESP32-S2, ESP32-S3, ESP32-C3, ESP32-C5, ESP32-C6, and ESP32-P4. See the [supported hardware page](https://docs.ghostesp.net/latest/getting-started/supported-hardware/) for the full compatibility matrix.
- A USB cable (Micro USB or USB-C). This must be a data cable, not a charge-only cable.
- For Methods 1 and 2: a WebSerial capable browser such as **Google Chrome**, **Brave**, or **Microsoft Edge**. Firefox and Safari are **NOT** supported.
- For Method 2: a tool to extract the firmware archive, such as [7-Zip](https://www.7-zip.org/download.html).
- For Method 3: a Flipper Zero with the [GhostESP companion app](#installing-the-ghostesp-companion-app) installed, and a way to wire the board to the Flipper GPIO pins.

??? note "If no serial port appears (Windows drivers)"
    Many ESP32 boards use a Silicon Labs CP210x USB-UART chip. If your board does not show a serial port after plugging it in, install the [CP210x VCP driver](https://www.silabs.com/software-and-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads), then unplug and reconnect the board.

    Cheaper boards may use a CH340 or CH9102 chip instead. Install the matching driver for the chip printed on your board.

### Entering Bootloader Mode
Methods 1 and 2 need the board in bootloader mode:

1. Hold the **BOOT** button on the board.
1. While continuing to hold **BOOT**, connect the USB cable, then release **BOOT**.
1. If that does not work: hold **BOOT**, tap **RESET**, wait 1-2 seconds, then release **BOOT**.

## Flashing Methods
Choose only ^^**one**^^ method from the list below:

- [Method 1: Web Flasher](#method-1-ghostesp-web-flasher) *(Recommended)*
- [Method 2: ESP Huhn Tool](#method-2-esp-huhn-tool)
- [Method 3: Flipper Zero](#method-3-flipper-zero-esp-flasher-app) *(No PC required)*

### Method 1: GhostESP Web Flasher
This is the recommended method and handles most of the complexity for you. It works directly from your browser without installing any tools.

1. Plug the board into your computer and put it in [bootloader mode](#entering-bootloader-mode).
1. Navigate to the [GhostESP Web Flasher](https://ghostesp.net/flasher).
1. Close any app that is using the board's serial port.
1. Select the ESP32 variant that matches your board from the dropdown.
1. Click **Connect** and follow the browser prompts to select the serial port.
1. Wait a few minutes for the flashing process to complete.
1. When flashing finishes, unplug and reconnect the board.

Proceed to [After Flashing](#after-flashing).

??? note "If the flasher fails or glitches"
    Clear your browser cache and reload the page. Disable any VPN or firewall that might block the flashing process, as some network configurations can interfere with the web flasher. If the flasher times out, reconnect the board and repeat the bootloader steps.

----

### Method 2: ESP Huhn Tool
Use this method if you prefer manual control, want to flash a specific release file, or the web flasher is unavailable.

1. Navigate to the [GhostESP releases page](https://github.com/GhostESP-Revival/GhostESP/releases) and find the most recent version.
1. Under *Assets*, download the `.zip` file that matches your exact board, saving it to a folder you can find easily.
1. Extract the `.zip` file with 7-Zip or your preferred tool.
1. Plug the board into your computer and put it in [bootloader mode](#entering-bootloader-mode).
1. Navigate to the [ESP Huhn Tool](https://esp.huhn.me/).
1. Click **Connect** and select your device's serial port.
1. Add `merged.bin` at offset `0x0`. This single file contains the bootloader, partition table, and firmware at the correct offsets for your board, so it is the recommended path. If your release has no `merged.bin`, use the separate binaries and offsets listed [below](#flashing-the-separate-binaries) instead.
1. Click **Flash** and wait for it to finish.
1. Unplug and reconnect the board.

Proceed to [After Flashing](#after-flashing).

#### Flashing the separate binaries
Only use these offsets if you are not flashing `merged.bin`. The bootloader offset depends on the chip, and the firmware offset depends on your board's partition layout. Getting either wrong produces a board that flashes successfully but never boots.

| Chip | `bootloader.bin` | `partitions.bin` | `firmware.bin` |
|---|---:|---:|---:|
| ESP32 / ESP32-S2 | `0x1000` | `0x8000` | `0x10000` (factory) or `0x20000` (OTA) |
| ESP32-C5 / ESP32-P4 | `0x2000` | `0x8000` | `0x10000` (factory) or `0x20000` (OTA) |
| ESP32-S3 / C3 / C6 | `0x0` | `0x8000` | `0x10000` (factory) or `0x20000` (OTA) |

Check the **OTA** column on the [supported hardware page](https://docs.ghostesp.net/latest/getting-started/supported-hardware/): a `✓` means the release uses a dual-partition layout, so `firmware.bin` usually belongs at `0x20000`, and `Manual` builds use the single-app layout at `0x10000`. Some OTA boards use a custom offset instead: S3TWatch uses `0x800000`, the C5 flash-XIP builds (NM-CYD-C5, T-Dongle-C5) use `0x500000`, and CrowPanel P4 builds use `0x490000`. If you are unsure which you have, flash `merged.bin` instead.

!!! warning "ESP32-C5 bootloader offset"
    The C5 ROM expects the bootloader at `0x2000`, not `0x1000` or `0x0`. Some third-party flasher instructions still say `0x0` for C5 boards, and that will not boot.

----

### Method 3: Flipper Zero (ESP Flasher App)
This method uses your Flipper Zero as the programmer, so a PC is not required for the flashing step.

1. Make sure the GhostESP companion app is on your Flipper Zero. It includes the **ESP flasher** app used below. If your custom firmware already has an up to date copy preinstalled, use that and skip this step. Otherwise see [Installing The GhostESP Companion App](#installing-the-ghostesp-companion-app).
1. Navigate to the [GhostESP releases page](https://github.com/GhostESP-Revival/GhostESP/releases) and download the `.zip` that matches your ESP32 board.
1. Extract the `.zip` file and copy its three `.bin` files to `SDCard/apps_data/esp_flasher/`. Do not place them in `assets/`.
1. Wire the ESP32 to the Flipper GPIO pins, following the pinout shown by the GhostESP app.
1. Put the ESP32 into bootloader mode: hold **BOOT**, connect USB, then release **BOOT**.
1. Open the **ESP flasher** app on the Flipper and choose **Manual Flash**.
1. Select `bootloader.bin`, `partitions.bin`, and `GhostESP.bin`, then confirm the target variant.
1. Start the flash and reset the ESP32 when it completes.

Proceed to [After Flashing](#after-flashing).

??? note "If flashing fails"
    Recheck the GPIO wiring, confirm all three `.bin` files are in `SDCard/apps_data/esp_flasher/` (not `assets/`), and make sure the selected variant matches your ESP32 chip.

----

## After Flashing
GhostESP boots automatically and creates a Wi-Fi access point called `GhostNet` with the password `GhostNet`. If you cannot see it, reboot the board and wait 10 seconds. You can control the board in three ways:

**Web Interface** (Easiest)

- Connect to the `GhostNet` Wi-Fi network
- Open a browser and go to `ghostesp.local` or `192.168.4.1`
- No authentication is required by default. To enable it, run `webauth on` from a serial terminal; the login is then your AP SSID and password (both `GhostNet` by default)
- Note: Wi-Fi and BLE commands do not work from the WebUI, because the radio is hosting the access point. Use a serial terminal or the on-device UI for those.

**On-Device UI** (Supported Display Boards)

- Open **Menu → WiFi → Scanning** and choose **Scan Access Points** to run your first scan
- Choose **List Access Points** to review the results

**Serial Terminal** (Full Control)

- Connect via USB and open a serial console at 115200 baud, for example the [GhostESP web dashboard](https://ghostesp.net/dashboard) console
- Run `help` to list all available commands
- Try your first passive scan with `scanap`, then view results with `list -a`
- To use the board through the Flipper instead of a PC, insert it into the Flipper (or wire it to the GPIO pins), plug the USB cable into the Flipper, and choose **GPIO → USB-UART Bridge**

## Installing The GhostESP Companion App

!!! warning "Custom firmware may already include it"
    If the GhostESP app is preinstalled and up to date on your custom firmware (e.g. Momentum Firmware), do not download the one from the Flipper app store. Use the preinstalled version.

The GhostESP companion app for the Flipper Zero is available on the Flipper mobile app and the Flipper app catalog. Install it here: [https://lab.flipper.net/apps/ghost_esp](https://lab.flipper.net/apps/ghost_esp)

Alternatively, download the `.fap` from the [GhostESP-FlipperCompanion releases page](https://github.com/GhostESP-Revival/GhostESP-FlipperCompanion/releases/latest) and copy it to your Flipper's SD card under the `apps/` directory.

After installing, launch it from **Applications → GPIO** on your Flipper Zero.

??? note "Version compatibility"
    The companion app is regularly updated to support new GhostESP firmware features. Always use the latest version of both the firmware and the companion app, and keep them updated together.

If you are unsure how to install applications on your Flipper Zero, see the [Official Documentation](https://docs.flipper.net/zero/apps).

## Troubleshooting

**Device won't boot or loops**

- Verify you flashed the correct firmware for your chip, and the correct offsets if you flashed separate binaries
- Try a different USB cable (some are charge-only)
- Reboot the device and wait 10 seconds

**Flash fails or times out**

- Ensure the board is in [bootloader mode](#entering-bootloader-mode)
- Try a different USB port or hub
- Close other apps using the serial port

**Can't connect to GhostNet**

- Reboot the device and move closer to it
- Check that you're using the correct password: `GhostNet` (case-sensitive)

**Serial connection issues**

- Install the [driver](#prerequisites) for your board's USB-UART chip
- Verify the correct COM port is selected

## Next Steps
- [GhostESP documentation](https://docs.ghostesp.net/latest/)
- [Try your first scan](https://docs.ghostesp.net/latest/getting-started/first-scan/)
- [Command line reference](https://docs.ghostesp.net/latest/getting-started/command-line-reference/)
- [Updating the firmware](https://docs.ghostesp.net/latest/getting-started/firmware-updates/)
