---
title: "Building a Portfolio"
date: 2017-07-24T20:30:00+01:00
draft: false
cover_image: webappBrackets.png
excerpt: "I've always liked telling stories. Sometimes, you need to tell yours, and that's called a portfolio or a CV, or maybe a book if you're an artist. As a developer, mine's a WebApp built with Ember."
authorname: Guillaume Maiano
authorlink: http://guillaume.maiano.fr
authortwitter: gmaiano
authorgithub: guillaumemaiano 
authorbio: "I'm a software developer, mostly doing iOS."
topics: [ "web", "ember", "dynamic site"]
tags: [ "SCSS", "Javascript", "Handlebars", "Openweathermap", "GoogleMaps API"]
---

***In Progress***

# Code is a good way to demonstrate code proficiency
## Building a Portfolio as a developer

I'm actually not a WebDev, I enjoy building `Objective-C` and `Swift` apps, writing C++ and building `IoT` chip-based gizmos too much to be a WebHead. However, as a true geek, I cannot ignore such a massive presence as the Web, can I?
So, here goes: I'm building my WebApp from scratch using *Ember 3*.

## How do we start?

### Learn the basics

Obviously, we start with a few tutorials and starter projects. I've put the code for the results on my Github repositories, but those aren't very interesting.

### Create a new project

That's where `ember new myProject` comes in handy. Then I've built a `partial`for a navbar using `ember g template navbar`, added a few useful libraries (found using **Ember Observer**), created keys for SNCF APIs (SNCF is the French National Train service), Google Maps and OpenWeatherMap when I realized I'd be quite satisfied to have one simple widget page showing me the traffic conditions, train statii and weather conditions around my home when leaving the office.
I then created appropriate routes and templates, but soon decided to turn them into components, so as to be able to reuse them.

