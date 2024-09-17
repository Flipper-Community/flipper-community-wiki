## Arcade Data Cards
There are five main arcade data cards that are used in arcades; they are:
> - Andamiro's [AM.PASS](https://am-pass.net/) [ISO15693-3 SLI/SLIX/SLIX2];
> 
> - Bandai Namco's [Bandai Namco Passport](https://banapass.net/setlocale/en) *fka Banapassport* [MIFARE Classic]
> 
> - Konami's [e-amusement pass](https://p.eagate.573.jp/index.html) [ISO15693-3 SLI/SLIX/SLIX2]
> 
> - Sega's [Aime Card](https://my-aime.net/en/) [MIFARE Classic]
> 
> - Taito's [NESiCA](https://nesica.net/) [MIFARE Ultralight]

If you are after the `Sega Aime Card` or `Bandai Namco Passport` access keys, then they are included in the Flipper Zero's system dictionary as of OFW 0.98.2, with the `Sega Aime Card` having a parser that reveals your access code; you may want to copy/paste the access keys into your user dictionary *if you frequently find yourself using them*.

The latter four companies have cards endorsed with the `Amusement IC Card [AIC]` logo; these cards are FeliCa, and are interoperable with each others' games.

The Flipper Zero has expanded its *FeliCa* emulation support as of OFW 0.103.1; however, `Bandai Namco Passport` readers do not recognise the emulated AIC Card and `Sega Aime Card` readers fail to read the AIC Card.
## Arcade Payment Cards
> ⚠️ ***You __should not__ be using your Flipper Zero to emulate your arcade payment card.*** ⚠️

If you are wanting to emulate your cashless pre-paid arcade payment card, then please check whether your arcade uses `Embed`; if they do, they may already have the `MobileWallet` module provisioned, meaning you may be able to legitimately add it to your `Apple Wallet` / `Google Wallet` via the arcade's Member Portal or App *provided your phone/watch/device is able to emulate NFC cards*.

If your arcade otherwise uses `InterCard`, `Sacoa`, `Amusement Connect`, `Semnox`, `RFPay`, `Tigapo`, or another cashless arcade payment system, then please read the above warning.
