---
layout: post
title:  "用apple script写自动开启wallproxy的命令"
date:   2013-07-26 11:58:50
categories: breakwall
tags: [automator,applescript]

---

---2014.10.27---

* `Automator`->`Application`->`Run Shell Script`
如下图
<img src="/resources/2014/10/27/1.png" alt="Drawing" style="width: 800px;"/>
click `cmd+s` 
* `File Format` as `Application`
如下图
<img src="/resources/2014/10/27/2.png" alt="Drawing" style="width: 800px;"/>
* `System Preferences`->`Usres & Groups`->`Login Items`->plus button->select the app you just created

---2013-07-26---

打开 as编辑器

	tell the application "Terminal"
	do script "python /Users/noteant-3/Documents/	wallproxy-master/local/startup.py"
	close the 1st window
	end tell
	quit

save as app

右键显示包内容可以修改 icon
icon binder 可以简单生成 icon
最后在login items 加入 wallproxy app 就ok了
