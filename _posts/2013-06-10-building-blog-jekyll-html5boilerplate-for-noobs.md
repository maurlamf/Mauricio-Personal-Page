---
title: Building a Blog/Personal Page with Jekyll for Newbies
layout: post
author: Mauricio Rivera
---

I was inspired to build this blog by Werner Vogels' [All Things Distributed](http://www.allthingsdistributed.com/). For those who are unfamiliar with Vogels, he's Amazon's CTO and he has a lot of interesting things to say. I noticed that he had build his blog with [Jekyll](http://jekyllrb.com/), which was built by one github's founders. I had never built anything of any significance, but the fact that Jekyll seemed much more elegant and simple than Wordpress or Drupal got me excited to build something even despite my impressive lack of any useful knowledge.  

I started with Jekyll and and [HTML5 Boilerplate](http://html5boilerplate.com/) in order to get some easy niceties and see how others do things. Here I'll explain how you can get started creating your own Jekyll blog. 

I will assume you have some minor experience with HTML, CSS, and the Command Line/Terminal. 

First you'll need Ruby because Jekyll is a Ruby script. For Mac users, OSX comes preinstalled with Ruby. If it's not installed, you can install it [here](http://www.ruby-lang.org/en/downloads/). 

I was working with a brand new MacBook Air, so I needed to install Command Line tools, which contains GCC - something you'll need to install Jekyll. You can either install XCode and then click Xcode > Preferences > Downloads, or you can download Command Line tools [directly here](https://daw.apple.com/cgi-bin/WebObjects/DSAuthWeb.woa/wa/login?appIdKey=d4f7d769c2abecc664d0dadfed6a67f943442b5e9c87524d4587a95773750cea&path=%2F%2Fdownloads%2Findex.action#); all you'll need is an Apple ID. 

Once you have those items installed, you can install jekyll with:

	$ gem install jekyll

If you run into an error because of an outdated version of Ruby, you can update it with:

	$ gem update --system

Once you get Jekyll installed, create any project folder and then you'll need to create the directory structure that Jekyll uses to build pages, which looks something like this:
	
	My Project/
		_layouts/
		_posts/
		_includes/
		_config.yml
		index.html

``_layouts``, ``_posts``, and ``_includes`` are all folders, while ``config.yml`` is YAML file that Jekyll gets sitewide information from. ``includes`` is technically optional, but it makes it much easier to create smaller HTML files and simply include them to create cool modular layouts. 

Once you have done all that, jump into the ``_config.yml`` and add this stuff (replace where relevant of course):

	name: "Mauricio Rivera"
	description: "Some interesting stuff"
	title: "This page is Mauricio's Page"

	url: "[YOUR DOMAIN]"

	paginate: 5

	markdown: maruku
	permalink: pretty

	authors:
	  maurrivera:
	    name: Mauricio Rivera	
	    display_name: Mauricio Rivera
	    gravatar: 
	    email: maurrivera@gmail.com
	    web: 
	    twitter: maurrivera	
	    github: maurlamf

The paginate option will generate pages and automatically paginate your stuff after whatever value you stick in there. This is useful for creating *loops*, which will allow you to spit out certain *tags* in your layout. These conventions come out of the [Liquid](http://wiki.shopify.com/Liquid) templating system, which was built by Shopify. 

A *tag* is like a taxonomy for your content, i.e., a tag could be &bsp``{{ post.content }}`` or ``{{ post.title }}``. If we create a loop that looked like this:



