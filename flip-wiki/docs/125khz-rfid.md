

# Low Frequency (RFID)
- the only currently supported formats are:
    ioprox
    hid prox 26 (37 coming soon)
    indala raw 26
    em4100
- low frequency credentials are read only memory. you cannot overwrite them. to create a copy of a low frequency credential you have, you will need to purchase T5577 credentials. these are chips that can pretend to be other chips 

# HID/Iclass
- Picopass iclass can be read using the picopass reader plugin 
- 26bit picopass can be downgraded to H10301 RFID credentials (note, it is not guaranteed to work if the reader is not configured to read low frequency)
- SEOS/SE/ELITE are not able to be read in detail yet due to unavailable keying
- Emulation for picopass is halted. read bettses pinned in <#954422716138676254> 
- write support for personalisation mode cards is in the pipeline

# Anything else/unknown tags
- if its not scanning and doesnt have any visible branding mentioned aboved (eg iclass) it means the type of card is not yet supported by the firmware. the devs are working their asses off to meet the hype and expectations so be patient
- the flipper is a good tool but it is not perfect and there will be things it can never do. if you are interested in researching more into RFID feel free to ping or dm me for more info on tech to look into and the RfidResearchgroup discord.