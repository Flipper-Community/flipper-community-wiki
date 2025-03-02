# NFC Overview

The Flipper Zero can read and emulate a number of NFC tags. Keep in mind however that NFC RFID technology is a complex topic with *many* tag types of varying security, and not all can be read by the device. 
The official [Flipper Zero docs](https://docs.flipper.net/nfc/read) detail what types of cards can and cannot be used with the device. Additionally, while the device can read these cards, not all of them can be saved or emulated due to the higher security design of select NFC formats. 



## MIFARE Classic
- See our [**MIFARE Classic guide**](mifareclassic.md)
- For making copies of mifare classic, refer to the [documentation](https://docs.flipper.net/nfc/magic-cards)

## HID Seos / NXP MIFARE DESFire
- Standard keyed can be read with [Seader](https://lab.flipper.net/apps/seader)
