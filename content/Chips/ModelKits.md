---
title: "Model Kits"
date: 2018-03-23T16:16:45+02:00
draft: false
cover_image: content-img/dallas.jpg
excerpt: "Model kits are so much better with lighting and some magnetic magic"
authorname: Guillaume Maiano
authorlink: http://guillaume.maiano.fr
authortwitter: gmaiano
authorgithub: guillaumemaiano 
authorbio: "I'm a software developer, mostly doing iOS."
topics: [ "arduino", "chips", "models"]
tags: [ "SoC", "chips", "arduino", "lights", "reed switch", "magnet", "fiber optics"]
---

# Improving models with electronics

One of the coolest things with modern electronics is, it's dirt cheap. Therefore you can drop some in pretty much any project, like models kits.

I've got four projects in progress that have some degree of automation or SoC-controlled lighting.

## Dallas

USS Dallas, SSN 700, was a nuclear-powered attack submarine of the longest running attack class, the 688/Los Angeles class, named after her lead ship.

This model has a magnet in the nose, which can be used as a hidden switch.

## Tomcat

The Tomcat might be the most famous fighter in existence. This model has a magnet in the nose, which, just like my Dallas, can be used to trigger a reed switch. This means I just have to slightly move the model to trigger illumination of the base. Sadly, I haven't yet found the time to actually build the base, which means a lot of modeling... only the electronics work.

![Nose, separated](/images/content-img/tomcat_disassembled.jpg)

Hardware-wise, the electronics are simple: a reed switch connected to set of powered-LEDs. Since reed switches cut power entirely when the magnet's not present, it just works.

![Nose, attached](/images/content-img/tomcat_assembled.jpg)

## Aventador

The Aventador is the iconic Lamborghini of the turn of the XXIth century. This Aoshima 1:24 model is going to be a challenge because it has so many really small parts.

![Aventador](/images/content-img/aventador.jpg)

What I intend to do here is to use an Arduino connected to LEDs and some fiber optics to bring the light to the appropriate locations. I will be able to switch the lighting via bluetooth thanks to a transceiver card.

![Bluetooth transceiver](/images/content-img/bluetooth_transceiver.jpg)

This actually is the most complex project, because the model available space is very small.

## F15-J

Japan's F15, the F15-J, looks pretty awesome, and I'm building a model at 1:48. I'll use an arduino-compatible card with an integrated bluetooth transceiver here. The fun part here are the small amount of programming needed to blink the position lights (for example), and switch the lighting according to the plane state (taxiing, etc).

![Eagle](/images/content-img/eagle1.jpg)

![Eagle](/images/content-img/eagle2.jpg)

![Eagle](/images/content-img/eagle3.jpg)