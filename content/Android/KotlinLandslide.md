---
title: "Kotlin: Global Landslides"
date: 2018-02-02T19:17:00+02:00
draft: false
cover_image: atlantis-launchpad-BIngalls.JPG
excerpt: "Creating an app displaying NASA's Global Landslides data, using Kotlin on Android" 
authorname: Guillaume Maiano
authorlink: http://guillaume.maiano.fr
authortwitter: gmaiano
authorgithub: guillaumemaiano 
authorbio: "I'm a software developer, mostly doing iOS."
topics: [ "developer", "Android", "kotlin"]
tags: ["NASA", "Open Data", "Kotlin"] 
---

# NASA Open Data

NASA is a very active member in the Open Data initiatives, and that means we get access to a treasure trove of information.

## Landslides

One of those stores of informations we get access to is the Global Landslides database, a database compiled by NASA that contains (mostly) American data, and some foreign landslide events.
What I want to do is get the data via the SODA JSON  endpoint, and display it inside an Android app.

## Kotlin

According to Google, Kotlin is a much better language than Java is, and will greatly simplify Android development. This is my attempt to delve into Kotlin and find out if it is as great a change in the Android World as the landslide event that was the advent of Swift in the Objective-C world.

## Github

I've set the app's Github repository at http://git@github.com:guillaumemaiano/LandslidesApp.git

# Development process

## First things first

I started with creating a new project in Android Studio and creating a new API key for NASA's developer APIs (it's actually a api.data.gov key). Once created, I can start using this key to make web service requests, says the NASA email. Thank you, O great Computer Server Overlord. I set that project to enable Kotlin support.
 I then activated etiennestuder's Gradle Credentials [plugin](https://github.com/etiennestuder/gradle-credentials-plugin), so as to not send my API key unto the Github repository. This requires a few lines added into the Gradle configuration, and a gradle task to tell gradle what the key is...
I used Powershell CLI (I've decided I needed to get used to Windows as a platform for Android development) to run my gradle command (it will launch .\gradlew from any android studio project folder), but I had to set `JAVA_HOME` beforehand, running Powershell as an administrator. Apparently it wasn't set in my Powershell. 

The gradle command in Powershell was `.\gradlew addCredentials --key NASA_API_Key --value maclef`.

## SODA's endpoint
 
 The landslides data is accessible at https://data.nasa.gov/resource/tfkf-kniw.json.

## Kotlin and Dagger 2

In order to use Dagger 2 with Kotlin, I need to activate Kapt in the build.gradle file.

    kapt {
      generateStubs = true
    }

I can also enable error type inferring by adding in the line `correctErrorTypes = true` after that generateStubs instruction.


# Wrap-up

### Credits
 
 The [image](https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Brightly_lit_STS-135_on_launch_pad_39a.jpg/2880px-Brightly_lit_STS-135_on_launch_pad_39a.jpg) comes from Wikimedia, was created by Bill Ingalls and I believe is originally a NASA picture. Also, it looks fantastic and has nothing to do whatsoever with landslides.

### Interesting Kotlin links

Swift [comparison](http://nilhcem.com/swift-is-like-kotlin/)

Comparison between the two from a company peddling a [translation tool](https://hackernoon.com/kotlin-and-swift-best-programming-languages-to-boost-developer-productivity-963ca8aec554). I still think platform-specific code is the correct way to go, but I fear that dream of "one-time development" will always raise its ugly head, year after year. Anyway, what's interesting is the comparison, not the tool.

Developer from San Francisco who thinks Swift/Kotlin hail a [transformative experience](https://codeburst.io/kotlin-and-swift-is-it-a-new-mobile-development-era-b4c5e81feb08) for developers
