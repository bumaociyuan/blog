---
layout: post
title:  "multiple xcode coexist"
date:   2014-11-25	09:15:36
categories: [xcode]
tags: []

---

[Can Xcode 6 and Xcode 5 coexist on the same computer?](http://stackoverflow.com/questions/24005297/can-xcode-6-and-xcode-5-coexist-on-the-same-computer)

1. Rename the origin `Xcode` to `Xcode6`.
2. Download Xcode5.dmg drag `Xcode` into `Desktop` folder.
3. Use `sudo xcode-select -s /Applications/Xcode.app` to switch between them.