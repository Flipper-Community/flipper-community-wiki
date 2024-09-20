# Overview

## Low Frequency (RFID)
- Don't expect to edit/rewrite low frequency credentials.  They are generally read only, passworded, or a type of tag the flipper zero doesn't work with.  To create a copy of a low frequency credential you have, you will need to purchase T5577 credentials. these are chips that can pretend to be other chips. 
- "I was able to write the ID on it but when i try another file it says error" you aren't writing anything, writing the content that was already on the chip, to the chip, makes the flipper thinks it was successful in it's write when it performs a read to validate the `new` ID is on the chip, which it is because it was already there. 
- - When purchasing T5577s, try to buy from listings that only mention T5577, if you buy from a listing that says T5577/EM4305 you may receive EM4305s and those cant be written to by the flipper.

## Kyber crystals

These are EM4305, but show up looking like EM4100 because EM4305 are emulator chips and they've been pre-configured with the kyber crystal ID.  You can't fully emulate or clone them, emulation is known to work with the holocron but not with the sabers themselves. You cant clone these to T5577s like most other LF RFID chips due to the sabers checking the EM4305 memory pages with specific commands the T5577 doesnt comply with. The flipper does not (currently) support writing to EM4305s, it is currently thought to be impossible with the flipper's hardware but the impossible has been overcome before so who knows if we will see it in the future. 

## HID/Iclass
- Technically 13.56mhz like NFC, but many people see "HID" and think LF RFID
- Standard and some Elite keyed iClass fobs/cards can be read with [Picopass](https://lab.flipper.net/apps/picopass) app.
- Standard keyed iClass SE can be read with [Seader](https://lab.flipper.net/apps/seader) + some hardware.

## Anything else/unknown tags
- if its not scanning and doesnt have any visible branding mentioned aboved (eg iclass) and you have also had no success reading it with the NFC or [Picopass](https://lab.flipper.net/apps/picopass) app, it means the type of card is not yet supported by the firmware. the devs are working their asses off to meet the hype and expectations so be patient; you can aide in bringing attention to this lack of support by filing a [github issue](https://github.com/flipperdevices/flipperzero-firmware/issues) including as much information as you have regarding the credential and reader including make & model & brand, filing a github issue does not ensure the support will be added quickly it just brings it to the attention of the devs & community developers who may be able to assist. 
- the flipper is a good tool but it is not perfect and there will be things it can never do. if you are interested in researching more into RFID feel free to join the Flipper discord and engage with the `#125khz-rfid` channel. 
