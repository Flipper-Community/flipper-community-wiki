# Overview

## Low Frequency (RFID)
- Don't expect to edit/rewrite low frequency credentials.  They are generally read only, passworded, or a type of tag the flipper zero doesn't work with.  To create a copy of a low frequency credential you have, you will need to purchase T5577 credentials. these are chips that can pretend to be other chips.

## Kyber crystals

These are EM4305, but show up looking like EM4100.  You can't fully emulate or clone them.

## HID/Iclass
- Technically 13.56mhz like NFC, but most people see "HID" and think LF RFID
- Standard and some Elite keyed iClass fobs/cards can be read with [Picopass](https://lab.flipper.net/apps/picopass) app.
- Standard keyed iClass SE can be read with [Seader](https://lab.flipper.net/apps/seader) + some hardware.

## Anything else/unknown tags
- if its not scanning and doesnt have any visible branding mentioned aboved (eg iclass) it means the type of card is not yet supported by the firmware. the devs are working their asses off to meet the hype and expectations so be patient
- the flipper is a good tool but it is not perfect and there will be things it can never do. if you are interested in researching more into RFID feel free to ping or dm me for more info on tech to look into and the RfidResearchgroup discord.
