---
layout: post
title: "NSAssert note"
description: ""
category: ios
tags: []
---


```objc
NSAssert(condition, desc, ...)
//if condition is true ,app will crash , log outputs desc
```

disable NSAssert in `release` mode

in `Build Settings` -> `Preprocessor Macros` add `NS_BLOCK_ASSERTIONS` to `release` section


