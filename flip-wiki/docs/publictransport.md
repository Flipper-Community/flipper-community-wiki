# Public Transport Cards
**<p style="text-align:center;color:red">NOTE: The below information is for educational purposes only, and is <b><u>NOT</u></b> designed to facilitate fare evasion.</p>**


## Resources
- [MetroDroid](https://github.com/metrodroid/metrodroid)
- [NXP TagInfo by NXP: Google Play](https://play.google.com/store/apps/details?id=com.nxp.taginfolite)
- [NXP TagInfo by NXP: App Store](https://apps.apple.com/us/app/nfc-taginfo-by-nxp/id1246143596)

## MIFARE Classic
If your transit agency is using MIFARE Classic, then follow [the MIFARE Classic guide](mifareclassic.md).

## MIFARE DESFire
If your transit agency is using MIFARE DESFire, then use either your Flipper Zero or the `MetroDroid` app to see if your transit card has any unlocked applications/files that reveal information such as:
- Card name;
- Card number;
- Fare type;
- Product type;
- Machine code;
- Current balance;
- Last/recent transaction date[s]/time[s];
- Vehicle type;
- Weekly journeys;
- Transaction counter

If the card is fully-locked, then the only valuable piece of information would be the six hexadecimal Application IDs; these may be found by looking at the Flipper Zero `.nfc` file or by scanning your card via the `NXP TagInfo by NXP` app.

Feel free to discuss public transport in [#nfc](https://discord.com/channels/740930220399525928/95442271613867625).
