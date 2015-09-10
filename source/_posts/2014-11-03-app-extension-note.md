---
layout: post
title:  "app extension note"
date:   2014-11-03	14:24:53
categories: [ios]
tags: [app extension,tutorial]

---

[demo](https://github.com/bumaociyuan/iphoneExtension)

remove the default margin of widget

```
#pragma mark - NCWidgetProviding
- (UIEdgeInsets)widgetMarginInsetsForProposedMarginInsets:(UIEdgeInsets)defaultMarginInsets {
    return UIEdgeInsetsZero;
}
```

