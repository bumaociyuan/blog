---
layout: post
title:  "turn off uisearchbar animation"
date:   2014-10-31	10:44:25
categories: [ios]
tags: [code snippet]

---

You can cancel animation by subclassing UISearchDisplayController and adding this:

```
- (void)setActive:(BOOL)visible animated:(BOOL)animated
{
    if(self.active == visible) return;
    [self.searchContentsController.navigationController setNavigationBarHidden:YES animated:NO];
    [super setActive:visible animated:animated];
    [self.searchContentsController.navigationController setNavigationBarHidden:NO animated:NO];
    if (visible) {
        [self.searchBar becomeFirstResponder];
    } else {
        [self.searchBar resignFirstResponder];
    }
}
```