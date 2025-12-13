# Public Transport Cards
!!! warning "**WARNING**"
    *The below information is for educational purposes only, and is* ***__NOT__*** *designed to facilitate fare evasion.*

## Resources
- [**MetroDroid**](https://github.com/metrodroid/metrodroid)
- [**Metroflip**](https://lab.flipper.net/apps/metroflip)
- [**NFC TagInfo by NXP: Google Play**](https://play.google.com/store/apps/details?id=com.nxp.taginfolite)
- [**NFC TagInfo by NXP: App Store**](https://apps.apple.com/us/app/nfc-taginfo-by-nxp/id1246143596)
- [**PTDex**](https://github.com/ry4000/ptdex)

## FeliCa
If you have either a HKG Octopus Card or a Japan Transit IC Card *using FeliCa*, then you can use either `MetroDroid` or the Android version of `NFC TagInfo by NXP` to view some information relating to the card.
`Metroflip` added support for HKG Octopus and Japan Transit IC Cards *using FeliCa* as of OFW 1.4.2.

It is also possible to use FeliCa *Standard* cards/tags/fobs/charms as an [**arcade data card**](arcadecards.md) for use on some `Konami` games.

## MIFARE Classic
If your transit agency is using MIFARE Classic, then follow [**the MIFARE Classic guide**](mifareclassic.md).

## MIFARE DESFire
If your transit agency is using MIFARE DESFire, then use either your Flipper Zero's `Metroflip` and `NFC` apps, and the `MetroDroid` app to see if your transit card has any unlocked applications/files that reveal information such as:

|                         | Example 1           | Example 2             |
| ----------------------- | ------------------- | --------------------- |
| **Card Name**           | Opal (SYD)          | metroCARD (ADL)       |
| **Card Number**         | 3085 2212 3456 7890 | 01-141 2345 6789 0123 | 
| **Fare Type**           | Full Fare           | Regular               |
| **Transaction Type**    | Tap off             |                       |
| **Current Balance**     | $10.00              |                       |
| **Last Txn Date/Time**  | Wed 5th Jul 4:20pm  | 31 May 2024 at 06:19  |
| **Balance Updated**     | 12:34 10/01/2025    |                       |
| **Vehicle Type**        | Bus                 | Bus 1234              |
| **Weekly Journeys**     | 1                   |                       |
| **Transaction Counter** | 12                  |                       |
| **Issue Date**          |                     | 1 January 2024        |
| **Expiry Date**         |                     | 30 June 2044          |
| **Machine Code**        |                     | 123                   |

Some transit agencies allow you to scan your card via their mobile app, which may provide additional information such as:

|                        | Example 3                                                    | 
| ---------------------  | ------------------------------------------------------------ |
| **Card Name**          | Leap (DUB)                                                   |
| **App**                | [**Leap Top-Up**](https://about.leapcard.ie/leap-top-up-app) |
| **Current Balance**    | €0.00                                                        |
| **Card Number**        | 10123 45678                                                  |
| **Status**             | Unblocked                                                    |
| **Auto Top-Up Status** | Disabled (€0.00)                                             |
| **Issue Date**         | 6/9/23                                                       |
| **Expiry Date**        | 20/4/43                                                      |
| **Fare Type**          | Adult                                                        | 
| **Last Txn Date/Time** | 19 Jun 13:37 Dublin Bus -€2.00                               |
| **Daily Cap**          | €0.00 / €8.00                                                |
| **Weekly Cap**         | €0.00 / €32.00                                               |

If the card is fully-locked, then the only valuable piece of information would be the six hexadecimal Application IDs; these may be found by looking at the Flipper Zero `.nfc` file or by scanning your card via the `NFC TagInfo by NXP` app. 

Little-endian is used for Flipper Devices' purposes. `Clipper (SFO)`'s AID in big-endian, for example, is `F21190`; converting it to little-endian, it then becomes `0x9011F2`.

Feel free to discuss public transport in [**#nfc**](https://discord.com/channels/740930220399525928/95442271613867625).
