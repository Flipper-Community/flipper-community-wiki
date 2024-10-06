## Arcade Data Cards
!!! warning "**WARNING**"
    *You __should not__ be using your Flipper Zero to emulate your arcade data card.*

The five main arcade data cards are:

| Company | Card | Chip | FeliCa<br>AIC | Notable Games |
| ----------- | ---------- | ------------ | ----------- | ----------- |
| **Andamiro** | [AM.PASS](https://am-pass.net/) | ICODE SLI<br>ICODE SLIX<br>ICODE SLIX2 | - | [Chrono Circle](https://chrono-circle.com/)<br>[PIU](https://piugame.com/) |
| **Bandai Namco** | [Bandai Namco Passport](https://banapass.net/setlocale/en/) | MIFARE Classic | X | [Taiko](https://donderhiroba.jp/login.php)<br>[WM6RR](https://wanganmaxi-official.com/wanganmaxi6rr/en/) |
| **Konami** | [e-amusement pass](https://p.eagate.573.jp/index.html)| ICODE SLI | X | [DDR](https://p.eagate.573.jp/game/ddr/ddrworld/top/index.html)<br>[SDVX](https://p.eagate.573.jp/game/sdvx/vi/) |
| **Sega** | [Aime](https://my-aime.net/en/) | MIFARE Classic | X | [IDAC](https://initiald.sega.jp/inidac/)<br>[maimai](https://maimai.sega.com/) |
| **Taito** | [NESiCA](https://nesica.net/) | MIFARE Ultralight | X | [MUSiCDiVER](https://musicdiver.jp/index.html)<br>[SF6TA](https://sf6ta.jp/) |

The Flipper Zero includes the `Sega Aime` and `Bandai Namco Passport` access keys in the system dictionary as of OFW 0.98.2, with the `Sega Aime` parser for revealing the corresponding access code.

The latter four companies have FeliCa card variants endorsed with the `Amusement IC Card [AIC]` logo, with the Flipper Zero having expanded its `FeliCa` emulation support as of OFW 0.103.1, and emulation compatibility is listed below:

### Arcade Data Card Emulation Compatibility
| Card | Chip | Andamiro | Bandai<br>Namco | Konami | Sega | Taito |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| Sega Aime | MFC | - | X | - | - | - |
| AM.PASS | ICODE SLI<br>ICODE SLIX<br>ICODE SLIX2| X | - | - | - | - |  
| Amusement IC | FeliCa | - | X | X | - | - | 
| Banapassport | MFC | - | X | - | - | - |
| e-amusement | ICODE SLI | - | - | - | - | - |
| NESiCA | MFU | - | - | - | - | - |

### Arcade Data Card Emulation Compatibility Notes
- If FeliCa emulation does not work, you may need to:
    1) Back up your microSD card;
    2) Synchronise your Flipper Zero with your Mobile App;
    3) Factory reset your Flipper Zero;
    4) Format your microSD card; then,
    5) Update to the latest OFW Version.
- There is an issue that prevents the Flipper Zero from emulating:
    1) FeliCa `Amusement IC Cards` on `Sega` games;
    2) ICODE SLI `e-amusement pass` cards on `Konami` games;
    3) MFC `Aime` cards on `Sega` games; and,
    4) MFC `Bandai Namco Passport` cards on `Sega` games.
- Emulation compatibility cannot be tested for `Taito` games without assistance from Members located within Japan.
- The ICODE SLI `e-amusement pass` cards are not compatible with `Andamiro` games.

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
