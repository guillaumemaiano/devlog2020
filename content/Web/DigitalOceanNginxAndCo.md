---
title: "Certificates? Yes, but free."
date: 2018-01-23T2:02:11+01:00
draft: false
cover_image: web_hugo_dev_cover.png
excerpt: "I am working on the process of deploying a full pipeline app on a VPS, with certificates. This documents parts of the process." 
authorname: Guillaume Maiano
authorlink: http://guillaume.maiano.fr
authortwitter: gmaiano
authorgithub: guillaumemaiano 
authorbio: "I'm a software developer, mostly doing iOS."
topics: [ "web", "VPS", "Kitura", "Certificates"]
tags: [ "Digital Ocean", "VPS", "CertBot"]
---

# Certs and NGinx

https://certbot.eff.org/#ubuntuxenial-nginx

# Api Server

I use Kitura. The documentation for a simple server setup is [here](https://github.com/IBM-Swift/Kitura/blob/master/Documentation/FastCGI.md), however it is likely that one would need to also check how to have multiple hosts and configurations, for example for testing environments, for a corporate site and a customer front, etc.

# Static pages

Kitura can serve pages just fine, but it seems like a lot of work for something that's so easy to do using Hugo, with a [clean deployment process](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-hugo-site-to-production-with-git-hooks-on-ubuntu-14-04).

