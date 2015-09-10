---
layout: post
title:  "block note"
date:   2014-09-29 11:13:52
categories: ios
tags: tutorial

---

**use block as local var**

	 void (^someBlock)(NSMutableArray *,id) = ^(NSMutableArray *items,NSString *item) {
			//do some thing
	 };
	     
	 someBlock(items, item);
	    
**use block as type**

1

	@property (nonatomic, strong) returnType(^propertyName)(arguments);
	
	e.g.
	@property (nonatomic, strong) void(^onSelectedCustomer)(NSArray *customers);
	
2

	typedef returnType(^name)(arguments);
	
	e.g.
	typedef void(^BlockType)(id);
	@property (nonatomic, strong) BlockType block;
	
**use block as method parameter**
	
	- (void)methodWithBlock:(returnType(^)(arguments))block

	e.g.
	- (void)loginAnimated:(BOOL)animated completion:(void(^)(void))completion failed:(void(^)(void))failed;