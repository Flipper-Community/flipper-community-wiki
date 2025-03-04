# Public Transport Cards
!!! warning "**WARNING**"
    *The below information is for educational purposes only, and is* ***__NOT__*** *designed to facilitate fare evasion.*

## Resources
- [**MetroDroid**](https://github.com/metrodroid/metrodroid)
- [**Metroflip**](https://lab.flipper.net/apps/metroflip)
- [**NFC TagInfo by NXP: Google Play**](https://play.google.com/store/apps/details?id=com.nxp.taginfolite)
- [**NFC TagInfo by NXP: App Store**](https://apps.apple.com/us/app/nfc-taginfo-by-nxp/id1246143596)

## FeliCa
If you have a Japan Rail IC Card, then you can use either `MetroDroid` or the Android version of `NFC TagInfo by NXP` to view some information relating to the card.
`Metroflip` is currently adding support for HKG Octopus and Japan Rail IC Cards, and this page will be updated when `Metroflip`'s author releases that update.

## MIFARE Classic
If your transit agency is using MIFARE Classic, then follow [**the MIFARE Classic guide**](mifareclassic.md).

## MIFARE DESFire
If your transit agency is using MIFARE DESFire, then use either your Flipper Zero's `Metroflip` and `NFC` apps, and the `MetroDroid` app to see if your transit card has any unlocked applications/files that reveal information such as:

| Category            | Example             |  
| ------------------- | ------------------- |
| Card Name           | Opal (SYD)          |
| Card Number         | 3085 2212 3456 7890 |
| Fare Type           | Full Fare           |
| Transaction Type    | Tap off             |
| Current Balance     | $10.00              |
| Last Txn Date/Time  | 31 Dec 24 at 23:59  |
| Vehicle Yype        | Bus                 |
| Weekly Journeys     | 1                   |
| Transaction Counter | 42                  |
| Issue Date          | 1 Jan 25            |
| Expiry Date         | 30 Jun 45           |
| Machine Code        | 619                 |

If the card is fully-locked, then the only valuable piece of information would be the six hexadecimal Application IDs; these may be found by looking at the Flipper Zero `.nfc` file or by scanning your card via the `NFC TagInfo by NXP` app.

Feel free to discuss public transport in [**#nfc**](https://discord.com/channels/740930220399525928/95442271613867625).
