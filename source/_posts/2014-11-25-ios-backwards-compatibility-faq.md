---
layout: post
title:  "iOS backwards compatibility FAQ"
date:   2014-11-25	14:34:50
categories: [ios]
tags: [faq]

---

# [xcode download addresses](http://bumaociyuan.github.io/xcode/2014/11/25/xcode-download-addresses.html)

# [multiple xcode coexist](http://bumaociyuan.github.io/xcode/2014/11/25/multiple-xcode-coexist.html)

# Storyboard build error

Error message

```
This version does not support constraints to layout margins. Open this document with Xcode 6.0 or later.
```
1. Select `UI.storyboard`
2. Show the file inspector
3. In `Interface Builder Document` section `Opens in` change to `Xcode 5.1`
4. Uncheck all `Constrain to margins`