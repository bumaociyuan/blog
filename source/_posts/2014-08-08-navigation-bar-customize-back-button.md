---
layout: post
title:  "navigation bar customize back button"
date:   2014-08-08 11:09:00
categories: ios

---

July 21, 2015
[iOS开发的一些奇巧淫技](http://blog.csdn.net/justinjing0612/article/details/42294329)

```objc
self.navigationItem.leftBarButtonItem = [[UIBarButtonItem alloc]

                                         initWithImage:img

                                         style:UIBarButtonItemStylePlain

                                         target:self

                                         action:@selector(onBack:)];

self.navigationController.interactivePopGestureRecognizer.delegate = (id)self;
```

December 27, 2014 update
[link](http://www.jianshu.com/p/50b63a221f09)

	  [[UIBarButtonItem appearance] setBackButtonTitlePositionAdjustment:UIOffsetMake(0, -60)
                                                         forBarMetrics:UIBarMetricsDefault];

----

in `AppDelegate.m`

		UINavigationBar * bar = [UINavigationBar appearance];
		bar.backIndicatorImage = [UIImage imageNamed:@"navBackButton"];
		bar.backIndicatorTransitionMaskImage = [UIImage imageNamed:@"navBackButton"];
	
in `BaseViewController.m` -viewdidload

		self.navigationItem.leftItemsSupplementBackButton = YES;
		self.navigationItem.backBarButtonItem = [self textBarButtonItemWithText:@""];
		
**cannot handle the back bar button item click event**