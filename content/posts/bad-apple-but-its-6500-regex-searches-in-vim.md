---
title: "Bad Apple but it’s 6,500 Regex Searches in Vim"
date: 2025-01-12
---

![](https://hackaday.com/wp-content/uploads/2025/01/vim_bad_apple_nolen_royalty.jpg?w=800)

In the world of showing off, there is alongside ‘Does it play Doom?’ that other classic of ‘Does it play Bad Apple?’. Whereas either would be quaint in the context of the Vim editor, this didn’t deter \[Nolen Royalty\] from making Vim play the Bad Apple video. As this is a purely black and white video, this means that it’s possible to convert each frame into a collection of pixels, with regular expression based search and custom highlighting allowing each frame to be rendered in the Vim window.

The fun part about this hack is that it doesn’t require any hacking or patching of Vim, but leans on its insane levels of built-in search features by line and column, adjusting the default highlight features and using a square font to get proper pixels rather than rectangles. The font is (unsurprisingly) called Square and targets roguelike games with a specific aesthetic.

First 6,500 frames are fed through ffmpeg to get PNGs, which are converted these into pixel arrays using scripts on the GitHub project. Then the regex search combined with Vim macros allowed the video to be played at real-time speed, albeit at 120 x 90 resolution to give the PC a fighting chance. The highlighting provides the contrast with the unlit pixels, creating a rather nice result as can be seen in the embedded video.

https://eieio.games/images/bad-apple-with-regex-in-vim/badapple-optimized-1500-small.mp4

Go to Source
