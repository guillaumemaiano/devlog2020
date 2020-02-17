---
title: "Baby Room Heat Monitor - Part 2"
date: 2017-07-13T21:54:51+02:00
draft: false

excerpt: "Communicating with the Mother(ship)"
topics: [ "arduino", "chips"]
tags: [ "SoC", "chips", "arduino", "ESP8266", "AM2302"]
---

**Work in progress**


## Get our chips connected to the LAN

*A few weeks ago, we went through the steps taken to check the temperature in our lovely baby's room.*

Let's discuss how to connect our sensor to the WiFi in order to check that information from a smartphone rather from a clunky setup!

### Bill of Materials

#### Required
- The sensor we built in the [previous post](../babyroomheatmonitor)
- An ESP8266 board (ESP8266 ESP-12F WiFi Module Wireless Transceiver)
 
#### Highly recommended
- A breakout board such as the **Breakout Adapter Board TE705** I use

I've also bought some chinese boards that integrate an ESP8266 and seem easier to use, due to their integrated connector.

![Sensor on board](https://scontent-cdg2-1.xx.fbcdn.net/v/t31.0-8/20248347_1774701406154292_208822053619959621_o.jpg?oh=594f55bfea38cd74462e7486a0070b17&oe=59F9F536)
![Sensor on board seen from bottom](https://scontent-cdg2-1.xx.fbcdn.net/v/t31.0-8/20247585_1774701409487625_4080924888607043235_o.jpg?oh=2ef66520b4742723b55d2b41d7e1333d&oe=59FB9427)
![Board markings](https://scontent-cdg2-1.xx.fbcdn.net/v/t31.0-8/20369547_1774701402820959_5581223627599634299_o.jpg?oh=ee3550a68244c8c34701f07f0c87ad10&oe=5A0F1827)

The connector however uses (as seen on the picture) a CH340G USB chip, which [requires a specific driver](https://kig.re/2014/12/31/how-to-use-arduino-nano-mini-pro-with-CH340G-on-mac-osx-yosemite.html). Thankfully, on my Mac (running High Sierra), it's a `tap` and `brew cask` away. [Adrian Mihalko](http://www.mihalko.eu) is to "git(hub) blame" for this, and can be [tipped here](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=adriankoooo%40gmail%2ecom&lc=SK&item_name=Adrian%20Mihalko&currency_code=EUR&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted)! 

_Note: it might be that these boards [aren't the best choice](https://frightanic.com/iot/comparison-of-esp8266-nodemcu-development-boards/), as they are larger than the competition and apparently with a questionable "version scheme" from the chinese producer LoLin. As long as they do the job I want them to do, though, I'm happily using them._ I did find a nice [guide to help](http://henrysbench.capnfatz.com/henrys-bench/arduino-projects-tips-and-more/arduino-esp8266-lolin-nodemcu-getting-started/).

### WiFi? Yes, Sir.

The ESP8266 was initially conceived and sold as a transmitter, which means we may connect it to the Arduino and use it to communicate with our WiFi.

### Lighter is better

The reason the ESP8266 has taken the IoT by storm is it has a dedicated SoC and can replace the Arduino entirely for some low-requirement situations. Getting and transmitting heat data every few seconds is one of those situations.

#### Replacing Arduino

The Arduino is a stronger platform than the ESP8266, but in this situation, it is not necessary. While we could [use hardware interupts](https://techtutorialsx.com/2016/12/11/esp8266-external-interrupts/), we chose to use the millis-base technique in order to simulate a vague sort of multithreading. 


