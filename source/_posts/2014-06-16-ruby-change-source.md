---
layout: post
title:  "ruby change source"
date:   2014-06-16 16:06:50
categories: ruby
tags: cocoapods

---
	$ gem sources --remove https://rubygems.org/
	$ gem sources -a https://ruby.taobao.org/
	$ gem sources -l
	*** CURRENT SOURCES ***

	https://ruby.taobao.org
	# 请确保只有 ruby.taobao.org
	$ gem install rails
