---
layout: post
title:  "git on google drive"
date:   2014-06-25 10:51:50
categories: git
tags: [tutorial,google]

---

[link](http://www.iexplain.org/using-git-with-google-drive-a-tutorial/)

* Now, create a folder in your Google Drive folder called “git”. You want this folder as git produces a lot of files and you may want other stuff on your google drive besides your code repository.

```
	mkdir \Users\JoeUser\Google Drive\git
```

* CD yourself to your project folder (or whatever folder you want to have git control over).

```	
	cd \my-project-path
```

* Now, in the projects folder, perform the following git commands

```
	git init
	git add .
	git commit -m "first commit"
```

* Now we go to Google Drive and create a bare git repo (note that the backslash between Google and Drive should be exactly there)

```
	cd \Users\JoeUser\Google Drive\git
	git init --bare my-project.git
	cd \my-project-path
	git remote add origin /Users/JoeUser/Google\ Drive/git/my-project.git
	git push -u origin master
```

* To checkout this project from another machine, you simply make sure you have google drive on that machine and type

```
	cd /the_location_I_want_to_checkout_the_repo
	git clone /Users/JoeUser/Google\ Drive/git/project1.git
```