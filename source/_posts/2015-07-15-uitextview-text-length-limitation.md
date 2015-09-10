---
layout: post
title: "UITextView text length limitation"
description: ""
category: ios
tags: []
---

iOS8 以上键盘的自动联想功能使UITextView的长度限制产生一些bug

* [再谈multistage text input（中文输入法）下UITextView的内容长度限制](http://blog.csdn.net/jasonblog/article/details/36894075)
* [textViewDidChange: crashes in iOS 7](http://stackoverflow.com/questions/19948394/textviewdidchange-crashes-in-ios-7/19960476#19960476)


```objc
#define textLimitLength 50
#pragma mark - UITextViewDelegate
- (BOOL)textView:(UITextView *)textView shouldChangeTextInRange:(NSRange)range replacementText:(NSString *)text {
    if (textView.text.length >= textLimitLength && text.length > range.length) {
        return NO;
    }
    return YES;
}

- (void)textViewDidChange:(UITextView *)textView {
    if (textView.markedTextRange == nil &&  textView.text.length > textLimitLength) {
        textView.text = [textView.text substringToIndex:textLimitLength];
    }
}
```