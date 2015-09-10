---
layout: post
title:  "ios unlimited args method"
date:   2013-11-15 16:06:50
categories: ios

---
	- (void)showErrorWithTitle:(NSString *)title message:(NSString *)message
         cancelButtonTitle:(NSString *)cancelButtonTitle
         otherButtonTitles:(NSString *)otherButtonTitles, ... {
    
    	UIAlertView *alert = [[UIAlertView alloc] initWithTitle:title
                                                    message:message
                                                   delegate:nil
                                          cancelButtonTitle:cancelButtonTitle
                                          otherButtonTitles:nil];
    
        va_list args;
        va_start(args, otherButtonTitles);
        for (NSString *arg = otherButtonTitles; arg != nil; arg = va_arg(args, NSString*))
            {
             [alert addButtonWithTitle:arg];
            }
        va_end(args);
    
        [alert show];
        [alert release];}