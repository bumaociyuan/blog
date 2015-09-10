---
layout: post
title: "How to change status bar color"
description: ""
category: ios
tags: []
---

[How to change Status Bar text color in iOS 7](http://stackoverflow.com/questions/17678881/how-to-change-status-bar-text-color-in-ios-7)

1. Set the `UIViewControllerBasedStatusBarAppearance` to `YES` in the `.plist` file.
2. In the `viewDidLoad` do a `[self setNeedsStatusBarAppearanceUpdate];`
3. Add the following method:

```
-(UIStatusBarStyle)preferredStatusBarStyle{ 
   return UIStatusBarStyleLightContent; 
}
```

This will not work controllers inside `UINavigationController`

[For anyone using a UINavigationController:](http://stackoverflow.com/questions/19022210/preferredstatusbarstyle-isnt-called/19513714#19513714)

The `UINavigationController` does not forward on `preferredStatusBarStyle` calls to its child view controllers. Instead it manages its own state - as it should, it is drawing at the top of the screen where the status bar lives and so should be responsible for it. Therefor implementing preferredStatusBarStyle in your VCs within a nav controller will do nothing - they will never be called.

The trick is what the `UINavigationController` uses to decide what to return for `UIStatusBarStyleDefault` or `UIStatusBarStyleLightContent`. It bases this on it's `UINavigationBar.barStyle`. The default (`UIBarStyleDefault`) results in the dark foreground `UIStatusBarStyleDefault` status bar. And `UIBarStyleBlack` will give a `UIStatusBarStyleLightContent` status bar.

If you want `UIStatusBarStyleLightContent` on a `UINavigationController` use:

```
self.navigationController.navigationBar.barStyle = UIBarStyleBlack;
```