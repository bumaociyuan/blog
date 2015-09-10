---
layout: post
title: "install meld on mac"
description: ""
category: 
tags: []
---

[gist](https://gist.github.com/p1nox/6102015)

[dmg](https://github.com/yousseb/meld/releases/tag/osx-v1)

[How To Run Meld on Mac OS X Yosemite Without Homebrew, MacPorts, or Think](http://www.alexkras.com/how-to-run-meld-on-mac-os-x-yosemite-without-homebrew-macports-or-think/)

```
$ brew install homebrew/x11/meld

#config git no backup and using meld for git mergetool
$ git config --global mergetool.keepBackup false
$ git config --global merge.tool meld
```