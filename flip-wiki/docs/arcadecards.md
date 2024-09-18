## Arcade Data Cards
> ⚠️ ***You __should not__ be using your Flipper Zero to emulate your arcade data card.*** ⚠️

There are five main arcade data cards that are used in arcades; they are:

| Company | Card | Chip | Notable Games |
| ------------ | ------------- | ------------ | ------------ |
| **Andamiro** | [AM.PASS](https://am-pass.net/) | ICODE SLI/SLIX/SLIX2 | [Chrono Circle](https://chrono-circle.com/) / [PIU](https://piugame.com/) |
| **Bandai Namco** | [Bandai Namco Passport](https://banapass.net/setlocale/en/) | MIFARE Classic | [Taiko](https://donderhiroba.jp/login.php) / [WM6RR](https://wanganmaxi-official.com/wanganmaxi6rr/en/) |
| **Konami** | [e-amusement pass](https://p.eagate.573.jp/index.html)| ICODE SLI/SLIX/SLIX2 | [DDR](https://p.eagate.573.jp/game/ddr/ddrworld/top/index.html) / [SDVX](https://p.eagate.573.jp/game/sdvx/vi/) |
| **Sega** | [Aime](https://my-aime.net/en/) | MIFARE Classic | [IDAC](https://initiald.sega.jp/inidac/) / [maimai](https://maimai.sega.com/) |
| **Taito** | [NESiCA](https://nesica.net/) | MIFARE Ultralight | [MUSiCDiVER](https://musicdiver.jp/index.html) / [SF6TA](https://sf6ta.jp/) |

If you are after the `Sega Aime` or `Bandai Namco Passport` access keys, then they are included in the Flipper Zero's system dictionary as of OFW 0.98.2, with the `Sega Aime` having a parser that reveals your access code; you may want to copy/paste the access keys into your user dictionary *if you frequently find yourself using them*.

The latter four companies have cards endorsed with the `Amusement IC Card [AIC]` logo; these cards are `FeliCa`, and are *generally* compatible with each others' games.

The Flipper Zero has expanded its `FeliCa` emulation support as of OFW 0.103.1; however, `Bandai Namco Passport` readers do not recognise the emulated `AIC Card`, and `Sega Aime Card` readers fail to read the `AIC Card`.
## Arcade Payment Cards
> ⚠️ ***You __should not__ be using your Flipper Zero to emulate your arcade payment card.*** ⚠️

If you are wanting to emulate your cashless pre-paid arcade payment card, then please check whether your arcade uses `Embed`; if they do, they may already have the `MobileWallet` module provisioned, meaning you may be able to legitimately add your card to your `Apple Wallet` / `Google Wallet` via the arcade's Member Portal or App *provided your phone/watch/device is able to emulate NFC cards*.

If your arcade otherwise uses `Amusement Connect`, `InterCard`, `RFPay`, `Sacoa`, `Semnox`, `Tigapo`, or another cashless arcade payment system, then please read the above warning.
