---
title: "Babyroom Heat Monitor"
date: 2017-07-03T13:00:13+02:00
draft: false
cover_image: arduino-GabrielTemp1.JPG
excerpt: "How shall I check the temperature in my baby's room? With chips, of course!"
authorname: Guillaume Maiano
authorlink: http://guillaume.maiano.fr
authortwitter: gmaiano
authorgithub: guillaumemaiano 
authorbio: "I'm a software developer, mostly doing iOS."
topics: [ "arduino", "chips"]
tags: [ "SoC", "chips", "arduino", "DHT22", "AM2302"]
---

## How hot is it really here?

*As a new Dad, I face a critical question all the time. How much clothing should my baby be wearing right now?*

That question, thankfully, has an answer that relies on three variables: temperature, current state of said baby, and wardrobe items still available. Of the three, only the first interests us here. How shall I check the temperature in my baby's room?

### Bill of Materials

#### Required
- A 10nF resistor
- A tiny 104 condensator
- An AM2302 heat and humidity sensor
- An Arduino board (or equivalent)

Note that the sensor used here is very cheap, but rather slow, and with a limited range of temperature use. It is quite appropriate for my situation, but if you intend to build yourself a suit of armor and check the exhausts, it won't be.

#### Useful
- A breadboard
- Pluggable connectors

## Let's talk to that chip!

I'm using the [Arduino IDE](http://www.arduino.cc), and I'll use some libraries (the Adafruit Unified sensor library, which is a requirement for the Adafruit DHT Sensor library, which I'll also need). To install them, go to the Sketches menu, "Add a library" > "Manage libraries".

### The circuit


#### The code

In this initial version, we'll get the data from the DHT22 sensor and print it to the IDE console. Later on, we'll also blink the LED whenever there is an issue with the sensor.

    #include "DHT.h"
    #define DHTTYPE DHT22 // AM2302
    #define DHTPIN 2 // subject to change

    struct TemperatureHumidityDataPoll {
      float temp;
      float humi;
      bool isFailed; 
     };

    DHT dht(DHTPIN, DHTTYPE);

    void setup() {
    
        Serial.begin(9600);
        dht.begin();
    }

    struct TemperatureHumidityDataPoll pollTemperature(bool now) {
      // wait between polls
      if (!now) {
        delay(5000);
      }
      // data reads take around 250ms
      // sensor data might be off by 2 seconds 
      // (slow cheap sensors)
      float h = dht.readHumidity();
      // T in Celsius
      float t = dht.readTemperature();
  
      // declares the data structure to be returned
      struct TemperatureHumidityDataPoll pollData;
      pollData.isFailed = (isnan(h) || isnan(t));
      if (!pollData.isFailed) {
        pollData.temp = t;
        pollData.humi = h;  
      }
      return (pollData);
    }
 
    void relayPollingErrors() {
      // write to serial
      Serial.println("Failed to poll DHT sensor!");
    }
 
    void loop() {
     struct TemperatureHumidityDataPoll dataPolled = pollTemperature(false);
      if (dataPolled.isFailed) {
        // immediate retry once
        dataPolled = pollTemperature(true);
        if (dataPolled.isFailed) {
        // things went South, call Houston
        relayPollingErrors();
        }
      }
      if (!dataPolled.isFailed) {
        Serial.print("Humidité: "); 
        Serial.print(dataPolled.humi);
        Serial.print(" %\t");
        Serial.print("Température: "); 
        Serial.print(dataPolled.temp);
        Serial.println(" °C ");
      }
     }
     
## Next step

Let's now add blinking if the sensor read fails! 

Note: we'll need to [drop the delay()](http://www.makeuseof.com/tag/arduino-delay-function-shouldnt-use/) call we had been using, because it is a blocking call and will prevent us from reacting!

For that, there are two techniques.

- One is known as protothreading, which basically emulates multithreading by faking interrupts. Your fastest thread will check whether other threads requested execution time whenever going through its loop, and each thread will have a time interval for its execution.
- The second [technique](https://www.arduino.cc/en/Tutorial/BlinkWithoutDelay) relies on checking execution time and is much simpler.

Some Arduinos also allow interrupts (software/hardware), which allows [another technique](http://playground.arduino.cc/Code/Interrupts).

We'll use the second technique because we'll later [switch to a smaller platform](../babyroomheatmonitorpart2), and I'd like to keep things simple.

## Bibliography

- [Blinking LEDs](https://learn.adafruit.com/adafruit-arduino-lesson-2-leds/blinking-the-led)
- [Connecting DHT sensors](http://www.electroschematics.com/11291/arduino-dht22-am2302-tutorial-library/)
- [DHT datasheet](https://cdn-shop.adafruit.com/datasheets/Digital+humidity+and+temperature+sensor+AM2302.pdf)
- [Protothreading](https://create.arduino.cc/projecthub/reanimationxp/how-to-multithread-an-arduino-protothreading-tutorial-dd2c37)