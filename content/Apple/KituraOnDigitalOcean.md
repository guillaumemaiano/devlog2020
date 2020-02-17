---
title: "Kitura on Digital Ocean"
date: 2018-01-22T12:31:18+02:00
draft: false
cover_image: apple-MBP.JPG
excerpt: "Installing Kitura on my Digital Ocean node" 
authorname: Guillaume Maiano
authorlink: http://guillaume.maiano.fr
authortwitter: gmaiano
authorgithub: guillaumemaiano 
authorbio: "I'm a software developer, mostly doing iOS."
topics: [ "developer", "kitura", "setup"]
tags: [ "tooling", "developer", "digital ocean", "process", "setup"]
---

# Digital Ocean

I like Digital Ocean, an essentially cheap way of running a virtual server whenever I need one. 

## UFW

I run UFW as a firewall, enabling HTTPS, HTTP, SSH and port 8090 for Kitura.

## Requisites and steps

`sudo apt-get install git clang libicu-dev curl
uname -r
lsb_release -a
cd
curl -O https://swift.org/builds/swift-4.0.3-release/ubuntu1604/swift-4.0.3-RELEASE/swift-4.0.3-RELEASE-ubuntu16.04.tar.gz
ls
tar -xvzf swift-4.0.3-RELEASE-ubuntu16.04.tar.gz 
ls
rm swift-4.0.3-RELEASE-ubuntu16.04.tar.gz 
mkdir archives
mv swift-4.0.3-RELEASE-ubuntu16.04/ archives/`


These libs are also needed, I found them from various "bug trackers"...

`sudo apt-get install libpython2.7
sudo apt-get install openssl libssl-dev`

and we link: 
`ls archives/
ln -s archives/swift-4.0.3-RELEASE-ubuntu16.04 swift`

We can test with `swift`and quit with... `:quit`.

Then we get the necessary installs for Kitura:

`sudo apt-get install autoconf libtool pkg-config libhttp-parser-dev     libcurl4-openssl-dev libhiredis-dev libblocksruntime-dev     libkqueue-dev libpthread-workqueue-dev libbsd-dev
ls
cd archives/
git clone https://github.com/apple/swift-corelibs-libdispatch.git
ls
cd swift-corelibs-libdispatch/
sh autogen.sh 
./configure --with-swift-toolchain=~/swift/usr --prefix=~/swift/usr
./configure --with-swift-toolchain=/home/gem/swift/usr --prefix=/home/gem/swift/usr
make && make install
cd ..
curl -O "http://ftp.exim.org/pub/pcre/pcre2-10.20.tar.gz"
tar zxvf pcre2-10.20.tar.gz
ls
rm pcre2-10.20.tar.gz 
cd pcre2-10.20/
./configure && make && sudo make install
cd ..
git clone https://github.com/IBM-Swift/Kitura.git
cd Kitura
swift
cd archives/Kitura/
swift test`
