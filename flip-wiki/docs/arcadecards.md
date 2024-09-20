## Arcade Data Cards
!!! warning "**WARNING**"
    *You __should not__ be using your Flipper Zero to emulate your arcade data card.*

The five main arcade data cards are:

| Company | Card | Chip | Notable Games |
| ------------ | ------------- | ------------ | ------------ |
| **Andamiro** | [AM.PASS](https://am-pass.net/) | ICODE SLI/SLIX/SLIX2 | [Chrono Circle](https://chrono-circle.com/) / [PIU](https://piugame.com/) |
| **Bandai Namco** | [Bandai Namco Passport](https://banapass.net/setlocale/en/) | MIFARE Classic | [Taiko](https://donderhiroba.jp/login.php) / [WM6RR](https://wanganmaxi-official.com/wanganmaxi6rr/en/) |
| **Konami** | [e-amusement pass](https://p.eagate.573.jp/index.html)| ICODE SLI | [DDR](https://p.eagate.573.jp/game/ddr/ddrworld/top/index.html) / [SDVX](https://p.eagate.573.jp/game/sdvx/vi/) |
| **Sega** | [Aime](https://my-aime.net/en/) | MIFARE Classic | [IDAC](https://initiald.sega.jp/inidac/) / [maimai](https://maimai.sega.com/) |
| **Taito** | [NESiCA](https://nesica.net/) | MIFARE Ultralight | [MUSiCDiVER](https://musicdiver.jp/index.html) / [SF6TA](https://sf6ta.jp/) |

The Flipper Zero includes the `Sega Aime` and `Bandai Namco Passport` access keys in the system dictionary as of OFW 0.98.2, with the `Sega Aime` parser for revealing the corresponding access code.

The latter four companies have cards endorsed with the `Amusement IC Card [AIC]` logo; these cards instead use `FeliCa` chips, and are *generally* compatible for use with each others' games.

The Flipper Zero has expanded its `FeliCa` emulation support as of OFW 0.103.1; however: `Bandai Namco Passport` readers do not recognise the emulated `AIC Card`, and `Sega Aime Card` readers fail to read the `AIC Card`.
## Arcade Payment Cards
!!! warning "**WARNING**"
    *You __should not__ be using your Flipper Zero to emulate your arcade data card.*
``` mermaid
flowchart TD
    A[I Want to Emulate my Cashless Pre-Paid Arcade Payment Card.] -->|Check Phone| B[NFC-Capable Phone?]
    B -->|No| H{PHONE EMULATION NOT POSSIBLE. DO NOT USE YOUR FLIPPER ZERO.}
    B -->|Yes: Disabled| D(Enable NFC.)
    D -->|NFC Enabled| C
    B -->|Yes: Enabled| C[I Use...]
    C -->|Apple Wallet| E[My Arcade Uses...]
    C -->|Google Wallet| E
    C -->|Other Wallet| H
    E -->|Embed| F(Login to Arcade's App/Member Portal.)
    F -->|Add Card to Wallet| G{Emulate Card via Wallet.}
    E -->|Other| H
```
!!! note "**LIST OF OTHER CASHLESS PRE-PAID ARCADE PAYMENT CARDS**"
    Amusement Connect; intercard; Parafait; RFpay; Sacoa; Tigapo 
