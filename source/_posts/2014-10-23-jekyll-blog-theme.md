---
layout: post
title:  "jekyll blog theme"
date:   2014-10-23 10:06:50
categories: jekyll

---
[http://themes.jekyllbootstrap.com](http://themes.jekyllbootstrap.com)

[http://jekyllbootstrap.com/usage/jekyll-quick-start.html](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

##Find Themes

[http://themes.jekyllbootstrap.com](http://themes.jekyllbootstrap.com)


##Install Themes
	rake theme:install git="https://github.com/jekyllbootstrap/theme-the-program.git"
	
if build error is `If you haven't initialized your submodule`
* just add 
	
	[submodule "_theme_packages/theme-name"]
	path = _theme_packages/theme-name
	url = https://github.com/theme-name/theme-name.git
        ignore = dirty

* cd the submodule's directory, run `git submodule init`, then `git submodule update`.
* commit and push your changes to trigger another build on our servers.
	
	
##Switch Themes

	rake theme:switch name="the-program"