---
layout: post
title: "make a jxa build system in sublime text 3"
description: ""
category: js
tags: [jxa,sublime,applescript]
---

[SUBLIME TEXT HELP » REFERENCE » Build Systems](http://sublimetext.info/docs/en/reference/build_systems.html)

`Tools` -> `Build System` -> `New Build System...`

```
{
	"cmd": ["osascript","-l","JavaScript","$file"]
}
```

<!--more-->

