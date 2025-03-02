# NFC Overview

The Flipper Zero can read and emulate a number of NFC tags. Keep in mind however that NFC RFID technology is a complex topic with *many* tag types of varying security, and not all can be read by the device. 
The official [Flipper Zero docs](https://docs.flipper.net/nfc/read) detail what types of cards can and cannot be used with the device. Additionally, while the device can read these cards, not all of them can be saved or emulated due to the higher security design of select NFC formats. 

---
## MIFARE Classic
- See our [**MIFARE Classic guide**](mifareclassic.md).
- For making copies of MIFARE Classic, refer to the [documentation](https://docs.flipper.net/nfc/magic-cards).

---
## MIFARE DESFire
- Use the `NFC` App to read the DESFire credential.

---
## HID iCLASS
- Standard-keyed iCLASS can be read via [PicoPass](https://lab.flipper.net/apps/picopass).
- Certain elite-keyed iCLASS can also be read via `PicoPass` via the `Elite System Dictionary`.
- Some iCLASS SE credentials can be read via [Seader](https://lab.flipper.net/apps/seader).
  - *You will require a compatible NARD and SAM to use the `Seader` app.*

---
## HID SEOS
- Standard-keyed Seos can be read with [Seader](https://lab.flipper.net/apps/seader).
   - *You will require a compatible NARD and SAM to use the `Seader` app.*
