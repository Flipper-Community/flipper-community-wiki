# Flipper Zero Asset Creation Tools Guide  
A guide of all time that focuses on animation tools by [pr3](https://github.com/the1anonlypr3)!
## I Need Software! 
The real truth about Flipper animation is that you can use just about any software to create pixelart! No joke, I started with Microsoft Paint. Many people use many different softwares, however the usefulness those softwares are only depends on whether they have certain features.  It cannot be stressed enough that you can use **anything!** Find your preference!

!!! note
    My preferred software is [Aseprite](https://www.aseprite.org/), and I'll be using it along with a custom firmware for the sake of demonstration and preference. However, this guide can be applied to just about any firmware or art software. (If you use a terrible art software and a terrible firmware it's your fault)

###  ‣ Art Softwares + Their Features
Although technically you can use any art software to create pixelart, the silver lining is that some more dedicated softwares **heavily** streamline the animation workflow. Some people even use entirely web-based platforms to make their pixelart! the beauty of flipper pixelart is in the diversity of not only art style/visuals, but how those visuals were made. 

!!! tip "Key:"
    ⭐ Software I have used and recommend.<br>
    ❓ Software which I haven't used/haven't used enough to form an opinion, but you should consider them.<br>
    ❌ Calling this software terrible is being nice.

### ‣ Non Web-Based Software
??? "⭐ Aseprite"
  
    - **Heavily** pixelart oriented. My personal favourite software.
    - Absolute epitome of a streamlined user-friendly experience - easy frame/layer swapping, editing and exporting, wondrous tools and easy-to-learn keybinds.
    - Open source - you can buy it [on their site](https://aseprite.org), on [steam](https://store.steampowered.com/app/431730/Aseprite/) or [build it yourself!](https://github.com/aseprite/aseprite)

??? "⭐ GIMP: Of Course I Included It."
  
    - [GIMP](https://www.gimp.org/downloads/) is a free and open source software, regarded by many as "free PhotoShop".
    - Although it's free and open source, it is great for pixel art due to it's arsenal of features and built-in animation player among other things. 

??? "❓ Adobe Photoshop: "Like driving an F1 car to the grocery shop" - Kuronons"
  
    - Professional tool - much less user-friendly, and takes a lot of getting used to. 
    - Great for things such as resizing and editing frames, however lacks in animation integration compared to software like Aseprite; some manual aspects. 

??? "❌ Microsoft Paint"
  
    - **Much** less pixelart oriented
    - **Many** manual aspects, such as changing between frames and terribly clunky keybinds meaning you'll move your mouse **a lot**.
    - An *alright* free software for starting out, however you will *definitely* want more once you're acquainted with pixelart.

### ‣ Web-Based Software
??? "⭐ EzGIF"
  
    - [EzGIF](https://ezgif.com) is a web-based art platform, but unlike [Photopea](https://photopea.com), it is more for grabbing frames from `.gif` files. 
    - [EzGIF](https://ezgif.com) is much better for grabbing the frames from a `.gif` and saving them to edit using one of the above softwares. It doesn't have an editor where you can change the physical pixels in each frame, however you can apply "filters" to whole GIFs. 
    - Personally, [EzGIF](https://ezgif.com) is one of the softwares I first used to get the gist of animation. Before i starting Flipper animation, the only animation experience i had was stop-motion! 

??? "⭐ Piskel"
  
    - [Piskel](https://www.piskelapp.com/) is a free, open source web and offline plaform for creating animations and sprites that is surprisingly well catered for pixelart.
    - It works similarly to Aseprite, but web-based (obviously...), and it includes many of aseprite's useful tools, with keybinds for each as well. 

??? "❓ Lopaka"
  
    - [Lopaka](https://lopaka.app/sandbox) is another web-based art platform tailored for the Flipper among other devices. 
    - It includes many pre-made assets that are used in Flipper's firmware, and includes basic tools such as layers, among other things.
    - Similar to Photopea, it's much better for small edits or creating menus since it lacks frame management. 

??? "❓ Photopea"
  
    - [Photopea](https://photopea.com) is a web-based art platform similar to Photoshop. 
    - It's better for single frame editing, and catching those slight details. 

<br>

!!! note
    **Web-based software** can have more latency/less reliability compared to local software, and can lack in some features. However, the convenience/unique tools on web-based art softwares are exceptionally useful. <br>
    **Local softwares** are my personal preference, and are essentially the opposite of web-based software. 

## I Chose a Software, What Now?
### ‣ Learn!
Now you create, experiment, and learn! Obviously, [YouTube](https://www.youtube.com/) has some wonderful tutorials from various channels. I also recommend looking at [Pinterest](https://pinterest.com/) for inspiration. Enjoy your learning experience! Pixelart is a huge journey. There's a plethora of pixelart techniques, so why not learn them all! Please note Aseprite has many tools for techniques such as dithering, making pixel perfect lines, and making basic shapes, which makes things a lot easier. 

## Viewing Your Animation
[Ooggle's Flipper Animation Manager](https://github.com/Ooggle/FlipperAnimationManager) is **the** tool for previewing animations. It includes necessary features such as a GUI, a compilation tool, previews based on butthurt/level, and other useful features. 

!!! note 
    Flipper Animations only take `.bm` files **for animations**, which are converted from 128x64px `.png` files. Flipper typically handles around 50-60 frames per animation and maximum of around 9fps before it crashes. 

### ‣ Compiling Frames
??? "⭐ asset_packer.py"
  
    - [WillyJL](https://github.com/Willy-JL)'s [asset_packer.py](https://github.com/Next-Flip/Momentum-Firmware/blob/dev/scripts/asset_packer.py) is a great quick and easy tool for compiling asset packs. 
    - Easy to use, and compiles blisteringly fast. I highly reccommend this tool! 

??? "⭐ Flipper Animation Manager"
  
    - [Ooggle's FlipperAM](https://github.com/Ooggle/FlipperAnimationManager) has a great built in compiler, complete with a GUI. 
    - The perfect suite for viewing and compiling animations on the fly. Zero complaints. 

??? "❓ FBT"
  
    - [Flipper Build Tool](https://github.com/flipperdevices/flipperzero-firmware/blob/dev/documentation/fbt.md) is a solid tool with simple installation - just clone the [OFW repo](https://github.com/flipperdevices/flipperzero-firmware)!
    - a bit overkill if you just want to compile some animations, but you'll need it if you want to compile for OFW. 
    - Compile animations in one command with `./fbt icons proto dolphin_internal dolphin_ext resources`.
    - TalkingSasquach has a [great video](https://www.youtube.com/watch?v=trpcZLlJtNw&t=1601s) on compiling with FBT. Follow it if you're compiling for the first time. 

!!! warning "Warning:  Use Only the Above Tools!"
    Compilation tools other than the ones stated above seem to produce broken images as the final product, hence you shouldn't consider using them to compile. Don't overcomplicate it! 