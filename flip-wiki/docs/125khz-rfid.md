# Overview

## Low Frequency (RFID)
- the only currently supported formats are:
    ioprox
    hid prox 26 (37 coming soon)
    indala raw 26
    em4100
- low frequency credentials are read only memory. you cannot overwrite them. to create a copy of a low frequency credential you have, you will need to purchase T5577 credentials. these are chips that can pretend to be other chips 

## HID/Iclass
- Technically 13.56mhz like NFC, but most people see "HID" and think LF RFID
- Standard and some Elite keyed iClass fobs/cards can be read with [Picopass](https://lab.flipper.net/apps/picopass) app.
- Standard keyed iClass SE can be read with [Seader](https://lab.flipper.net/apps/seader) + some hardware.

## Anything else/unknown tags
- if its not scanning and doesnt have any visible branding mentioned aboved (eg iclass) it means the type of card is not yet supported by the firmware. the devs are working their asses off to meet the hype and expectations so be patient
- the flipper is a good tool but it is not perfect and there will be things it can never do. if you are interested in researching more into RFID feel free to ping or dm me for more info on tech to look into and the RfidResearchgroup discord.
