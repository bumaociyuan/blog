---
layout: post
title: "swift lazy initialization"
description: ""
category: ios
tags: [swift]
---

```swift
    // {#code#}() 是执行闭包函数
    lazy var someView: UIView = {
        var result = UIView()
		  //do something
        return result
    }()

    // lazy 是延迟加载的关键字，也可以直接用
    
    lazy var someView: UIView = UIView()
    
    // 或者
    
    lazy var someView: UIView = SomeViewController.setupSomeView()
    
    static func setupSomeView() -> UIView {
    	// setup someView
    	return someView
    }
```