# MIFARE Classic
Here are the steps to follow in order to read your cards. Your goal is to find as many keys as possible. The keys unlock sections of your card for the Flipper to read them - you must have a card. Once you read enough sections, you can use an emulated or cloned card at the original card reader to unlock it (sometimes even without finding all of the keys!).


> [!IMPORTANT]
> **Major update** coming in [first update following OFW 1.0.0](https://github.com/flipperdevices/flipperzero-firmware/pull/3822#issuecomment-2335180124) (ETA: mid to late September) which overhauls and simplifies this process: [![Status](https://img.shields.io/github/pulls/detail/state/flipperdevices/flipperzero-firmware/3822?label=Status&style=flat-square)](https://github.com/flipperdevices/flipperzero-firmware/pull/3822)

## Reading the card

Steps:

1. **Dictionary attack**: Try to scan your MIFARE Classic card with NFC -> Read. It will try a dictionary attack of default keys to unlock your card, as well as any keys you may have found through other methods. Do not interrupt the dictionary attack, it may take a while! If it finds 32/32 keys (or 80/80) with 16/16 sectors (or 40/40), congratulations and [proceed to "Emulation"](mifareclassic.md#emulation). If not, continue to step 2.
2. **Mfkey32 attack** (<https://docs.flipper.net/nfc/mfkey32>): If you have only a few keys found or no keys found, you can get more keys from the card reader (the same one you would normally tap your card against). If you do not have access to the card reader and have at least one key, you may skip to step 3. Navigate to NFC -> Detect Reader (renamed to "Extract MF Keys" in OFW 1.0.0) and hold the Flipper Zero up to the reader. If the reader unlocks during this process, it is using the UID of the card and is highly insecure. Otherwise, it'll collect "nonces" from the reader, which allows you to recover keys using any one of these three methods:
    - On your Computer: ![Flipper Devices official method](https://cdn.flipperzero.one/favicon-16x16.png) Connect your Flipper Zero with a USB-C cable to your computer, visit https://lab.flipper.net/ in Chrome -> NFC Tools -> GIVE ME THE KEYS, or mfkey32v2 https://github.com/equipter/mfkey32v2. This is the original method and the best supported by the experts on Discord.
    - On your Flipper Mobile App (iOS/Android): ![Flipper Devices official method](https://cdn.flipperzero.one/favicon-16x16.png) Connect your Flipper Zero via Bluetooth, navigate to Hub -> NFC tools -> Mfkey32 (Detect Reader). This is the most common official method today.
    - On your Flipper: Main Menu -> Applications -> NFC -> MFKey ([available on the App Hub](https://lab.flipper.net/apps/mfkey) if you are missing it), press OK to run. This is when you only have a Flipper Zero. CFW may have insufficient memory to run at full speed (reboot Flipper).

    When the cracking process is complete, the number of new user keys that are found will be shown. If more than zero keys are found, return to step 1 and repeat the process.
3. **Nested attack** (<https://github.com/AloneLiberty/FlipperNested>) (⚠️ IMPORTANT: Currently only works on firmware [0.93.0](https://update.flipperzero.one/builds/firmware/0.93.0/) - flipper-z-f7-update-0.93.0.tgz - and below - update coming at the end of September 2024): If you have at least one key from the previous attacks, you can run a Nested attack against the card. First, [download the FlipperNested app from the App Hub](https://lab.flipper.net/apps/mifare_nested) on the Flipper Mobile App. Then follow the guide here: <https://github.com/AloneLiberty/FlipperNested/wiki/Usage-guide> (English, Russian provided at main link). If the card is not vulnerable to a Nested attack, the app will let you know. The nonces it collects will allow you to perform one of these three attacks (see guide):
    - Static Nested: This can be cracked by FlipperNestedRecovery on a computer, or your Flipper Zero using the [MFKey app](https://lab.flipper.net/apps/mfkey). Cracking coming soon to the Flipper Mobile App (Android).
    - Full Nested or Hard Nested: This requires FlipperNestedRecovery to crack on a computer. It is being improved. Full Nested may be available on your Flipper Zero in the near future.

    If more than zero keys are found by FlipperNested after running "Check found keys", return to step 1 and repeat the process. If FlipperNested reports you have a Static Encrypted card, you must use a [Proxmark](google.com/search?q=PM3%20Easy%20512k) and run the command `script run fm11rf08s_recovery` (or sniff the reader). Cracking Static Encrypted cards will be possible in the Flipper [firmware update later this month](https://github.com/flipperdevices/flipperzero-firmware/pull/3822).
4. **KDF attack** (https://github.com/noproto/flipper_kdf): You can use KDF plugins to instantly crack keys for [certain brands](https://github.com/noproto/flipper_kdf/wiki/List). Visit <https://github.com/noproto/flipper_kdf/releases/latest>, download the latest plugins.zip file, extract the plugin files (.fal) to your SD card (ext) at /apps_data/nfc/plugins/, and finally try to scan your card using the NFC app again. If it finds 32/32 keys (or 80/80) with 16/16 sectors (or 40/40), congratulations and [proceed to "Emulation"](mifareclassic.md#emulation).

If you have completed all of the above steps and do not have all of the keys, return to step 2 (Mfkey32). If Mfkey32 no longer finds new keys, there is no known process to crack the remaining keys to your card at this time.

## Emulation

![Emulation](https://gist.githubusercontent.com/noproto/2ee35c1916b358924c08f77645a46d81/raw/c4f19920a2ccbe4c66998476a3d4d76c2f98ad78/emulation.png "Emulation")

Go to NFC -> Saved -> (The name you assigned your card) -> Emulate and hold it up to the reader. Try various angles to find the correct positioning.

Even if you have all of the keys and try to emulate your card, you may find the reader still does not accept the emulated card (<https://flp.wiki/nfc/mfc/emulation/>). This is often a timing issue (slow emulation on the Flipper Zero). You have three options:

* Update your Flipper Zero to the latest firmware (0.94.0 or above). Flipper Devices rewrote the NFC stack, which improved MIFARE Classic dictionary attacks and emulation. Be aware that FlipperNested does not yet support any firmware above 0.93.0.
* Purchase a special kind of MIFARE Classic card called a magic card to clone the data onto a physical card. Magic cards are more likely to be recognized by the card reader, however some readers may be programmed to detect magic cards. To find shops to purchase magic cards from, search for the magic card you need (ensure the listing mentions the term "UID changeable"):
    - 4 byte UID (e.g. `AA BB CC DD`): Gen1a Magic Card (💲), Gen2 Magic Card - 4 byte UID variant (💲💲)
    - 7 byte UID (e.g. `AA BB CC DD EE FF 00`): Gen2 Magic Card - 7 byte UID variant (💲💲), Gen4/Ultimate Magic Card (💲💲💲)

    Follow the official guide to write the card data to a magic card: (<https://docs.flipper.net/nfc/magic-cards>).
* If you have a spare identical MIFARE Classic card (1K for 1K, 4K for 4K, EV1 for EV1, etc.), have all of the keys to the spare card, and the access conditions on the spare card allow: you can duplicate the data from the initial card to the spare card and it could possibly work (if the reader is indifferent to the UID of the card, and the keys are *diversified* - you will need the diversified keys from the reader using Mfkey32/KDF if they are not already present on the card). ⚠️ IMPORTANT: Save the data stored on the spare card before overwriting it, otherwise it will be irrecoverably erased. This is less reliable than using a magic card, but an option if you are unable to obtain a magic card.