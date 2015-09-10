---
layout: post
title: "swift lazy initialization"
description: ""
category: ios
tags: [swift]
---

```swift
    lazy var someView: UIView = {
        var result = UIView()
		//do something
        return result
    }()
```