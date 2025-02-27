## Arcade Data Cards
!!! warning "**WARNING**"
    *You __should not__ be using your Flipper Zero to emulate your arcade data card.*

The five main arcade data cards currently in use are:

| Company | Card | Chip | FeliCa<br>AIC | Supported<br>Games |
| ----------- | ---------- | ------------ | ----------- | ----------- |
| **Andamiro**<br>*AM* | [AM.PASS](https://am-pass.net/) | ICODE SLI<br>ICODE SLIX<br>ICODE SLIX2 | - | [Pump It Up](https://piugame.com/) |
| **Bandai Namco**<br>*BN* | [Bandai Namco Passport](https://banapass.net/setlocale/en/)<br>*Banapass / BNP* | MIFARE Classic | X | [太鼓の達人](https://donderhiroba.jp/login.php)<br>*Taiko no Tatsujin*<br>[湾岸マキシ](https://wanganmaxi-official.com/wanganmaxi6rr/en/)<br>*Wangan Maxi* |
| **Konami** | [e-amusement pass](https://p.eagate.573.jp/index.html)<br>*e-amuse / eap*| ICODE SLI | X | [DanceDanceRevolution](https://p.eagate.573.jp/game/ddr/ddrworld/top/index.html)<br>[SOUND VOLTEX](https://p.eagate.573.jp/game/sdvx/vi/) |
| **Sega** | [Aime](https://my-aime.net/en/) | MIFARE Classic | X | [CHUNITHM](https://chunithm.sega.com)<br>[頭文字D](https://initiald.sega.jp/inidac/)<br>*InitialD*<br>[maimai](https://maimai.sega.com/) |
| **Taito** | [NESiCA](https://nesica.net/) | MIFARE Ultralight | X | [MUSIC DIVER](https://musicdiver.jp/index.html)<br>[STREET FIGHTER](https://sf6ta.jp/) |

The Flipper Zero includes the MFC `Sega Aime` and `Bandai Namco Passport` access keys in the system dictionary as of OFW 0.98.2.

The `Sega Aime` parser reveals its access code.

The latter four companies have FeliCa card variants endorsed with the `Amusement IC Card [AIC]` logo.

The Flipper Zero expanded its `FeliCa` emulation support as of OFW 0.103.1.

### Arcade Data Card Emulation Compatibility
| Card | Chip | AM | BN | Konami | Sega | Taito |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| AIC | FeliCa | - | X | X | - | - | 
| Aime | MFC | - | X | - | - | - |
| AM.PASS | ICODE | X | - | - | - | - |  
| Banapass | MFC | - | X | - | - | - |
| e-amuse | ICODE | - | - | - | - | - |
| NESiCA | MFU | - | - | - | - | X |

### Arcade Data Card Emulation Compatibility Notes
- If FeliCa emulation does not work, you firstly need to:
    1. Back up your microSD card;
    1. Reboot your Flipper Zero;
    1. Synchronise your Flipper Zero with your [Mobile App / qFlipper](https://flipperzero.one/update);
    1. Update to the latest OFW Version; then,
    1. Update any installed Apps;
- If FeliCa emulation *still* does not work, you then need to:       
    1. Back up your microSD card;
    1. Format your microSD card;
    1. Factory reset your Flipper Zero;
    1. Re-connect your Flipper to your [Mobile App / qFlipper](https://flipperzero.one/update);
    1. Re-update to the latest OFW Version; then,
    1. Re-install any external Apps.
- There is an issue that prevents the Flipper Zero from emulating:
    1. FeliCa `Amusement IC Cards` on `Sega` games;
    1. ICODE SLI `e-amusement pass` cards on `Konami` games;
    1. MFC `Aime` cards on `Sega` games; and,
    1. MFC `Bandai Namco Passport` cards on `Sega` games.
- Emulation compatibility cannot be tested for `Taito` games without further assistance from Members located within Japan.
- The ICODE SLI `e-amusement pass` cards are not compatible with `Andamiro` games *and vice versa*.

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
    <li>Amusement Connect</li><li>intercard</li><li>Parafait</li><li>RFpay</li><li>Sacoa</li><li>Tigapo</li> 
