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