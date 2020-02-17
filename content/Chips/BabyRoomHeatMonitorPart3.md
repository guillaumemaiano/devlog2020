---
title: "Baby Room Heat Monitor - Part 3"
date: 2017-11-19T21:37:01+02:00
draft: false

excerpt: "Communicating with the Mother(ship)"
topics: [ "arduino", "chips"]
tags: [ "SoC", "chips", "arduino", "AM2302"]
---

## Display data on a small LCD

*A few weeks ago, we went through the steps taken to check the temperature in our lovely baby's room, and connect to the Internet.*

However, it's way more practical to just look at the sensor and read HRD (human-readable data).

### Bill of Materials

An Arduino Uno, a Nano V3, a tiny 128x64 OLED display I got from AZDelivery
#### Required

- The sensor we built in a [previous post](../babyroomheatmonitor)

### What's being built?

Basically, I'm just building a tiny bit on the [external screen post](../externalscreen): I've taken the code from the baby room monitor, chucked in the code for displaying some text and boom, I can read the temperature and humidity "instantly".

I've had some trouble though: the LolIn card I intended to use crashes my Mac, the Trinket Pro cannot feed both the 5V sensor and the 3.3V screen (and playign with voltage dividers sounded ridiculously complicated compared to the original, relatively clean schematics). However, digging into the electroncis box brought back the Nano V3, which after a few tiny issues, such as requiring reinstallation of a driver (I'm running High Sierra since yesterday, and it seems to have removed the previous driver, or otherwise rendered it unusable?...) gave me a small system with a nice display!

Also, it turns out babies find tiny LEDs and long, colorful jumper cable absolutely irresistible, and that, in turn, means a lot of grabbing and pulling on carefully arranged connections... Woe betides one who programs electronics with a six-month old in his arms.

Note: I sometimes need to reboot the Mac, because the port disappears. I don't
have a clue why, but since a reboot fixes it...

### Code

I've put the simple code on [Github](https://gist.github.com/guillaumemaiano/745c95c0271e89917bfaab09c21230df).

Note: I move from pin 2 to pin 3 on the Nano because of experimenting with different cards, some of which don't use pin 2.
