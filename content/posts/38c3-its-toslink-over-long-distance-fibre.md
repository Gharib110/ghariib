---
title: "38C3: It’s TOSLINK, Over Long Distance Fibre"
date: 2025-01-08
tags: 
  - "data"
  - "tech"
  - "ui"
  - "un"
---

![](https://hackaday.com/wp-content/uploads/2025/01/fibre-toslink-featured.jpg?w=800)

If you’ve owned a CD player or other piece of consumer digital audio gear manufactured since the 1980s, the chances are it has a TOSLINK port on the back. This is a fairly simple interface that sends I2S digital audio data down a short length of optical fibre, and it’s designed to run between something like a CD player and an external DAC. It’s ancient technology in optical fibre terms, with a lowish data rate and plastic fibre, but consider for a minute whether it could be adapted for modern ultra-high-speed conenctions. It’s what \[Ben Cartwright-Cox\] has done, and he delivered a talk about it at the recent 38C3 event in Germany.

if you’ve cast you eye over any fibre networking equipment recently, you’ll be familiar with SFP ports. These are a standard for plug-in fibre terminators, and they can be had in a wide variety of configurations for different speeds, topographies, and wavelengths. They’re often surprisingly simple inside, so he wondered if he could use them to carry TOSLINK instead of a more conventional network. And it worked, with the simple expedient of driving an SFP module with an LVDS driver to make a differential signal. There follows a series of experiments calling in favours from friends with data centre space in various locations around London, finally ending up with a 140 km round trip for CD-quality audio.

It’s an interesting experiment, but perhaps the most value here is in what it reveals to us about the way optical networking systems work. Most of us don’t spend our days in data centres, so that’s an interesting technology to learn about. The video of the talk itself is below the break.

<iframe title="38C3 - Going Long! Sending weird signals over long haul optical networks" width="800" height="450" src="https://www.youtube.com/embed/3qojgJGtTos?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Go to Source
