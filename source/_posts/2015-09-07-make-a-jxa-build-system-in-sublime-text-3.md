---
layout: post
title: "make a jxa build system in sublime text 3"
description: ""
category: js
tags: [jxa,sublime,applescript]
---

`Tools` -> `Build System` -> `New Build System...`

```
{
	"cmd": ["osascript","-l","JavaScript","$file"]
}
```

