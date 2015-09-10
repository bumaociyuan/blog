---
layout: post
title: "switch in swift"
description: ""
category: ios
tags: [swift]
---

###swift

```swift

var testVar = 1
var result = 0

switch(testVar) {
case 0:
    fallthrough
case 1:
    result = 1
default:
    result = 3
}

```

###objc

```objc

int testVar = 1;
int result = 0;

switch(testVar) {
case 0:
case 1:
    result = 1;
break;
default:
    result = 3;
break;
}

```
