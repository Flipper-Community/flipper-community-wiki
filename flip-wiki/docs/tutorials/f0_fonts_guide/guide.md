# How to create custom fonts for the Flipper Zero

Guide credited to EntranceJew

*"I spent two days trying to do this mess so you're going to learn something."*

This guide aims to show how a custom font can be created for the Flipper Zero, with Microsoft Windows as the OS used.

## Pixelfont

Download and open [pixelfont](https://yellowafterlife.itch.io/pixelfont) in your browser 

Before you import your image, really study how this is laid out, the default example is really helpful on how you should plan to draw your own font.

## Aesprite your font

This part is painful.

1. Find find your largest character, make sure each letter of your font is on a grid with an equal amount of room as that one.
1. If you have a baseline, be sure to account for that with your tile size in regards to how each character is positioned within the tile.
1. You can work with layers or tags but most auto-tools are going to expect a long "tile sheet" where each character is visible in rows/columns of equal size.
1. Make sure to set up your grid to help you out:

![aesprite_photo](aseprite_grid.png)

## Back to pixelfont
1. Pick an image (your export from aesprite)
1. Type out the glyphs in the image in the order they appear
	- ***NOTE:*** save this somewhere, we're going to want to have this later!
1. Set the `tile width` / `tile height` to match the largest character
1. Adjust the baseline to be `the height of your pixel font` as your starting point:
	1. If all your characters are equally tall (reach the top and bottom) then you don't need to do anything
	1. If you have characters that are like a lowercase "y" which is 2 pixels lower than every other character / the only one that touches the bottom of its tile, then make this box equal to the height of a tile minus the distance between a regular letter's bottom (like `h`) to the tile's bottom. 
	1. If your font was 5 pixels tall, but your y goes 2 pixels lower than every other character, then you'd type 3 here
1. If you set up kerning pairs then you probably don't want to click `Monospace`
![pixelfont](pixelfont_setup.png)
1. If there is a reason to change anything on the output page, I do not know it.
1. Fill out your Meta page, then hit `Save TTF`

## FontForge cleanup
This part was mostly cited from [https://github.com/projectitis/packedbdf/blob/master/README.md](https://github.com/projectitis/packedbdf/blob/master/README.md) verbatim but I had to change a few parts in order to make it accurate for me, on windows, trying to make fonts for the Flipper Zero.

1. Download and install [Font Forge](https://fontforge.github.io/en-US/downloads/)
1. Launch Font Forge and open the font file (ttf tends to keep kerning pairs better?)
1. _Edit > Select > Glyphs Worth Outputting_ 
	1. You can do _Element > Overlap > Remove Overlap_ at this stage to simplify the geometry of your pixel font.
	1. Other [Validation](http://designwithfontforge.com/en-US/The_Final_Output_Generating_Font_Files.html) steps may impact your font if you set up kerning pairs in the pixelfont tool, it relies on boundaries being set up a specific way with the font so fixing "declared widths" may cause more problems for you.

It is recommended you remove Glyphs you have no concern with, you can do this via the following:

1. *Edit > Select > Invert* the selection (to select the glyphs you don't want to keep), and
1. *Encoding > Detach and remove Glyphs* to remove them from the font
	- This might not work if you have something invalid in your selection, like something you can't remove.
1. You can check what is still inside your font if you select *Encoding > Compact* to reduce the character set, but I recommend turning it back off prior to generating fonts.

The next few steps will generate the bitmaps/pixel versions of each glyph in the sizes that you need:

1. _Element > Bitmap strikes available_ launches the dialog to generate the bitmap versions
	1. Select `Win`,
	1. Type in the pixel height of a single character of your font in the `Point sizes on a 120 dpi screen` 
		- e.g. `5` will automatically populate into => `Pixel Sizes: 8`
1. Click *[OK]* to generate the bitmap strikes of each glyph in various sizes
1. Finally, select _File > Generate Fonts_
    - Select "No outline font" (for Outline font) and "BDF" (for Bitmap font), then hit \[Generate\].
    - Enter 120dpi as the screen resolution (also see step 7). This ensures that the font sizes are correct inside the files.
1. A BDF file with the pixel size will be generated.
1. I recommend you save your current project as a `sfdir` in case you need to tweak it later.

## u8g2 Unifont Helper

1. Visit [u8g2 Unifont helper](https://stncrn.github.io/u8g2-unifont-helper/)
1. Paste your glyph string from earlier in pixelfont into the `Individual characters` section
	- If you don't have it anywhere, open up the TTF in FontForge and without the encoding collapsed, take note of the number of the glyphs that you have in your font
	   ![fontforgeSetup](fontforge_setup.png)
1. Change the input filename to whatever FontForge saved, e.g. `DootieMicroStats-8.bdf`
1. Run the command line (install the bdfconv linked at the top if you don't have a copy)
	- You will probably need to prefix most things with a path otherwise the source file will output next to `bdfconv.exe`
1. Verify that the rendered TGA matches the tile height of your font from the earlier steps ![config](bdfconv_output.png)

## Clean the output
bdfconv exports some extra junk you don't need.
![configresult](bdfconv_result.png)
You can get rid of the `U8G2_FONT_SECTION` stuff highlighted above.

I also got rid of the absolute array length because I was dialing in a lot of tests trying to find 1:1 pixel ratio

## Test it out
[the default example_custom_font](https://github.com/flipperdevices/flipperzero-firmware/tree/dev/applications/examples/example_custom_font) Flipper Zero provides in an example is a good spot to transplant the results from `YourFontName.c` to demo things.
![fontTestimg](tested_font.png)

Looks like all my kerning test samples worked.