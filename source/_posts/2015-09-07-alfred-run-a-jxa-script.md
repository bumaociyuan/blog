---
layout: post
title: "alfred run a jxa script"
description: ""
category: js
tags: [jxa,alfred,applescript]
---

Add a bash script

```
osascript -l JavaScript <<"EOF"

var app = Application('Finder')
app.activate()
app.includeStandardAdditions = true
app.displayAlert('wow')

FOE
```


**Nice**

> Alfred v2.8
> 
> 21st Sep 2015
> 
>  •JavaScript is now available as a scripting language within Alfred Workflows (OS X 10.10+, using osascript)
