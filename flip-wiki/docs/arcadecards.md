## Arcade Data Cards
!!! warning "**WARNING**"
    *You __should not__ be using your Flipper Zero to emulate your arcade data card.*

The five main arcade data cards are:

| Company | FeliCa<br>AIC | Card | Chip | Notable Games |
| ----------- | ---------- | ------------ | ----------- | ----------- |
| **Andamiro** | - | [AM.PASS](https://am-pass.net/) | ICODE SLI<br>ICODE SLIX<br>ICODE SLIX2 | [Chrono Circle](https://chrono-circle.com/)<br>[PIU](https://piugame.com/) |
| **Bandai Namco** | X | [Bandai Namco Passport](https://banapass.net/setlocale/en/) | MIFARE Classic | [Taiko](https://donderhiroba.jp/login.php)<br>[WM6RR](https://wanganmaxi-official.com/wanganmaxi6rr/en/) |
| **Konami** | X | [e-amusement pass](https://p.eagate.573.jp/index.html)| ICODE SLI | [DDR](https://p.eagate.573.jp/game/ddr/ddrworld/top/index.html)<br>[SDVX](https://p.eagate.573.jp/game/sdvx/vi/) |
| **Sega** | X | [Aime](https://my-aime.net/en/) | MIFARE Classic | [IDAC](https://initiald.sega.jp/inidac/)<br>[maimai](https://maimai.sega.com/) |
| **Taito** | X | [NESiCA](https://nesica.net/) | MIFARE Ultralight | [MUSiCDiVER](https://musicdiver.jp/index.html)<br>[SF6TA](https://sf6ta.jp/) |

The Flipper Zero includes the `Sega Aime` and `Bandai Namco Passport` access keys in the system dictionary as of OFW 0.98.2, with the `Sega Aime` parser for revealing the corresponding access code.

The latter four companies have FeliCa card variants endorsed with the `Amusement IC Card [AIC]` logo, with the Flipper Zero having expanded its `FeliCa` emulation support as of OFW 0.103.1, and emulation compatibility is listed below:

### Arcade Data Card Emulation Compatability
| Card | Chip | Andamiro | Bandai<br>Namco | Konami | Sega | Taito |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| Sega Aime | MFC | - | X | - | X | 1 |
| AM.PASS | ICODE SLI<br>ICODE SLIX<br>ICODE SLIX2| X | - | 2 | - | 1 |  
| Amusement IC | FeliCa | - | X<sup>3</sup> | X<sup>3</sup> | 4 | 1 | 
| Banapassport | MFC | - | X | - | X | 1 |
| e-amusement | ICODE SLI | 2 | - | 5 | - | 1 |
| NESiCA | MFU | - | - | - | - | 1 |

### Arcade Data Card Emulation Compatability Notes
    1) Emulation compatibility cannot be tested for Taito games without assistance from Members located within Japan.
    2) The `AM.PASS` and `e-amusement pass` ISO15693 cards are not compatible with each others' games.
    3) If FeliCa emulation does not work, you may need to:
        a) Back up your microSD card;
        b) Synchronise your Flipper Zero with your Mobile App;
        c) Factory reset your Flipper Zero;
        d) Format your microSD card; then,
        e) Update to the latest OFW Version.
    4) There is an issue that prevents the Flipper Zero from emulating FeliCa Amusement IC Cards on Sega games.
    5) There is an issue that prevents the Flipper Zero from emulating ISO15693 e-amusement passes on Konami games.

## Arcade Payment Cards
!!! warning "**WARNING**"
    *You __should not__ be using your Flipper Zero to emulate your arcade payment card.*
``` mermaid
flowchart TD
    A[I Want to Emulate my Cashless Pre-Paid Arcade Payment Card.] -->|Check Phone| B[NFC-Capable Phone?]
    B -->|No| H{PHONE EMULATION NOT POSSIBLE. DO NOT USE YOUR FLIPPER ZERO.}
    B -->|Yes: Disabled| D(Enable NFC.)
    D -->|NFC Enabled| C
    B -->|Yes: Enabled| C[I Use...]
    C -->|Apple/Google Wallet| E[My Arcade Uses...]
    C -->|Other Wallet| H
    E -->|Embed| F(Login to Arcade's App/Member Portal.)
    F -->|Add Card to Wallet| G{Emulate Card via Wallet.}
    E -->|Other System| H
```
!!! note "**LIST OF OTHER CASHLESS PRE-PAID ARCADE PAYMENT CARDS**"
    <li>Amusement Connect</li><br><li>intercard</li><br><li>Parafait</li><br><li>RFpay</li><br><li>Sacoa</li><br><li>Tigapo</li> 
