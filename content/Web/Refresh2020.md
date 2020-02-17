---
title: "Blog Refresh!"
date: 2020-02-16T2:10:11+01:00
draft: false
excerpt: "The tools used to build this devblog had become a bit stale, so I updated them to more modern versions and changed the theme to Aether when I made the site conform to 2020-standards of security."
authorname: Guillaume Maiano
authorlink: http://guillaume.maiano.fr
authortwitter: gmaiano
authorgithub: guillaumemaiano 
authorbio: "I'm a software developer, mostly doing iOS."
topics: [ "aether", "hugo", "certificates", "SSL"]
tags: [ "Digital Ocean", "NGinx", "CertBot", "Hugo", "aether"]
---

# Hugo and Aether

A little while ago, I realized my certbot installations running on my [Digital Ocean](https://www.digitalocean.com) servers needed some updating. After some digging, I decided to go nuclear on my various servers and rebuild everything from a clean slate, using Nginx instead of Apache, since my Web servers all run static sites. It quickly became clear that, once my servers passed the A+ grade of [SSL Labs](https://ssllabs.com) testing, I needed to refresh my knowledge of [Hugo](https://www.gohugo.io), which had moved on quite a lot. This, in turn, led to the realization that my themes of choice had mostly been retired.

After some digging, I decided to move the devblog over to [Aether](https://themes.gohugo.io/aether/), a nice and crisp theme, learn how to build my [own theme](https://www.zeolearn.com/magazine/develop-a-theme-for-hugo), and learn the ropes of the powerful [Syna](https://syna.okkur.org) theme.

I'm version-controlling my work, as usual, on [Github](https://github.com/guillaumemaiano/devlog2020).
