# Frequently Asked Questions
This page aims to collect frequent or common questions people may have related to the Flipper Zero.


## Flipper Zero

### Can Flipper Zero read Credit/Debit cards?
No, you cannot use Flipper to emulate your bankcard.  These cards are protected by encryption.

While the Flipper Zero used to show some public details of the card in release 0.81.1, this was later removed due to confusion from both people and companies that caused them to think the Flipper Zero might be able to 'skim' bank cards. The information the device was reading was just the unencrypted part of the card. All actual payment related functions are encrypted on the card and are impossible for the Flipper Zero to read. 

### Can Flipper Zero copy car remotes?
Short answer: No. Car remotes typically use rolling code to prevent copying to generate new codes each button press. Any attempts may cause the remote to desync, likely requiring an expensive trip to the dealer to fix your remote.

The Flipper Zero does not support the cloning of any rolling code automotive remote. 

See [this site](https://harryli0088.github.io/rolling-code/) for an example of how the basics of rolling codes work.
