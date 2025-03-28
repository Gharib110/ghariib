---
title: "An Instant Gratification Game Boy Printer"
date: 2025-01-20
---

![](https://hackaday.com/wp-content/uploads/2025/01/tinygb_feat.jpg?w=800)

When the Game Boy Printer was released back in 1998, being able to produce a hard-copy of your _Pokémon_ diploma or your latest Game Boy Camera snapshot at the touch of a button was was pretty slick indeed. But in our modern paperless society, the GB Printer somehow sticks out as even more archaic than the other add-on’s for Nintendo’s iconic handheld. Even among the folks who are still proudly playing the games that support the Printer, nobody actually wants to print anything out — although that doesn’t mean they don’t want to see the images.

The TinyGB Printer, developed by \[Raphaël BOICHOT\] and \[Brian KHUU\], could be considered something of a Game Boy Non-Printer. Powered by the RP2040 Zero development board, this open source hardware device plugs into your Game Boy and is picked up by all the games as a legitimate Printer. But instead of cranking out a little slip of thermal paper once you hit the button, the image is displayed in all its 240×240 glory on a 1.3 inch TFT display mounted to the top of the board.

Now, there’s a couple neat things going on here. First of all, because the whole process is digital, \[Raphaël\] and \[Brian\] have managed to pull out all the stops and believe they are reproducing these images in the highest fidelity possible. The images are also being simultaneously stored (as PNGs) to a micro SD card on the board, which given the file size of these images, essentially gives you unlimited storage capacity. The documentation says the code might start glitching once you’ve put tens of thousands of images on the card, but surely your sanity would give out before then.

<figure>

![](https://hackaday.com/wp-content/uploads/2025/01/tinygb_detail.jpg)

<figcaption>

Clever use of off-the-shelf modules keeps the board cheap, easy to build, and relatively compact.

</figcaption>

</figure>

The documentation looks fantastic on this project, and we love the different variations that are possible depending on how you want to build it. For example you can choose to power it with AA or AAA batteries (to match whatever your Game Boy uses), and there’s support for removing the display if you’re more interested in banking the images than viewing them on the go.

If this project seems a bit similar, it’s probably because the duo were involved in the NeoGB Printer we covered back in 2021. Between the two this new version is considerably more polished, and it’s interesting to see how the team has improved on the basic concept over the last few years.

Go to Source
