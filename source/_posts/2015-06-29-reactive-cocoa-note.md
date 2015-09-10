---
layout: post
title: "reactive cocoa note"
description: ""
category: ios
tags: []
---

[Observe textField.text changing](https://github.com/ReactiveCocoa/ReactiveCocoa/issues/765)

```objc
	//only RACObserve(self.textField, text) or self.textField.rac_textSignal will not working
    RACSignal *textFieldTextSignal = [RACSignal merge:@[RACObserve(self.textField, text),self.textField.rac_textSignal]];
    
    [textFieldTextSignal subscribeNext:block];

```

Combine two signals

```objc
	
	void(^block)(RACTuple *) = ^(RACTuple *tuple) {
		NSString *x = tuple.first;
        NSString *y = tuple.second;
        //do something
    };
	
	[[RACSignal combineLatest:@[signal1,signal2]] subscribeNext:block];

```