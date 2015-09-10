---
layout: post
title:  "customize tabbar icon and text color"
date:   2014-10-30	15:41:32
categories: [ios]
tags: [code snippet]

---

```
- (void)configTabBar {
    UIColor *greenColor = [UIColor colorWithRed:0.213
                                          green:0.898
                                           blue:0.573
                                          alpha:1.000];
    [self.tabBar.items
     enumerateObjectsUsingBlock:^(UITabBarItem *obj, NSUInteger idx, BOOL *stop) {
         [obj  setTitleTextAttributes:@{
                                        NSForegroundColorAttributeName: [UIColor whiteColor],
                                        }
                             forState:UIControlStateNormal];
         [obj  setTitleTextAttributes:@{
                                        NSForegroundColorAttributeName: greenColor,
                                        }
                             forState:UIControlStateSelected];
         obj.image = [[UIImage imageNamed:@"tabbar_icon".addInt(idx)] imageWithRenderingMode:UIImageRenderingModeAlwaysOriginal];
         obj.selectedImage = [UIImage imageNamed:@"tabbar_icon".addInt(idx)];
     }];

}    
```