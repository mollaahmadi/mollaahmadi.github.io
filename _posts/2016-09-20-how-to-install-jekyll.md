---
layout: post
title: How to install jekyll?
description: installing jekyll on ubuntu
tags: jekyll blog ubuntu
comments: true
permalink: install-jekyll
sitemap:
  lastmod: 2016-09-20
---
Jekyll is a simple, blog-aware, static site generator. It takes a template directory containing raw text files in various formats, runs it through a converter (like Markdown) and our Liquid renderer, and spits out a complete, ready-to-publish static website suitable for serving with your favorite web server. Jekyll also happens to be the engine behind GitHub Pages, which means you can use Jekyll to host your project’s page, blog, or website from GitHub’s servers for free.

### Install ruby version 2

To install jekyll version 2 and later you need to install ruby version 2 or later. So you can use this way to install that on ubuntu:

```bash
sudo apt-get -y update
sudo apt-get -y install build-essential zlib1g-dev libssl-dev libreadline6-dev libyaml-dev
cd /tmp
wget http://cache.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p481.tar.gz
tar -xvzf ruby-2.0.0-p481.tar.gz
cd ruby-2.0.0-p481/
./configure --prefix=/usr/local
make
sudo make install
```

after installing requirement you can install last version of jekyll.

```bash
gem install jekyll -v "3.2.1"
```
[Head to the readme](http://stackoverflow.com/questions/16222738/how-do-i-install-ruby-2-0-0-correctly-on-ubuntu-12-04) to learn more.

