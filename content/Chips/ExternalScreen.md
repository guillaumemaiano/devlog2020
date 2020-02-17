---
title: "External Screen"
date: 2017-11-19T13:25:12+02:00
draft: false

excerpt: "Displaying data to humans"
topics: [ "arduino", "chips"]
tags: [ "SoC", "chips", "arduino", "ESP8266", "AM2302"]
---

**Work in progress**

I recently got a small 128x64 display, which I'm attempting to connect to the prototyping Arduino Uno, and later to one of the smaller cards lying around in my electronics box.

### Bill of Materials

- Arduino Uno (and later, Nano V3 AVR)

###

I've connected the SCL and SCA entry ports of the display to A4 and A5 on the Uno.
Since the display requires 3.3V, I've connected `Vcc` to the 3.3V output pin on the Uno, and the ground pin to GND. Everything seems straightforward.

###

My display makes use of a `SSD_1306` controller, which can be driven via Adafruit's `Adafruit_SSD1306` library. In order to drive the display itself, I'll use another Adafruit library (Adafruit GFX). As usual, they get dl'ed via Sketch > Include Library > Manage Libraries.

I'll just get two changes before I fire up my new screen. First, I'll load up the example file for my screen size from the 1306 library examples, and switch the I2C address from Adafruit's 0x3D to 0x3C, the address used by the company that made mine. 

The library code states, precisely:

`// Address for 128x64 is 0x3D (default) or 0x3C (if SA0 is grounded)`

I'll also have to modify the screen size in the `Adafruit_SSD1306.h`file, as stated in the example, to adapt it to 64 pixel's height. The SSD1306_128_32 and SSD1306_96_16 `#define`s should be commented out, and the SSD1306_128_64 #define should be active.
