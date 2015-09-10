---
layout: post
title: "How to make UIButton outside superview clickable"
description: ""
category: ios 
tags: []
---

in superview.m file 

```objc
- (BOOL)pointInside:(CGPoint)point withEvent:(UIEvent *)event {
        if (CGRectContainsPoint(self.bounds, point) ||
				CGRectContainsPoint(self.outsideButton.frame, point)) {
				return YES;
		}
                            
		return NO;
}
```
