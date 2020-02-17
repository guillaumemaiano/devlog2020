---
title: "Get a Devlog running... again"
date: 2017-07-19T21:00:00+01:00
draft: false
cover_image: web_hugo_dev_cover.png
excerpt: "From Wordpress to Hugo: I've used various tools to document some of my technical experiments, and this Devlog uses the latest one I've found"
authorname: Guillaume Maiano
authorlink: http://guillaume.maiano.fr
authortwitter: gmaiano
authorgithub: guillaumemaiano 
authorbio: "I'm a software developer, mostly doing iOS."
topics: [ "web", "hugo", "static site"]
tags: [ "SCSS", "Markdown", "Handlebars"]
---
# The Devlog : a modern equivalent to the Captain's Log
## Options, options

I've mostly been using pen and paper notes to log my work, jotting down notes as I went. One of the issues if the solution is that you tend not to carry the correct notebook when you need an answer. I've used a [Wordpress blog](http://www.wordpress.org) for a while to go around this limitation, then the maintenance hassle convinced me to drop it for [DayOne](http://www.dayoneapp.com). I particularly liked being able to use Markdown to save code samples in context, however when Dayone released a new app, removing that critical feature I relied on, I had to reluctantly abandon ship. A while ago, I decided to find a new option. **Hugo**, a static site generator built in Go, is my current answer.

## Handlebars, Sass and Github

Cloning **Hugo**, then cloning a few 'themes', the set of templates and CSS that governs how your site will be generated, is very simple. Writing basic markdown is as easy, though I find the quickstart docs lacking in information about the keys to use in the "front matter", the magical metadata used by **Hugo** to make sense of our markdown.

What really gets me, though, is the complexity of all nice themes I've seen. Indeed, deploying a new **Hugo** site takes seconds on top of writing the contents, but eduting the themes to tweak them? You'll need to understand the Handlebars conventions, likely use SCSS or Bootstrap, figure out partials and render commands... **Hugo** then starts looking as complex as **Ember**... The one I chose, `Hugo-Incorporated`, looks simple enough to learn. I've tweaked it a bit, but it currently lacks a lot of features from other themes, or is just broken in places. I'll come around to fixing it eventually!