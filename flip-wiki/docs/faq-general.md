# Frequently Asked Questions
This page aims to collect frequent or common questions people may have related to the Flipper Zero.


## Flipper Zero

### What can the Flipper Zero do?
All of the cool things the device can do are nicely laid out in the [**official docs**](https://docs.flipper.net)!

### Can I take my Flipper Zero on an airplane?
It's completely fine to travel with your Flipper Zero to any country the device is sold in. In case you are going on an airplane and through security, here's a few tips on what you should do:

* Turn the device off and treat it like any other electronic device in your carry-on bag.
* If asked, do not lie. Tell them that the device is an electronic multi-tool.
* After landing and before using your Flipper Zero in your destination country, make sure to update via Qflipper. That way, the frequency restrictions will be updated to that country's laws and regulations.

A lot of people have flown with and passed security checks with Flippers on them before, there haven't been any reported incidents. 

### Can Flipper Zero read Credit/Debit cards?
**No, you cannot use Flipper Zero to emulate your bankcard.**  These cards are protected by encryption.

While the Flipper Zero used to show some public details of the card in release 0.81.1, this was later removed due to confusion from both people and companies that caused them to think the Flipper Zero might be able to 'skim' bank cards. The information the device was reading was just the unencrypted part of the card. All actual payment related functions are encrypted on the card and are impossible for the Flipper Zero to read. 

### What cool modules should I buy with my Flipper Zero. 

It's typically recommended to just stick with the basics (Flipper Zero + optional Wi-Fi development board) until you learn what you're doing and what things you *want* your device to do. 
Otherwise, its likely that whatever you buy will just end up in a drawer gathering dust after a few days because you dont have any good uses, or worse: because you don't know how to set up the module. 

If you know what you want, a few popular module overviews are listed in the [GPIO page](gpio-overview.md#popular-modules)

### Can Flipper Zero copy car remotes?

!!! Warning
    Attempting to clone car remotes will fail and can lead to a **VERY expensive mistake!**

Short answer: **No.** Car remotes typically use rolling code to prevent copying to generate new codes each button press. Any attempts may cause the remote to desync, likely requiring an expensive trip to the dealer to fix your remote.

The Flipper Zero does not support the cloning of any rolling code automotive remote. 

See [this site](https://harryli0088.github.io/rolling-code/) for an example of how the basics of rolling codes work.

### Can Flipper Zero copy garage remotes?
Maybe! Refer to the chart below:

``` mermaid
graph LR
  A[Start] --> B{is the remote using a supported frequency? * };
  B --> |Yes| C{Is it using a rolling code?};
  B --> |No| D[You cannot copy the remote.];
  C --> |No| F[You can likely copy the remote!];
  C --> |Yes| E{Is your rolling code supported? **};
  E --> |Yes| G[You can possibly create and pair a new remote! ***];
  E --> |No| D;
```
* [Supported Frequencies](https://docs.flipper.net/sub-ghz/frequencies)

** [Supported Rolling Codes](https://docs.flipper.net/sub-ghz/add-new-remote#3iGlU)

*** [Creating and pairing a new remote](https://docs.flipper.net/sub-ghz/add-new-remote)